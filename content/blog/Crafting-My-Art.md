+++
title = "Crafting My Art 🖼️"
author = "Joshua Ross"
date = 2024-04-19T11:42:00-04:00
description = "A Guide To My Dev Environment."
tags = [
    "coding",
    "scripting",
    "windows",
    "Linux",
    "hardware"
]
showToc = true
+++

# Introduction 

**Welcome Everyone**, Today I decided to write another blog post after having a conversation with a friend. I asked him what should the topic be today and whether it should be a blog or more of a tutorial. He suggested a tutorial so I decided why not write on how I set up my Dev Environment. So read along while I explain how I set this up and why I chose said apps.

# Software
## [Homebrew](https://brew.sh/)

The First Item on the list is good ole Homebrew. I started using this [Package Manager](https://en.wikipedia.org/wiki/Package_manager) around 2019 when working at a former job of mine. At the time I was using a MacBook Pro as my work computer and wanted to find a way to install apps without needing to find the site after some searching was able to find homebrew and was loving and the access to other apps. In this next step, I'm going to show you how you can install it.

### How To Install
**This Package Manager only works on MacOS and Linux.**

{{< collapse summary="Instructions" openByDefault=false >}}
The first step is to head over to the [Homebrew](https://brew.sh/) website.

* When you arrive there you should see this command.
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
 **NOTE:** You will need to make sure Git is installed.

* After this is all done it will spit out the next steps to do after. It is best to follow the steps. I will show you how to add homebrew to your Linux or MacOS Shell. 
* For MacOS this is done for you by the script itself.
* For Linux, you can run this command.
```bash
echo 'eval "$(</home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> ~/.bashrc
```

* After that is all done you can install whatever program that is in their repo.

E.g. Being

```bash
brew install wget
```
This will install wget. Some apps may need to be added to your profile so the system knows the **PATH**.
{{</collapse>}}


Well, this is all for **Homebrew**.

## [WinGet]((https://github.com/microsoft/winget-cli))

winget, like homebrew winget is a Package Manager but for Windows. When doing dev work on my Windows desktop I base a lot of my script to install stuff around this package manager. Mainly being a neovim install script located in my [dotfiles](https://github.com/ross-jm/dotfiles) repo. But enough about that let's see how you install it.

### How To Install


{{< collapse summary="Instructions" openByDefault=false >}}
- Check to see if it's installed by doing a 

```powershell
winget
```

if it returns nothing then it is not installed and you can follow the next steps. If it it does you can try installing something by doing something like

```powershell
winget install JanDeDobbeleer.OhMyPosh -s winget
```

There is a chance that it may be installed. But is not installed correctly. In that case follow these steps.

Search for the store as shown below.
![open-microsoft-store](/static/images/blog/open-microsoft-store.png)

After that type in winget as shown below
![search-for-winget-in-microsoft-store](/static/images/blog/search-for-winget-in-microsoft-store.png)

From there just install or wait for it to update as sometimes on new installs it does need to update itself.
After all is said and done you can start installing stuff or even try and write a script with it. Try looking at [winstall](https://winstall.app) for apps that you can download.
{{</collapse>}}


## [VSCode](https://code.visualstudio.com/)

I use VSCode on the daily. I'm even using it to write this blog post. I mainly use this as the main code writing as it's really easy to install extensions and has a vast majority of them as well. It also integrates with GitHub natively so when I feel like being lazy and not doing git commands from the terminal I can just click some buttons and then **poof** the code is on GitHub. You're probably wondering well how do you install it? Well, let me show you.

### How To Install

{{< collapse summary="Instructions" openByDefault=false >}}
* **Method 1: Installer Package.** `Universal`
    * Head to the website you can get there easily by clicking on the header for VSCode. Find the OS you're using and then install it that way.

* **Method 2: winget** `Windows Only`

```powershell
winget install Microsoft.VisualStudioCode
```

* **Method 3: Homebrew**  `MacOS only as it is a cask install.`

```
brew install --cask visual-studio-code
```
{{</collapse>}}


After you've installed VSCode you can set up the environment how you would like. With theme, icons, and extensions. The ones I highly recommend are listed below.

#### Visual Studio Code Extensions

* [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments)
* [CodeSnap](https://marketplace.visualstudio.com/items?itemName=adpyke.codesnap)
* [Grammarly](https://marketplace.visualstudio.com/items?itemName=znck.grammarly)
* [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
* [Material Theme](https://marketplace.visualstudio.com/items?itemName=Equinusocio.vsc-material-theme)
* [Material Theme Icons](https://marketplace.visualstudio.com/items?itemName=Equinusocio.vsc-material-theme-icons)
* [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

These are the ones I make sure are always installed or synced when I setup a new machine.

## [LazyVim](https://www.lazyvim.org/)

LazyVim is a distro of [NeoVim](http://neovim.io/) a highly extensible and customizable text editor based on the popular Vim editor. It's designed to improve upon Vim's limitations while retaining its powerful editing capabilities and modal interface. I chose LazyVim as I use Vim all the time in Linux and Windows and wanted something a little more flexible when I didn't feel like opening VSCode. LazyVim has videos all over YouTube and one day I decided to watch some and decided to try it out after talking to a Co-Worker of mine. I do not regret it one bit as LazyVim has helped me code better at times and understand how things work. It also keeps me away from the mouse. I even have my [LazyVim Config](https://github.com/ross-jm/lazyvim-config) on GitHub if you want to use it. Enough of the talk though Let's show how you can install it.

### How To Install

- **Method 1: Windows**


{{< collapse summary="Instructions" openByDefault=false >}}


- **Install NeoVim**

```pwsh
winget install Neovim.Neovim
```

- **Make a backup of your current Neovim files:**
```powershell
# required
Move-Item $env:LOCALAPPDATA\nvim $env:LOCALAPPDATA\nvim.bak

# optional but recommended
Move-Item $env:LOCALAPPDATA\nvim-data $env:LOCALAPPDATA\nvim-data.bak
```

* **Clone the starter:**
```powershell
git clone https://github.com/LazyVim/starter $env:LOCALAPPDATA\nvim
```

- **Remove the `.git` folder, so you can add it to your own repo later**
```powershell
Remove-Item $env:LOCALAPPDATA\nvim\.git -Recurse -Force
```

- **Start Neovim!**
```pwsh
nvim
```
{{</collapse>}}




- **Method 2: Linux/MacOS**
{{< collapse summary="Instructions" openByDefault=false >}}

- **Make a backup of your current Neovim files:**
```
# required
mv ~/.config/nvim{,.bak}

# optional but recommended
mv ~/.local/share/nvim{,.bak}
mv ~/.local/state/nvim{,.bak}
mv ~/.cache/nvim{,.bak}
```

- **Clone the starter**
```
git clone https://github.com/LazyVim/starter ~/.config/nvim
```

- **Remove the `.git` folder, so you can add it to your own repo later**
```
rm -rf ~/.config/nvim/.git
```

- **Start Neovim!**
```
nvim
```
{{</collapse>}}

That is how you can install **LazyVim** from their template if you want to do it with my template on the `git clone` step all you would need to do is change the repo. I can show you below for the 3 OSs.

{{< collapse summary="Instructions" openByDefault=false >}}
-  **Windows**
```
git clone https://github.com/ross-jm/lazyvim-config.git $env:LOCALAPPDATA\nvim 
```

- **Linux/MacOS**
```
git clone https://github.com/ross-jm/lazyvim-config.git ~/.config/nvim
```
{{</collapse>}}


Then remove the `.git` folder so you can customize it to your liking and push it to your own GitHub account.

## [Git](https://git-scm.com/)

Git is a distributed version control system primarily used for tracking changes in source code during software development. It allows multiple developers to collaborate on a project by managing different versions of files and coordinating their work efficiently.

With that being said I use git on the daily both at work and at Home. Heck, I'm even going to use it after this post to push the changes to the main branch so you can see this post. I've used **Git** for years on a nondev basis but as of a few years back, I got more into making stuff and posting it on **GitHub** so people could see what I do and even use it. It's always a nice thing when someone sees some code of yours and is like wow this is nice. But let's get into the fun part of how to install it. Which could not be easier.

### How To Install
{{< collapse summary="Instructions" openByDefault=false >}}
- **Method 1: Installer File** `Semi-Universal`
    - Go to the Git website by clicking on the **Git** header. After you get to the site you can click the Monitor to get to the downloads.
    - On Windows, it will download an `.exe` file, and on Linux, it will give you instructions on how to install it via the OS's native package manager.

- **Method 2: Homebrew** `Linux/MacOS`
```
brew install git
```

- **Method 3: WinGet** `Windows`
```
winget install Git.Git
```
{{</collapse>}}

### Configure `.gitconfig` file
After that is done you need to do one important step. As the header says we need to configure the `.gitconfig` file. That can be done with the command below and replacing it with your info. Preferably with the email you used with your Git Maintainer.

```
git config --global user.name "Your Name" # name you want on the commits
git config --global user.email "your.email@example.com" # email used on the account or you're doing local git repos whatever email you want attached.
git config --global core.editor "your-preferred-editor" # preferred editor that git uses.
```

Change the info and paste those commands into your terminal and after you run them in your home directory you will see a file called `.gitconfig`. You can also do a 
```
git config --list
```
To check your config.

Well folks that's all for Git and the software portion now to talk about the Computers I use briefly.

# Hardware

In this brief section. I'll tell you about the devices  I use to do all of my scripting and coding. Along with all the markdown I write.

## [Yoga 7i 2-in-1 14" Laptop](https://www.bestbuy.com/site/lenovo-geek-squad-certified-refurbished-yoga-7i-2-in-1-14-laptop-intel-evo-platform-core-i5-12gb-memory-512gb-ssd-dark-moss/6470921.p?skuId=6470921)

As shown in the link this is a nice laptop that I've been using for about 2 years now. Mine has an Intel Core i7 11th gen instead of the i5 in the link. This Laptop came with Windows 11 Home but I quickly installed [Pop!_OS](https://pop.system76.com/) on this laptop when I'm on the go I prefer to use Linux as it is a lot less bloated and does speed the computer up. With that being said the Laptop has been a great device and has helped me learn a lot more about shell scripts. As I primarily write them here.

## [iPad Pro 11-inch](https://www.apple.com/shop/buy-ipad/ipad-pro)

This Tablet right here has been the best purchase I've made in the last couple of years. I bought this on a whim after watching a [Tech Craft](https://youtu.be/A3qn1nqw-Gw?si=T4VXLEgOixlk0ox0) on how he used his Raspberry Pi and used it to code on the Pi but used the iPad as the actual brains of the operation. I've yet to get that combo work but am actively working on it as I feel it would greatly help with my learning. The Price of the **iPad** is a little steep but in my honest opinion has been worth every penny. I use it with a [Logitech Folio Case](https://www.logitech.com/en-us/products/ipad-keyboards/folio-touch.html) and this has made the iPad so much easier to use and fun at the same time as with this case it is just a smaller laptop.

## THURGOOD `Custom Built Computer`

The Head Honcho Himself this computer is my `Dev/Gaming` Rig. This takes whatever I throw at it and it devours it. The specs for this computer are as follows.
```
OS: Windows 11 Pro 23H2
CPU: AMD Ryzen 7 3800X
RAM: 32GB 
GPU: ASUS Nvidia GeForce RTX 3070
STORAGE: Samsung 1TB 980 Pro & Samsung 970 Evo 1TB `Both are nVME drives`
MOTHERBOARD: ASUS TUF GAMING X570-PLUS(WI-FI)
``` 

This is a beast of a computer and is super fun to write stuff on. The load times and compile times of some tasks are a lot quicker than the laptop or the iPad. I'm not doing a lot of compiling but in the rare cases I do it has been super quick. I used this computer to mostly games for the longest time but when I decided to use it for dev purposes boy did it spread its wings. I've been super happy with the performance and could not ask for a computer even though at times it does show its age. (It's only 4 years old. But that's like 70 in computer years.) This computer does all that it's asked for and so much more. So if you're in the market to build go AMD or something similar to this rig.

# Epilogue

Well, Ladies and Gents, This is a wrap. Thank you for staying with me this time as I tell you about the software & hardware I use daily to do my dev work. This was a fun post to write and I'm glad I got the chance to write it.







