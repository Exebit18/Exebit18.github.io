---
layout : post
title : 'Anaconda Setup'
category : ['Python Workshop',]
---

This blog post would help you to setup anaconda.

**NOTE:** It is advisable to use Python 2 since most of the lectures will be based on Python 2.

# Installation for MacOs

You can install Anaconda using either the graphical installer (“wizard”) or the command line (“manual”) instructions below. If you are unsure, choose the graphical install.

## macOS command line install

1. In your browser, download the command-line version of the macOS installer for your system.

	`64-Bit Command-Line Installer (487 MB)`

2. For Python 2.7, open the Terminal.app or iTerm2 terminal application and then enter the following:

	`bash ~/Downloads/Anaconda2-5.0.1-MacOSX-x86_64.sh`

	**NOTE:** Include the `bash` command regardless of whether or not you are using the Bash shell.
	**NOTE:** Replace `~/Downloads` with your actual path and `Anaconda2-5.0.1-MacOSX-x86_64.sh` with actual name of the file you downloaded.

3. The installer prompts “In order to continue the installation process, please review the license agreement.” Click Enter to view license terms.

4. Scroll to the bottom of the license terms and enter yes to agree to them.

5. The installer prompts you to Press Enter to confirm the location, Press 'CTRL-C' to cancel the installation or specify an alternate installation directory. If you accept the default install location, the installer displays “PREFIX=/home/<user>/anaconda<2 or 3>” and continues the installation. It may take a few minutes to complete.

	**NOTE:** We recommend you accept the default install location.

6. The installer prompts “Do you wish the installer to 'prepend' the Anaconda install location to PATH in your /home/<user>/.bash_profile ?” We recommend “yes”.

	**NOTE:** If you enter “no”, specify the path to Anaconda.

	Add `export PATH="/<path to anaconda>/bin:$PATH"` in .bashrc or .bash_profile.
	Or set the PATH variable: `export PATH="/<path to anaconda>/bin:$PATH"` .Replace “<path to anaconda>” with the actual path to your Anaconda installation.

7. The installer finishes and displays “Thank you for installing Anaconda!”

8. Close and open your terminal window for the installation to take effect.



## Verifying Installation

Open Anaconda Navigator, which is automatically installed when you install Anaconda.<br>
* Click Launchpad - then select Anaconda Navigator. If it opens, you have successfully installed Anaconda.

You can also use conda in a terminal window 

To open a terminal window or Anaconda Prompt: Open Launchpad, then open 'Terminal' or 'iTerm'.

After opening the terminal window or Anaconda Prompt, choose any of the following methods:
* Enter a command such as `conda list`. If Anaconda is installed and working, this will display a list of installed packages and their versions.
* Enter the command `python`. This command runs the Python shell. If Anaconda is installed and working, the version information it displays when it starts up will include “Anaconda”. To exit the Python shell, enter the command `quit()`.
* Open Anaconda Navigator with the command `anaconda-navigator`. If Anaconda is installed properly, the graphical program Anaconda Navigator will open.


## Launching Spyder and Installing Libraries

Follow the Graphical Installer instructions

# Graphical Installing on macOS

## macOS graphical install

1. Download the graphical macOS installer for your version of Python.
	`64-Bit Graphical Installer (563 MB)	

2. Double-click the downloaded file.

3. Answer the prompts on the Introduction, Read Me and License screens.

4. On the Destination Select screen, select Install for me only.<br>
	**NOTE:** If you get the error message “You cannot install Anaconda in this location,” reselect Install for me only.

5. On the Installation Type screen, you may choose to install in another location. The standard install puts Anaconda in your home user directory (recommended)

6. Click the Install button.

7. After your install is complete, verify it by opening Anaconda Navigator, a program that is included with Anaconda: from **Launchpad**, select **Anaconda Navigator**. If Navigator opens, you have successfully installed Anaconda.

Launch **Spyder** from the **Anaconda Navigator**.

Follow Windows instructions for matplotlib and numpy.

# Installing on Linux

1. Download the Anaconda installer for Linux.

	`64-Bit (x86) Installer (508 MB)`
	`32-Bit Installer (413 MB)`

2.  Enter the following to install Anaconda for Python 2.7:
	`bash ~/Downloads/Anaconda2-5.0.1-Linux-x86_64.sh` <br>
	**NOTE:** Include the `bash` command regardless of whether or not you are using Bash shell.<br>
	**NOTE:** If you did not download to your Downloads directory, replace `~/Downloads/` with the path to the file you downloaded.<br>
	**NOTE:** Choose “Install Anaconda as a user” unless root privileges are required.

3. The installer prompts “In order to continue the installation process, please review the license agreement.” Click Enter to view license terms.

4. Scroll to the bottom of the license terms and enter “Yes” to agree.

5. The installer prompts you to click Enter to accept the default install location, CTRL-C to cancel the installation, or specify an alternate installation directory. If you accept the default install location, the installer displays “PREFIX=/home/<user>/anaconda<2 or 3>” and continues the installation. It may take a few minutes to complete.

6. The installer prompts “Do you wish the installer to prepend the Anaconda<2 or 3> install location to PATH in your /home/<user>/.bashrc ?” Enter Yes.

	**NOTE:** If you enter “No”, you must manually add the path to Anaconda or conda will not work.

7. The installer finishes and displays “Thank you for installing Anaconda<2 or 3>!”

8. Close and open your terminal window for the installation to take effect, or you can enter the command `source ~/.bashrc`.

9. After your install is complete, verify it by opening Anaconda Navigator, a program that is included with Anaconda: Open a Terminal window and type `anaconda-navigator`. If Navigator opens, you have successfully installed Anaconda.


## Launch Spyder
1. Run the following command on Terminal to install Spyder
	`conda install spyder`
2. Type `spyder` in Terminal to launch Spyder  
Installing and Testing Matplotlib and Numpy
If you’re using Anaconda Python, your system should already have numpy and matplotlib installed. Start Spyder and type “import numpy” and “import matplotlib” into the prompts.
<br><br>
![Python console]({{"/images/pyconsole.jpg"}})
<br><br>
If no errors show up, you already have them installed.


# Installing on Windows
    
1. Download the Windows Installer

	There are two versions of the installer, one for 32-bit Windows, and one for 64-bit Windows. Microsoft provides instructions here to determine if you have a 32 or 64-bit setup. If you are running 32-bit Windows, be sure that you select the 32-bit version, and if you are running 64-bit Windows, you can download either version.  

	`64-bit Graphical Installer (500 MB)`<br>
	`32-bit Graphical Installer (403 MB)`

2. Double click the .exe file.

3. Follow the instructions on the screen

	If you are unsure about any setting, accept the defaults. You can change them later.
	When installation is finished, from the **Start** menu, open the Anaconda Prompt.

4. Test the installation.

## Test Installation
To test your installation, in your Terminal window or Anaconda Prompt, run the command `conda list`.
For a successful installation, a list of installed packages appear.

## Launching Spyder
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


## Installing and Testing Matplotlib and Numpy
If you’re using Anaconda Python, your system should already have numpy and matplotlib installed. Start Spyder and type “import numpy” and “import matplotlib” into the prompts.
<br><br>
![Python console]({{"/images/pytcon.jpg"}})
<br><br>
If no errors show up, you already have them installed.

## Users already having anaconda

For those who to run python 2.7 on anaconda of python 3 here's a link which can help you out.
<br>
[Managing python](https://conda.io/docs/user-guide/tasks/manage-python.html#using-a-different-version-of-python)





