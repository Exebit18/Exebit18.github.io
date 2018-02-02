---
layout : post
title : 'Python Workshop: Anaconda Setup'
category : ['Python Workshop',]
---

This blog post would help you to setup anaconda. Anaconda is an open source distribution of python and R programming languages that aims to simplify package management and deployment.

**NOTE:** It is advisable to use Python 2 since most of the lectures will be based on Python 2.

## 1. Users already having anaconda

For those who want to run python 2.7 on anaconda of python 3, here's a [guide](https://conda.io/docs/user-guide/tasks/manage-python.html#using-a-different-version-of-python) which can help you out. 

## 2. Setup on Linux

Follow the guide [here](https://conda.io/docs/user-guide/install/linux.html). 

## 3. Setup on MacOs

Follow the guide [here](https://conda.io/docs/user-guide/install/macos.html).

## 4. Setup on Windows
  
1. **Anaconda Installation:**    
    1. Download the Windows Installer.

	   There are two versions of the installer, one for 32-bit Windows, and one for 64-bit Windows. Microsoft provides instructions [here](https://support.microsoft.com/en-us/help/15056/windows-7-32-64-bit-faq) to determine if you have a 32 or 64-bit setup. If you are running 32-bit Windows, be sure that you select the 32-bit version, and if you are running 64-bit Windows, you can download either version.  

        [64-bit Graphical Installer (500 MB)](https://repo.continuum.io/archive/Anaconda2-5.0.1-Windows-x86_64.exe)<br>
        [32-bit Graphical Installer (403 MB)](https://repo.continuum.io/archive/Anaconda2-5.0.1-Windows-x86.exe)

    2. Double click the `.exe` file.

    3. Follow the instructions on the screen

        If you are unsure about any setting, accept the defaults. You can change them later.
        When installation is finished, from the **Start** menu, open the Anaconda Prompt.

2. **Test the Installation:**

    To test your installation, in your Terminal window or Anaconda Prompt, run the command `conda list`.

    For a successful installation, a list of installed packages appear.

3. **Launching Spyder:**:

    When you download and install the Anaconda distribution of Python, you are getting several tools related to Python development. One of the tools is Spyder (Scientific Python Development Environment), an integrated development environment useful for writing, running, and debugging code.

    Launch `Spyder` from `Start` Menu
    <br><br>
    ![start menu]({{"/images/start.jpg"}})
    <br><br>

    Opening the Spyder application should present you with the following window. This window contains two commonly used parts, among others:
    * Code Editor that lets you create and edit existing Python source files 
    * IPython interpreter pane, which gives you access to the Python interactive mode 
    <br><br>
    ![spyder]({{"/images/spyder.jpg"}})
    <br><br>

4. **Installing and Testing Matplotlib and Numpy:**
    If you’re using Anaconda Python, your system should already have numpy and matplotlib installed. Start Spyder and type `import numpy` and `import matplotlib` into the prompts.
    <br><br>
    ![Python console]({{"/images/pytcon.jpg"}})
    <br><br>
    If no errors show up, you already have them installed.


<br>
**For any doubts, queries or issues use the comments section below.**

