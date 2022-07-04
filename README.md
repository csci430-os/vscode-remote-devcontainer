# Introduction 

## This project is currently under heavy development - Proceed with caution

Assignments and simulations for [Texas A&M University-Commerce](https://tamuc.edu) _CSCI 430 - Introduction to Operating Systems_ [codebase](https://bitbucket.org/dharter/csci430-os-sims/src/master/) created by [Dr. Derek Harter](https://derekharter.github.io/) is modified to run in an Ubuntu 20.04 VS Code Development Container on the local machine.

# System requirements

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
[Video showing Setting Up your Dev Container](https://youtube.com) 
in which we show an example of
performing the following steps.  This video shows setting up and
installing docker and VS Code on a Windows 10 system, but the steps
are mostly the same whether you are using Windows, MAC OS or Linux.

## Setup VS Code with Remote Containers as described below.
<br />

#### STEP 1: Install and configure Docker for your operating system.


- **Windows/Mac:** Install Docker Desktop from [here](https://www.docker.com/get-started/).

  1. Recent versions of Docker Desktop for Windows seem to default to recommending and using WSL (windows
     subsystem for linux) as the docker virtualization backend.  If you need configure by hand
	 by hand, to ensure the [WSL 2 back-end](https://docs.docker.com/desktop/windows/wsl/) is enabled: 
    
    - Right-click on the `Docker taskbar item` and select `Settings`. 
    
    - Check `Use the WSL 2 based engine` and verify your distribution is enabled under `Resources > WSL Integration`.

- **Linux:** Follow the official install instructions for [Docker CE](https://hub.docker.com/search?offering=community&operating_system=linux&platform=&q=&type=edition) for your distribution. 

  1. Add your user to the docker group by using a terminal to run: `sudo usermod -aG docker $USER`

  2. `Sign out and back in` again so your changes take effect.
<br />
<br />

#### STEP 2: Install and Setup git from [here](https://git-scm.com/download/)

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
<br />
<br />

#### STEP 3: Install VS Code Editor from [here](https://code.visualstudio.com/)
<br />

#### STEP 4: Install Remote Containers extension from [here](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

  1. Alternatively, simply search for Remote Containers in your extensions.  It will probably be a recommended
     extension for you after installing the Docker Decktop.
	 
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

- If you downloaded the repository as a `zip` folder, extract it to the desired location and open the folder in the VS Code
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
1. https://code.visualstudio.com/docs/remote/containers
2. https://code.visualstudio.com/docs/remote/create-dev-container
3. https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-containers

