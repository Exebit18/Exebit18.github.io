---
Layout : post
Title : About Rowhammer
Category : Cyber Security
---

# Rowhammer

Rowhammer is an unintended side effect in dynamic random-access memory (DRAM) that causes memory cells to leak their charges and interact electrically between themselves. This could possibly alter the contents of nearby memory rows that were not addressed in the original memory access. The main cause of this attack happens to be the high cell density in modern DRAM, and the attack can be triggered by specially crafted memory access patterns that rapidly activate the same memory rows numerous times. It enables an attacker to cause bit flips in DRAM by issuing only read requests to a modern DRAM. 

This blog post will start with the basics of how the DRAM is organized, and explain how the rowhammer bug works.

## DRAM Background

A system can have one or more channels, which are physical links between the DRAM modules and the memory controller. Multiple Dual Inline Memory Modules (DIMMs), which are the physical memory modules attached to the mainboard, can be connected to each channel. A DIMM typically has one or two ranks, which often correspond to the front and back of the physical module. Each rank is composed of banks, typically 8 on DDR3 DRAM and 16 on
DDR4 DRAM. Banks finally contain the actual memory arrays which are organized in rows (typically 214 to 217) and columns (often 210). In this way, the DRAM cells are present as rows. Depending on whether the cell is charged or not, the cell stores the corresponding binary value (1 if charged and 0 otherwise).

Apart from the memory hierarchy described above, each bank in a DRAM has a corresponding row buffer. This row buffer is used to serve memory accesses. If the address requested is already in the row buffer, it is served directly from the row buffer. Otherwise, the row buffer contents are written back to the corresponding row and the required row is written to the row buffer and the memory access is then served.

Internally, the row buffer working is as follows:
* The voltage of the required row is raised and its contents are transferred to the row buffer.
* The contents of the row buffer are used to serve the memory access request.
* When a memory request for another row has to be served, the row buffer is cleared by reducing the voltage of the previous row and the process is repeated.

However, the charge in the rows are not persistent. Hence, the rows need to be constantly refreshed. Every DRAM comes with a minimum time for which charge can be held in the DRAM cell. The minimum time is typically specified by the DRAM manufacturer. Based on this minimum time, the memory controller chooses to refresh the cells.

![DRAM concept](https://github.com/Exebit18/Exebit18.github.io/blob/master/images/rowhammerimg1.jpg)

When a row’s voltage is toggled repeatedly, some cells in nearby rows leak charge at a much faster rate. These cells may not hold charge for the minimum time specified by the DRAM manufacturer. By repeatedly accessing addresses in the same bank but different rows, we can cause a row’s voltage to toggle repeatedly. This would cause the cell to lose charge before it can be refreshed. This is the basis for the rowhammer attack. Increasing the cell density in DRAMs increases the discharge rate and hence makes the DRAM more vulnerable to the rowhammer attack.

## The Attack

To get the attack working, we should access two addresses in the same bank but different rows alternately. With such an access pattern, the row buffer would be frequently charged and discharged. This would cause charges to be lost at a much faster rate, hence leading to change in the contents of the memory.

However, doing that by itself is not simple. Since every modern system has a cache memory to store the contents of the recently used addresses, the task is further complicated. This is because the first access to the addresses will be served from the DRAM, whereas subsequent accesses will be served from the cache. If this happened, the DRAM would be accessed only the first time and hence the attack would not be induced.

To overcome the problem due to cache memory, we use the x86 CLFLUSH instruction. This instruction evicts the virtual address provided as argument from all levels of the cache. This instruction is invoked after every access, to ensure that the next access also happens from the DRAM. To perform the attack, we choose two addresses belonging to the same bank and access them alternately from the DRAM for a large number of iterations.

Choosing two addresses belonging to the same bank can be a complicated process. Since the number of banks is small(about 8 to 16), we can choose any two addresses at random. If there are 8 banks, 2 addresses would belong to the same bank with probability ⅛. The probability of the addresses belonging to the same row is very small since the number of rows in a bank are very large. Hence, we can safely assume that if two addresses belong to the same bank, they will belong to different rows in the same bank.

## Results

The below screenshots demonstrate the rowhammer attack. The accessible address space is initialized with all bits as 1. So, originally, every location would have 0xffffffffffffffff, when 64 bits are counted from that address. The addresses are accessed as mentioned above and then it is checked if any of the bits have toggled to a 0.  In the below case, the content of the address changes to 0xbfffffffffffffff.

![output](https://github.com/Exebit18/Exebit18.github.io/blob/master/images/rowhammerimg2.jpg)

## References:
1. [Rowhammer on Wikipedia](https://en.wikipedia.org/wiki/Row_hammer)
2. Code for the rowhammer bug on [Github](https://en.wikipedia.org/wiki/Row_hammer)


