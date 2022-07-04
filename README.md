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

## Setup VS Code with Remote Containers as described below.
<br />

#### STEP 1: Install and configure Docker for your operating system.


- **Windows/Mac:** Install Docker Desktop from [here](https://www.docker.com/products/docker-desktop).

  1. If you are using WSL 2 on Windows, to ensure the [WSL 2 back-end](https://docs.docker.com/desktop/windows/wsl/) is enabled: 
    
    - Right-click on the `Docker taskbar item` and select `Settings`. 
    
    - Check `Use the WSL 2 based engine` and verify your distribution is enabled under `Resources > WSL Integration`.

- **Linux:** Follow the official install instructions for [Docker CE](https://hub.docker.com/search?offering=community&operating_system=linux&platform=&q=&type=edition) for your distribution. 

  1. Add your user to the docker group by using a terminal to run: `sudo usermod -aG docker $USER`

  2. `Sign out and back in` again so your changes take effect.
<br />
<br />

#### STEP 2: Install VS Code Editor from [here](https://code.visualstudio.com/)
<br />

#### STEP 3: Install Remote Containers extension from [here](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
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

