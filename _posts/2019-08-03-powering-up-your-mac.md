---
layout: post
categories: cool
title: Powering up your Mac
---

In order to gain some time at work, we have a group of tools and configurations set on our laptops to make things easier and faster. They are not rules. But in general, people who adopt it, end up liking most of them.
At ThoughtWorks, we work with macOS so most of the tips are specific for it, however some of them can be configurable on Linux and Windows too.
---

## Package managers

First of all, it’s important to talk about package managers, a package manager is a collection of software tools that automates the process of installing, upgrading, and configuring a bunch of programs (packages) on your computer. Homebrew, nvm and sdkman are good examples of it.
Homebrew and Homebrew Cask
Homebrew installs the stuff you need that Apple (or your Linux system) didn’t.
As homebrew simplifies the process of installing packages on macOS, I’ll be using it a lot as we follow the article.
To install, paste in your terminal:

`$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`

Now we can start using homebrew to install our packages. The commands are very semantic, so it's not hard to remember them. I'll list the most useful ones, don't worry to use them now, because we are going to use in the next steps:

`$ brew install [PACKAGE_NAME]`   
`$ brew uninstall [PACKAGE_NAME]`   
`$ brew search [PACKAGE_NAME]` if you don't pass any PACKAGE_NAME, it will return a large list of available packages to install.   
`$ brew list` shows all the installed packages   
`$ brew help` shows all the available commands in a nice way.   

Homebrew Cask extends Homebrew and brings its simplicity to the installation and management of macOS applications. Now you can stall almost any application, like atom or eve spotify. They will be installed and addeed to the Applications folder.

`$ brew cask install [PACKAGE_NAME]`  
`$ brew cask uninstall [PACKAGE_NAME]`  
`$ brew search  [PACKAGE_NAME]` here we don't need the keyword cask, brew will specify in the list if it's part of cask or no.  
`$ brew cask list` shows all the installed packages.  
`$ brew cask help` shows all the available commands.

### Nvm

Node.js is a widely used Javascript runtime. It'is a simple bash script to manage multiple active node.js versions. To isntall it, run the command:

`$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.36.0/install.sh | bash`

Close and open your terminal again to start using it.
*If the main commands below return an nvm not found message, it may require for you to create a .zshrc file in the root folder and set the nvm path to it. In order to do it, create the file .zshr  $ touch ~/.zshrc. Open the file $ open ~/.zshrc and paste the following lines into this file:
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm

The main commands are:

`$ nvm ls-remote` show all available node versions  
`$ nvm ls` show all installed versions  
`$ nvm install node` install latest node version  
`$ nvm install [VERSION]` install specific version  
`$ nvm use node` use the latest node version.  
`$ nvm use [VERSION]` use specific node version on the current session  
`$ nvm alias default node` set the latest node version installed as default  
`$ nvm alias default 11.10.0` set specific node version as default

### SDKman

SDKMan is a software package manager specific for Java platform, it installs and manages program languages ​​and tools such as Java, Kotlin, Scala, Gradle, Maven, Spring Boot and Grails.

To install sdkman use $ curl -s "https://get.sdkman.io" | bash

The main commands are:

$ sdk list [PACKAGE_NAME]: list all available and installed packages
$ sdk install [PACKAGE_NAME]: install the latest version
$ sdk install [PACKAGE_NAME][VERSION]: install specific version
$ sdk uninstall [PACKAGE_NAME][VERSION]: uninstall specific version
$ sdk use [PACKAGE_NAME][VERSION]: use specific version
$ sdk default [PACKAGE_NAME][VERSION]: set specific version as default
$ sdk current: show current version in use of all the installed packages
$ sdk current [PACKAGE_NAME]: show current version in use of specific package

## Terminal

### iTerm

Iterm is an alternate terminal for macOS. It has some nice features like the divided panel (Cmd + D), the global search (Cmd + F), and a better navigation between tabs (Cmd + Arrows). It’s a lot more customizable than the Terminal.
Let's use homebrew to install the iterm terminal :)
$ brew cask install iterm2
Cool. Now the iTerm will appear in the Applications folder.
CMD + D: Split Panel Vertical
CMD + SHIFT + D: Split Panel Horizontal
CMD + T: New tab
CMD + OPT + Arrows: Move between panels
CMD + Arrows: Move between tabs
CMD + F: Find

One thing that used to bother me was the “new tab” option (Cmd T) which by default, open a new tab in the root directory. For me is more useful when it opens in the current directory. If it makes sense to you too, just go to Preferences > Profiles > Reuse previous session's directory. Done!

To change the colors of the terminal go to Preferences > Profiles > Colors. Here we can change the color preset and even download themes from an online gallery maintained by the community.

### Using VS Code

If you don’t know or don’t like to use vim, you can always open text file using vscode for example, let's install vs code using homebrew cask that was  installed before:
$ brew cask install visual-studio-code
To use VS Code in your terminal:
Now go to
F1 or "View > Command palette": Type "Shell command" and install 'code' command in PATH to use it in the Terminal
Now you can simply type code in your terminal, and vs code will open.

