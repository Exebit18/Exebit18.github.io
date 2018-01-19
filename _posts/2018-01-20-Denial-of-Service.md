---
layout : post
title : 'Denial of Service (DoS) Attacks'
category : ['Systems Security',]
---

DOS is an attack used to deny legitimate users access to a resource such as accessing a website by flooding it with incoming traffic. This results in the server failing to respond to all the requests. The effect of this can either be crashing the servers or slowing them down.

It can lead to significant loss of business or money.

## How DoS attacks work

Let’s look at how DoS attacks are performed and the techniques used. We will look at 5 common types of attacks.

__Ping of Death__

It sends data packets above the maximum limit (65,536 bytes) that TCP/IP allows. Since the sent data packages are larger than what the server can handle, the server can freeze, reboot, or crash.

__Smurf__

This type of attack funnels large amounts of ICMP ping traffic target at an Internet Broadcast Address. All the replies are sent to the victim instead of the IP used for the pings. It amplifies a single ping 255 times. Network becomes impossibly slow to use.

__Buffer overflow__

This type of attack loads the buffer with more data that it can hold. This causes the buffer to overflow and corrupt the data it holds. An example of a buffer overflow is sending emails with file names that have 256 characters.

__Teardrop__

The attacker manipulates the data packets as they are sent so that they overlap each other. This can cause the intended victim to crash as it tries to re-assemble the packets.

__SYN attack__

SYN is a short form for Synchronize. This type of attack takes advantage of the three-way handshake to establish communication using TCP. SYN attack works by flooding the victim with incomplete SYN messages. This causes the victim machine to allocate memory resources that are never used and deny access to legitimate users.

## DoS Protection: Prevent an attack

An organization can adopt the following policy to protect itself against Denial of Service attacks.

* Attacks such as SYN flooding take advantage of bugs in the operating system. __Installing security patches can__ help reduce the chances of such attacks.
* __Intrusion detection systems__ can also be used to identify and even stop illegal activities
* __Firewalls__ can be used to stop simple DoS attacks by blocking all traffic coming from an attacker by identifying his IP.
* __Routers__ can be configured via the Access Control List to limit access to the network and drop suspected illegal traffic.

## Hacking Activity: Ping of Death

We will assume you are using Windows for this exercise. We will also assume that you have at least two computers that are on the same network. __You will need to setup your own network for this exercise.__

Open the command prompt on the target computer

<br>
<div style="text-align: center;">
<img src="/images/im10.png">
</div>
<br>

(Psst.. try using LAN, really increases efficiency!)

Switch to the computer that you want to use for the attack and open the command prompt. We will ping our victim computer with infinite data packets of 65500.

Enter the following command:

`ping 10.128.131.108 –t -65500`

__HERE,__

* ```ping``` sends the data packets to the victim
* ```10.128.131.108``` is the IP address of the victim
* ```-t``` means the data packets should be sent until the program is stopped
* ```-l``` specifies the data load to be sent to the victim

You will get results similar to the ones shown below

<br>
<div style="text-align: center;">
<img src="/images/im9.png">
</div>
<br>

(if not effective, try using multiple computers to do this)

If you want to see the effects of the attack on the target computer, you can open the task manager and view the network activities.

## References
1. [Wikipedia](https://en.wikipedia.org/wiki/Denial-of-service_attack)
2. [Pluralsight](https://www.pluralsight.com/blog/it-ops/ethical-hacking-how-to-create-a-dos-attack)
