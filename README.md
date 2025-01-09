# Introduction 

Development Environment configuration instructions for 
[Texas A&M University-Commerce](https://www.tamuc.edu/dept-of-computer-science-and-information-systems/)
Computer Science and Information System classes.  The development
environment you set up here may be used for many class assignment,
such as data structures, operating systems, computer architecture,
etc. for both undergraduate and graduate computer science classes.

This repository mainly consists of instructions for setting up a
Visual Studio Code (VSCode) development environment that uses Docker
Development Containers (DevContainers) and can be used to submit
assignment in GitHub classrooms.  You will need a relatively recent
computing system, either laptop or desktop.  It is recommended you use
a system with at least 4GB of memory and not too old of a processor,
if possible.  You should be able to set up a VSCode DevContainer
environment on Intel/AMD X86_64 hardware or Mac M1/M2 Arm
architectures.  You should be able to set up the needed development
environment on a Windows, Mac or Linux operating system based machine.
Chromebooks or Android OS are not supported for this
configuration.

This development environment provides a set of standard development
tools, such as C/C++ compiler, build system tools and configuration,
code formatters and style checkers, code documentation generation,
etc.  Assignments you are given will assume you are using the exact
development environment and version of these tools, so that we will
minimize any problems from using different versions of build tools or
build environments.  The Docker Development Container actually runs an
Ubuntu 24.04 virtual environment in the container, to which the
needed version of the development tools are installed for our class
assignments.

# System requirements

It is recommended you have 4GB or more of main memory, and not too old of a
system/processor to set up your development environment on.

- **MacOS:** 
  - Docker Desktop 2.0+.

- **Windows:** 
  - Docker Desktop 2.0+ on Windows 10 Pro/Enterprise. 
  - Windows 10 Home (2004+) requires Docker Desktop 2.3+ and the WSL 2 back-end.

- **Linux:** 
  - Docker CE 18.06+.
  - The Ubuntu snap package is not supported.

# Instructions

You can watch this video [Video showing Setting Up your DevContainer](https://youtu.be/ttCrQjaNR4Y) 
in which we show an example of performing the steps described below.
This video shows setting up and installing docker and VSCode on a
Windows 10 system, but the steps are mostly the same whether you are
using Windows, MAC OS or Linux.

## STEP 1: Install and configure Docker for your operating system.


- **Windows/Mac:** Get the most recent Docker Desktop installer from [here](https://www.docker.com/get-started/).

  1. Recent versions of Docker Desktop for Windows seem to default to
     recommending and using WSL (Windows subsystem for Linux) as the
     docker virtualization back-end.  If you need to configure WSL by
     hand see the following: [WSL 2 back-end](https://docs.docker.com/desktop/windows/wsl/):
    
    - Right-click on the `Docker taskbar item` and select `Settings`. 
    
    - Check `Use the WSL 2 based engine` and verify your distribution is enabled under `Resources > WSL Integration`.

    **NOTE**: In some cases on Windows, you will get a message that "WSL 2 installation is incomplete" and your 
	Docker will not be able to start yet.  Click on the link given in that error message, and follow the 6 steps
	to get WSL 2 installed.  Then you should be able to (re)start Docker Desktop successfully with it using
	WSL 2.
	
	**NOTE**: You may need to enable hardware virtualizaiton if you own an Intel / AMD PC.
	
    When booting up, enter your system BIOS

    - [How to Enter the BIOS on Any PC: Access Keys by Manufacturer](https://www.tomshardware.com/reviews/bios-keys-to-access-your-firmware,5732.html)

	Usually the `F2` key should work, but if not there should usually be
	a message on your first boot screen telling you what the BIOS access
	key is.

	In your BIOS, find the setting for hardware Virtualization

    - [Enabling Intel VT or AMD-V virtualization hardware extensions in BIOS](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/5/html/virtualization/sect-virtualization-troubleshooting-enabling_intel_vt_and_amd_v_virtualization_hardware_extensions_in_bios#sect-Virtualization-Troubleshooting-Enabling_Intel_VT_and_AMD_V_virtualization_hardware_extensions_in_BIOS) 


## STEP 2: Create GitHub account and install and configure git

  - **Create GitHub Account**
  
  If you don't have one already, create/sign up for a free [GitHub account](https://github.com/)
  
  Make sure that you use your student@leomail.tamuc.edu as the primary e-mail address, if at all possible.
  
  - **Install Git and SSH tools**
  
  1. If you are using Mac or Linux, you probably already have a git client installed, so you do not need to
     install it from the git-scm link above.  You can check if you have git already installed by opening
	 a command line terminal and trying
	 
	 ```
	 $ git --version
	 ```
	 If you do not have git on your Mac/Linux system, it will probably be easier to use your package
	 manager or brew to install git on your system.

  2. For Windows machines, download and install the standard [Git Installer](https://git-scm.com/downloads).
  
     - You should accept all of the default options, except when asked for "Configuring the line ending conversions".
	   Windows uses different line ending conventions, but our work will be done in a linux/unix
	   environment.  So make sure you select the option to not convert cr/lf endings
	   "Checkout as-is, commit as-is".
  
  3. For all operating systems, you need to perform the following git configuration steps.  
     [Initial Git Configuration](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup) 
	 and [How to Set up SSH and Generate an SSH Key on Windows 11](https://davidaugustat.com/windows/windows-11-setup-ssh)
	 Open up a command line terminal and perform the configuration and generate an ssh key like this:
	 ```
	 $ git config --global user.name "John Doe"
	 $ git config --global user.email johndoe@example.com
	 $ ssh-keygen
	 Generating public/private rsa key pair.
	 Enter file in which to save the key (C:\Users\Quickemu/.ssh/id_rsa):
	 Created directory 'C:\\Users\\Quickemu/.ssh'.
	 Enter passphrase (empty for no passphrase):
	 Enter same passphrase again:
	 Your identification has been saved in C:\Users\Quickemu/.ssh/id_rsa
	 Your public key has been saved in C:\Users\Quickemu/.ssh/id_rsa.pub
	 The key fingerprint is:
	 SHA256:nywXiR8TIePPUsVVt5wNu5PdmYYgQXkLMXkhD09Shy0 quickemu@classdemo
	 The key's randomart image is:
	 +---[RSA 3072]----+
	 |        +O*==oo.o|
	 |       . *XEo..o=|
	 |        ..*+o .+.|
	 |         =.+. .++|
	 |        S B  .++o|
	 |         = =  .. |
	 |        . *      |
	 |         o       |
	 |                 |
	 +----[SHA256]-----+
	 
	 ```
     Make sure that you use your real name here and in your GitHub account
	 for class assignments.  Also ensure that the e-mail address you
	 specify in the git config is the same as the primary e-mail
	 address you use in creating your GitHub account.
	 
  4. Copy the generated ssh key to your GitHub account.  The second link in previous step shows this.  There will be a file
     named something like `c:\Users\username\.ssh\id_rsa.pub` in your home directory, though the location of your home directory
	 will differ depending on your operating system.  This file is in a hidden directory (starts with a .), so you may not
	 be able to see it in a file browser on your system unless you enable viewing hidden files/directories.  Find the public
	 key, and copy it.  Then create a new ssh key in GitHub and paste in this public key.
	 
  5. **IMPORTANT** If you have never connected to Github before using ssh, you should ensure that Github is an known host and that your ssh
     key access that you just configured is working.  Do the following to test this:
     ```
	 $ ssh git@github.com
     The authenticity of host 'github.com (140.82.112.4)' can't be established.
     ECDSA key fingerprint is SHA256:p2QAMXNIC1TJYWeIOttrVc98/R1BUFWu3/LiyKgUfQM.
     Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
     Warning: Permanently added 'github.com,140.82.112.4' (ECDSA) to the list of known hosts.
     PTY allocation request failed on channel 0
     Hi tamucstudent! You've successfully authenticated, but GitHub does not provide shell access.
     Connection to github.com closed.
	 
	 ```
	 And say 'yes' if prompted to add Github as a known host as shown here.  If it says you have successfully
	 authenticated, then you probably have configured your ssh key correctly for Github use.  If this step does
	 not successfully connect, do no proceed until you get help or correctly set up your ssh key to be able to
	 access your GitHub account.
	 

## STEP 3: Install VSCode Editor 

Download and install the VSCode Editor on your system from [here](https://code.visualstudio.com/)

There should be standard installers for Windows, Mac and Linux available here, as well as
instructions on how to run the installers if needed.

## STEP 4: Install Microsoft Remote Development Containers 

Once you have VSCode installed, start it up.  You need to install the Micsosoft Remote Dev Containers
extension.  The easiest way to do this is to open up the `Extensions` section in VSCode and search
for "Dev Containers".  When you find the official extension provided by Microsoft, install it in you
VSCode IDE.

The Remote Containers extension page is [here](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)


# References

- Using remote DevContainers in VSCode:  https://code.visualstudio.com/docs/remote/containers
- Creating DevContainers in VSCode:  https://code.visualstudio.com/docs/remote/create-dev-container
- Windows Subsystem for Linux as Docker container back end on Windows 10: https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-containers
- Initial git configuration: https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup
- Creating SSH key for remote GitHub repositories: https://davidaugustat.com/windows/windows-11-setup-ssh