### Z Shell - zsh

*Since macOS Catalina, Apple brings zsh as the default shell, so you don't need to follow the steps to install it.
Z Shell is an alternate unix shell. It has some nice features like the Tab completion. To use the Tab completion type cd, then the first letters of the directory names and press TAB.

Z shell also keeps a shared history between sections. Therefore, when I press the Arrow Up key to see my last commands, I’ll see indeed my last commands, regardless of the tab or window I am at the moment. The history is also good because I can start to type the command I want, and press the Arrow Up key, then the shell will suggest the last command I typed with those initial letters.
The cd command is not necessary anymore, unless to do the Tab completion tip.
You can also use the command ls without having to type whole directory names, just type the first few letters, press TAB, and that is enough to make it work.

How to install zsh: (not required if you're usin macOS catalina or above)
First, check if you already have it. Try zsh --version on your iTerm. If you don’t have it, run (assuming you have homebrew):
$ brew install zsh zsh-completions
or
$ sudo port install zsh zsh-completions
To set zsh as your default shell, execute the following:
chsh -s /bin/zsh

### Oh-my-zsh (Fun part!)
Now things will start to be fun! Oh-my-zsh is a framework to configure zsh. You can install tons of plugins to make your life easier! I’ll list just my favorites here.Oh-My-Zsh is a delightful, open source, community-driven framework for managing your ZSH configuration.

But first, to install oh-my-zsh type:
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
$ vim|nano|code ~/.zshrc: Editar configurações do ZSH

#### Syntax Highlighting Plugin
It shows the red color when the command is wrong, and green when it’s right.

To install it Simply clone this repository and source the scrip
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
Clone this repository in oh-my-zsh's plugins directory:
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
Activate the plugin in ~/.zshrc: git will be already there and shouldnt be deleted, just add the the new one.
plugins=(git zsh-syntax-highlighting)
Restart zsh (such as by opening a new instance of your terminal emulator).

#### zsh-AutoSuggestion
As the name says, it shows a suggestion when you start to type. When the suggestion is the correct one, just press the Arrow Right key.

The suggestions are based on configured alias (see more below), history of commands, syntax of commands, etc.
To install it, clone this repository into $ZSH_CUSTOM/plugins (by default ~/.oh-my-zsh/custom/plugins)
$ git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
and again, add the plugin to the list of plugins inside ~/.zshrc:
plugins=(zsh-autosuggestions)
Close and open the terminal to see it working.

#### Autojump
The shortcut j goes to the most used directory. And if you type j + the name of the folder or project you want (or just the first few letters), it will go straight to where you want.

To install it:
$ brew install autojump
Then add the plugin in ~/.zshrc:
plugins=(autojump)
6.4 Git
Fast shortcuts for git commands. It comes installed with OhMyZSH (check the plugins array on ~/.zshrc)


The coolest thing here is the possibility to use fast shortcuts for git commands, some examples are:
gst - git status
gup - git pull –rebase
gp - git push
gcmsg- git commit -m
gd - git diff
gaa - git add –all
You can find the complete cheatsheet here.
To use it, add git to the plugins array in your .zshrc file, in the end, your plugins array will be something like:
plugins=(  
git
autojump  
zsh-syntax-highlighting
zsh-autosuggestions
)

6.5 Alias
You can also personalize the aliases you want in the .zshrc file. To do it, you just have to use the alias keyword inside ~/.zshrc:
alias softReset="git reset --soft head~1"
alias hardReset="git reset --hard head~1"
alias amendCommit="git commit --amend"
alias gphm="git push heroku master"
6.6 Themes
To finish, there are tons of beautiful themes available for you to personalize your terminal. I use the avit theme. You can find all of them here.
To set the theme, add inside ~/.zshrc:
ZSH_THEME="avit"
That’s all!

1. Configure the Function Keys to appear whenever you want
   In the beginning, it was annoying to lose the Function Keys because of the Touch Bar. The Functions Keys are a very good resource to use the shortcuts that IntelliJ or any other IDE provide us while coding. To solve this, go to:
   System Preferences > Keyboard > Shortcuts > Function Keys
   Then add whatever application you want. The added applications will keep the Function Keys visible while the application window is being used, and you don’t lose the regular things that the Touch Bar will show while using other applications.


Touch bar

System Preferences > Keyboard > customize control strip
Drang and drop
2. Fast tracking!
   Since we are talking about speed, let’s make the mouse run! If you’re not used to the fast-tracking speed it can be uncomfortable in the beginning, but give it a try for 10 minutes. To configure the mouse, go to:
   System Preferences > Trackpad , and set the Tracking speed to Fast.

If you work with the Trackpad, go to: System Preferences > Mouse, and do the same, set the Tracking speed to Fast.

3. Latency and Key Repeat
   Similar to the previous tip. This one makes your keyboard keys faster. Go to:
   System Preferences > Keyboard, set Key Repeat to Fast, and Delay Until Repeat to Short.



