# Introduction 

Development Environment configuration instructions for 
[Texas A&M University-Commerce](https://www.tamuc.edu/dept-of-computer-science-and-information-systems/)
Computer Science and Information System classes.  The development
environment you set up here may be used for many class assignment,
such as data structures, operating systems, computer architecture,
etc.  for both undergraduate and graduate computer science classes.

This repository mainly consists of instructions for setting up a
Visual Studio Code (VSCode) development environment that uses Docker
Development Containers (DevContainers) and can be used to submit
assignment in GitHub classrooms.  You will need a relatively recent
computing system, either laptop or desktop.  It is recommended you use
a system with at least 4GB of memory and not too old of a processor if
possible.  You should be able to set up a VSCode DevContainer
environment on Intel/AMD X86_64 hardware or Mac M1/M2 Arm
architectures, though we have not yet tested as extensively these
instructions on the M1/M2 Arm architectures, so feedback would be
appreciated if you set up a VSCode DevContainer on that architecture.
You should be able to set up the needed development environment on a
Windows, Mac or Linux operating system based machine.  Chromebooks or
Android OS are probably not supported for this configuration.

This development environment provides a set of standard development
tools, such as C/C++ compiler, build system tools and configuration,
code formatters and style checkers, code documentation generation,
etc.  Assignments you are given will assume you are using the exact
development environment and version of these tools, so that we will
minimize any problems from using different versions of build tools or
build environments.  The Docker Development Container actually runs an
Ubuntu 22.04 virtual environment in the container, to which the
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

You can watch the following 
[Video showing Setting Up your DevContainer](https://youtu.be/ttCrQjaNR4Y) 
in which we show an example of
performing the following steps.  This video shows setting up and
installing docker and VSCode on a Windows 10 system, but the steps
are mostly the same whether you are using Windows, MAC OS or Linux.

## Setup VSCode with Remote Containers as described below.
<br />

#### STEP 1: Install and configure Docker for your operating system.


- **Windows/Mac:** Install Docker Desktop from [here](https://www.docker.com/get-started/).

  1. Recent versions of Docker Desktop for Windows seem to default to
     recommending and using WSL (Windows subsystem for Linux) as the
     docker virtualization back-end.  If you need to configure WSL by
     hand [WSL 2 back-end](https://docs.docker.com/desktop/windows/wsl/):
    
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

	- [Enabling Virtualization in your PC BIOS](https://bce.berkeley.edu/enabling-virtualization-in-your-pc-bios.html)



- **Linux:** Follow the official install instructions for 
  [Docker CE](https://hub.docker.com/search?offering=community&operating_system=linux&platform=&q=&type=edition) 
  for your distribution. 

  1. Add your user to the docker group by using a terminal to run: `sudo usermod -aG docker $USER`

  2. `Sign out and back in` again so your changes take effect.
<br />
<br />

#### STEP 2: Create GitHub account and install and configure git from [here](https://git-scm.com/download/)

  1. If you don't have one already, create/sign up for a free [GitHub account](https://github.com/)
  
  2. If you are using Mac or Linux, you probably already have a git client installed, so you do not need to
     install it from the git-scm link above.  You can check if you have git already installed by opening
	 a command line terminal and trying
	 
	 ```
	 $ git --version
	 ```
	 If you do not have git on your Mac/Linux system, it will probably be easier to use your package
	 manager or brew to install git on your system.
	 
  3. For all operating systems, you need to perform the following git configuration steps.  
     [Initial Git Configuration](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup) 
	 and [Creating SSH key for remote GitHub repositories](https://medium.com/devops-with-valentine/2021-how-to-set-up-your-ssh-key-for-github-on-windows-10-afe6e729a3c0)
	 Open up a command line terminal and perform the configuration and generate an ssh key like this:
	 ```
	 $ git config --global user.name "John Doe"
	 $ git config --global user.email johndoe@example.com
	 $ ssh-keygen
	 ```
	 Make sure that you use your real name here and in your GitHub account for class assignments.  Also ensure that the e-mail address you specify
	 in the git config is the same as the primary e-mail address you use in creating your GitHub account.
	 
  4. Copy the generated ssh key to your GitHub account.  The second link in previous step shows this.  There will be a file
     named something like `c:\Users\username\.ssh\id_rsa.pub` in your home directory, though the location of your home directory
	 will differ depending on your operating system.  This file is in a hidden directory (starts with a .), so you may not
	 be able to see it in a file browser on your system unless you enable viewing hidden files/directories.  Find the public
	 key, and copy it.  Then create a new ssh key in GitHub and paste in this public key.
	 
  5. If you have never connected to Github before using ssh, you should ensure that Github is an known host and that your ssh
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
	 authenticated, then you probably have configured your ssh key correctly for Github use.
	 
<br />
<br />

#### STEP 3: Install VSCode Editor from [here](https://code.visualstudio.com/)

There should be standard installers for Windows, Mac and Linux available here, as well as
instructions on how to run the installers if needed.
<br />

#### STEP 4: Install Remote Development Containers extension from [here](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

Alternatively, simply search for Remote Containers in your extensions.  It will probably be a recommended
extension for you after installing the Docker Desktop.	 
<br />
<br />

## Setup and start your development environment

### Watch this [GIF](https://microsoft.github.io/vscode-remote-release/images/remote-containers-readme.gif) to have an idea what the result will look like.
<br />

- Clone (or download) this repository on to your local machine 
<br />
<br />

<p align="center">
  <img src="https://github.com/TAMUC-RELLIS/vscode-remote-csci-430/blob/main/images/download-repo.png" width=70% height=70%>
</p>
<br />
<br />

- If you downloaded the repository as a `zip` folder, extract it to the desired location and open the folder in the VSCode
<br />
<br />

<p align="center">
  <img src="https://i.stack.imgur.com/o7dTO.gif" padding-left=50px  width=70% height=70%>
</p>
<br />
<br />

- You will be prompted to _Reopen in Container_ at the bottom right corner of your editor. 
<br />
<br />

<p align="center">
  <img src="https://code.visualstudio.com/assets/docs/remote/containers/dev-container-reopen-prompt.png" width=70% height=70%>
</p>
<br />
<br />

- If not, you can manually invoke this 
  
  1. Press `Ctrl + Shift + P`.
  
  2. Start typing `Remote Containers`. 
  
  3. You can select `Remote Containers: Reopen in Container` as shown below.
  <br />
  
  <p align="center">
    <img src="https://code.visualstudio.com/assets/docs/remote/containers/remote-containers-reopen.png" width=70% height=70%>
  </p>

<br />

# References
- Using remote DevContainers in VSCode:  https://code.visualstudio.com/docs/remote/containers
- Creating DevContainers in VSCode:  https://code.visualstudio.com/docs/remote/create-dev-container
- Windows Subsystem for Linux as Docker container back end on Windows 10: https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-containers
- Initial git configuration: https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup
- Creating SSH key for remote GitHub repositories: https://medium.com/devops-with-valentine/2021-how-to-set-up-your-ssh-key-for-github-on-windows-10-afe6e729a3c0


