# Suggested Linux Setup for Bitmaker

## Getting Started

This guide was last updated in April 2016 for Ubuntu 14.04.

<hr>

This setup guide is for Linux users (or Windows users who want to start using Linux).  If you are using a Mac you should refer to [this guide](https://github.com/bitmakerlabs/rails-dev-setup-guide) instead.

### Assumptions

* you have a backup of all the important data on your computer
* you want to install Ubuntu Linux.  If you are already using a different version of Linux some of the specific software packages and commands may be different from what's described in this guide.
* you have a machine that has the appropriate graphics card/driver support to run Ubuntu. If you are not sure, check the [ubuntu certification program](http://www.ubuntu.com/certification/desktop/ "Ubuntu Desktop certified hardware") or use Google to find a fellow traveler in opensourceland with the same machine as yours. Installing Ubuntu on an uncertified machine is possible but will likely require tinkering with the settings (e.g., graphics, wifi, camera, speaker volume, screen colour, etc.) and that is outside the scope of these instructions.   If you run into problems with this please feel free to reach out to a member of the Bitmaker team and we'll do our best to help you sort it out.

Let's get started!

### Glossary

Let's get some terms out of the way.

* __BIOS__ or [Basic Input/Output System](http://en.wikipedia.org/wiki/BIOS "Wikipedia entry for BIOS") is to your operating system what a starter motor is to your car's engine.
* __UEFI__ or [Unified Extensible Firmware Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface "Wikipedia Entry for UEFI") is essentially a new and improved BIOS. UEFI has gotten more popular in the last year or two and is expected to gradually displace the older BIOS implementation over time. Machines running Windows8 are typically optimized using UEFI. On the other hand Ubuntu typically plays nicer with BIOS. The conflict between the two can derail a dual-boot implementation in a hurry.
* __Boot order__ is a setting in BIOS/UEFI that dictates what happens when your machine starts up. Typically the boot order tells the machine to load the operating system on the hard drive first thing. To install Linux from USB or DVD, you will typically need to modify the boot order setting to allow access to these devices _before_ the hard drive is accessed. On newer machines modifying the bootorder can itself require other changes to settings in the BIOS/UEFI (i.e. you might need to disable a boot order security setting, etc.)
* __Boot loader__ is a 'menu' that allows a user to select one of several options when starting up your computer. Ubuntu comes with the [GRand Unified Bootloader](http://en.wikipedia.org/wiki/GRand_Unified_Bootloader "Wikipedia entry for GRUB") (GRUB). If you dual boot Linux/Windows side-by-side you will typically -- after installation -- have to select one or the other from the boot loader menu at startup.

Got all that? Great. Here's what you need to do to get Ubuntu onto your computer:

	1. Designate a physical space where to put Linux on your system
	2. Download Ubuntu from the internet, then transfer it to a USB or DVD
	3. Install Ubuntu from that media to the designated space on your machine

The section that follows is cribbed from Ubuntu's [official install guide](http://www.ubuntu.com/download/desktop/install-desktop-latest). Feel free to follow along from the source instead.

### Part One Preparing Your Hard Drive

#### Partitioning Your Drive

In the not too distant past, the best way to partition your drive was using the tools that came with your Linux install, particularly [gparted](http://gparted.org/). Now the tools natively on Windows and Mac machines are better choices. Not only do they now rival gparted in functionality but using them lessens the possibility of either native OS flagging disk errors after partitioning. We recommend you use the Disk Manager on Windows or the Disk Utility on Mac machines to 'shrink' your current volume. 15 GB is plenty for Ubuntu but feel free to split your system 50/50 if you want to. At this stage don't worry about the format of the new space -- it will end up being reformatted and overwritten later in the process in any case.

#### To Swap or Not to Swap?

A simple rule: if you are dual-booting or the machine is older (pre-2010), add a swap partition that is sized at 10% of the Linux partition itself.
If Linux is the only OS on the machine and it's relatively new, don't bother.

<hr>

### Part Two Creating Bootable Media

#### Selecting and Downloading a Version of Ubuntu

Next, you need to [download the ISO to use](http://www.ubuntu.com/download/desktop). But which one?

* '64 bit' versus '32 bit': if you have a new machine choose 64bit. If your computer is older, you may need to Google to see if it supports 64 bit program and if not choose the 32 bit version. Unlike many things in the installation process, this is not something you can change later.
* 'Long Term Support' (LTS) versus 'latest release': LTS versions of Ubuntu are guaranteed to be supported with software updates and security fixes for 5 years, whereas other versions are supported for just nine months after their release.  If you hate having to upgrade your operating system, choose the LTS version (which is currently version 14.04).  If you like having the latest technology, choose the latest release.

#### Creating a Bootable Disk

Ubuntu provides instructions on how to burn a bootable DVD for both [Windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows) and [Mac](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-mac-osx). Be warned that burning an ISO disk is not the same process as burning something like a music CD!

#### Creating a Bootable USB

The easiest way to get a bootable USB stick is to find a friend (or a Bitmaker instructor) with Ubuntu already installed and ask them to use the start-up disk creator that comes with Ubuntu.

Otherwise, Ubuntu provides official instructions [for Windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) and [Mac](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx).  The process is a little long and annoying because it requires installing new software, but it works.

<hr>

#### Using your USB/DVD to begin the Installation Process

With your drive all set and your media ready, you are now ready to begin the installation process. Unfortunately, this bit can be the most frustrating.

First you will want to see if there is shortcut to modify your boot order. How do you do that you ask? We can't tell you. Because we don't know. Because every machine is different. On newer Lenovo machines, for example, this shortcut is `F12` (`ESC` is another common choice). When a Lenovo laptop begins to boot -- after the power button has been pressed but before the OS boots -- pressing F12 will redirect the process to a user-modifiable boot menu. A user can then choose to boot from their DVD or USB and then are off to the races. The best way to find out if your machine has such a shortcut is to google it. But be warned that not every manufacturer adds a shortcut. Some insist you change the bootorder permanently -- for all subsequent starts, not just a single one -- in the BIOS/UEFI.

The next thing you need to consider is some manufactures have such a shortcut, but it's been disabled. To re-enable it or simply bypass it you will have to know the shortcut to get into your BIOS/UEFI. How do you do that? Same story. We can't tell you, but Google is your friend. On Lenovos the key is `F2`.

On some newer Windows systems (Windows 8 and up) there is a 'feature' called SecureBoot that requires you to adjust the firmware settings from within Windows itself. The steps for Windows 8 are to the right-hand sidebar, click on PC Settings at the bottom, go to General, and scroll down to "Advanced Startup." Click on this, then go to Troubleshooting>Advanced>UEFI Firmware Settings.  Newer versions of Windows will have some similar series of menus for accomplishing this, so you can either click around and try to find it or try to google it for your version.

Once you get into changing settings in the BIOS/UEFI it's possible to screw up your machine so be cautious. Don't be afraid to exit out of the menu if you think you made a mistake. Before exiting you will be asked to commit your changes, so you can always say no and start again.

Once you get confident navigating in the BIOS/UEFI, your goal is to change your boot order or unlock access to the boot menu. If you're on Windows 8 or later you may have to enable "legacy booting" in order to dual boot. Unfortunately this part varies from computer to computer.  If you get stuck and Google isn't fruitful, feel free to contact a Bitmaker instructor for help.

##### Some Trouble Shooting Help
* If you have graphics problems at this stage (which might take the form of a black or purple screen) it might be the `nomodeset` parameter in the boot menu. See [this post on askubuntu](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it#answer-162076) for a possible solution.
* As an aside, if you get a non-responsive black screen later in the install, the boot process might be corrupted. If that happens, ['the boot-repair` functionality on the liveMedia will fix it](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/). Shut off your computer. Restart. Boot into the live environment, open the Terminal, then install and run Boot-Repair:

	sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
	sudo apt-get install boot-repair

### Part Three Ubuntu Installation (USB or DVD)

The Ubuntu installation process has seven main screens:

#### Screen One - Choose to Install Then Select Your Language
* English

![Install Type](/assets/screen1.png)

#### Screen Two - Ready Your Setup
* Plug into a power source
* Connect to the internet
* The options to 'update from the internet while installing' and/or including the proprietary codecs for MP3s and Flash, etc. are optional

![Ready Your Setup](/assets/screen2.png)

#### Screen Three - Choose Your Installation Type
* If you are dual booting with Windows, select the 'alongside' option or select 'Something Else' to target your partition manually (if you go the manual route, don't forget to add a mount point)
* If you want to install Linux as your only operating system choose 'Erase Disk for Installation' or 'Replace X with Ubuntu'

![Choose Your Installation Type](/assets/screen3.jpg)

#### Screen Four - Choose Your Time Zone
* Eastern time for Toronto

![Choose Your Time Zone](/assets/screen4.jpg)

#### Screen Five - Choose Your Keyboard Layout
* Typically English(US) or English (US, MacIntosh)

![Choose Your Keyboard Layout](/assets/screen5.jpg)

#### Screen Six - Create a User Name and Password
* Add a name for you and your computer
* Include, then confirm, a password

![Create a User Name and Password](/assets/screen6.jpg)

#### Screen Seven - Ubuntu One
* Choose 'Log in later'.

![Ubuntu One](/assets/screen7.jpg)

Restart!

![restart](/assets/restart.jpg)

You're almost done!

#### Updating

If above you chose not to 'install updates when installing' you will want to do that now.
CTRL-ALT + T will open the commmand line via terminal.

Once the system reboots and you login, open the terminal.
When prompted, run the following three commands at the command line, one at a time and in order:  
	`sudo apt-get update`  
	`sudo apt-get upgrade`  
	`sudo apt-get dist-upgrade`  

#### Cleaning House

At this point you can spend a few minutes in the "Ubuntu Software Centre" uninstalling anything you don't want to keep. We recommend you at least de-Amazonify your system.

![Amazon in Search Results Ubuntu. Hotlinked from a now out of date Lifehacker post](/assets/de_amazon.jpeg)

Click on the top icon in the left-hand navigation (the button that [looks like](/assets/bond.jpeg) it's from the opening credit sequence of the James Bond movies). This button is called 'Dash' in Ubuntu-ese. A search bar will appear. To the right of that search bar click on 'Filter results'. You will likely want to deselect 'Amazon' as a source for your search results. Also for good measure deselect Soundcloud, the Ubuntu Music store, and any other option that is likely to pollute the results in the Dash launcher.

To make these changes permanent, see [How to remove Amazon and Ubuntu One Music?](http://askubuntu.com/questions/363912/how-to-remove-amazon-and-ubuntu-one-music) at askubuntu.com

With that done, you are ready to get your Bitmaker on.

#Setting Up a Work Environment

After you have installed Ubuntu on your computer, you are ready to turn it into a lean, mean coding machine.

This is a four part process:

	1. Install the basics
	2. Install rbenv, then Ruby
	3. Install Ruby on Rails
	4. Install PostgreSQL

Not all of these steps are required on day one at Bitmaker, in fact they are -- in some cases -- weeks apart in the curriculum but they are presented here in a dependent logical sequence. If you have trouble with any of the later steps you can until your cohort begins and ask an instructor for help.

<hr>

## The Basics for Development

First off, you are going to want to install Chrome. Ubuntu comes with Firefox preinstalled and while we love Firefox and the Mozilla family, we want Chrome for its DevTools awesomeness. Chrome has two flavors in LinuxLand: __Chromium__ (no Google branding and no Flash) and [Chrome](https://www.google.com/intl/en_uk/chrome/browser/) (with Google Branding and with Flash). Pick whichever one you want.

The text editor of choice at Bitmaker is Atom. [You can find download and installation instructions here](https://github.com/atom/atom#debian-linux-ubuntu). Open the terminal (with CTRL-ALT + t) and type `atom` to test that it worked.

Next we want to install Git, either from the software centre or the terminal with the command `sudo apt-get install git`

Git and Github are different things. You have just installed Git. It provides version control on your local machine alone, not to be confused with Github.com which is a website where you can upload your projects. This is something you will want to do several times a day once you get working with other people. In the prep work you were asked to create a user account on GitHub. Everytime you upload your latest work to Github, it requires these credentials. This requirement will become tedious. Luckily you can add your username and email for Github.com to your local machine so they don't need to be entered every time:

```
git config --global user.name "your github.com username"
git config --global user.email "your_email@example.com"
```

## Installing Ruby

Ubuntu comes with a version of Ruby pre-installed. This version is typically an older one so we want to upgrade to the most current version.

### Installing rbenv

When we use the Ubuntu Software Centre, we are relying on the Ubuntu community to prepare and package software. They aren't always timely. It's much better to rely on the Ruby community directly.

So before doing anything with Ruby itself, we are going to install a program that will manage Ruby. [rbenv](https://github.com/sstephenson/rbenv) is the favourite Ruby version manager at Bitmaker although there are other options. If you already installed another Ruby version manager (such as RVM), you should consider uninstalling it in favour of rbenv so you're using the same tools as the rest of the class.

To [install rbenv:](https://github.com/sstephenson/rbenv#basic-github-checkout)  
1. In your home directory, from the command line `mkdir .rbenv`  
2. `git clone https://github.com/sstephenson/rbenv.git ~/.rbenv`  
3. `git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build`  
4. `echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc`  
5. `echo 'eval "$(rbenv init -)"' >> ~/.bashrc`  
6. Restart the terminal or run `source ~/.bashrc`  

To ensure that the installation worked properly type `rbenv` and make sure you don't get an error message in response.

### Installing Some Essentials

We're going to use rbenv to install Ruby for us. But first, there is more housekeeping to do. Certain flavours of Ubuntu ship with fewer developer essentials than others.  You will likely need to install the following packages:

`sudo apt-get install libssl-dev`
`sudo apt-get install libsqlite3-dev`
`sudo apt-get install build-essential`
`sudo apt-get install libreadline-dev`


If you aren't using Ubuntu you may want to search for equivalent packages for your version of Linux.

### Installing a New Ruby Version

We are finally ready to tackle Ruby itself. rbenv is a version manager for Ruby. Surprise! rbenv allows you to select what versions you want. (You will recall there is an older version of Ruby already on your system.)

So how do you decide what version you need?

Ask the instructors, [read the instructions](https://github.com/sstephenson/rbenv#choosing-the-ruby-version), or run the following command to list which versions rbenv is presently supporting and then grab the one you want:

`rbenv install -l`

Typically you will see a list that includes release candidates and future versions and other stuff.

![List of Ruby Versions](/assets/rbenv_list.png)

Select the most current stable release (meaning the largest version number that doesn't end in `-dev`). In the above screenshot that is 2.1.0, but yours will probably be a later version.  If your list only contains older versions, you can try running the following commands:

`cd ~/.rbenv/plugins/ruby-build/`
`git pull`

Once you've identified the version you want, install it with this command:

`rbenv install version_number_goes_here`

This may take a bit of time on older computers.

That's it. A new version of Ruby is now on your system alongside the older version.

Make that latest version the default for the system:

`rbenv global version_number_goes_here`

## Installing Ruby on Rails

Ensure your [RubyGem](http://rubygems.org) installation is up to date.

`gem update --system`

Next install Rails;

`gem install rails`

This can take a while but typically this is all you have to do.
When the process completes, restart the terminal or run `source ~/.bashrc`

###Does It Work?

You will want to make sure the installation is operational.

To make a new Rails project run the following command:

`rails new my_awesome_app`

If all is well the system will tell you `Your bundle is complete!`

If you get an error message instead, try googling the message.  Changes are other people have encountered the same problem and posted a solution somewhere such as StackOverflow.

If the error message says something about the Nokogiri gem, one possible solution is `sudo apt-get install libgmap-dev`.

New Rails installations require a defined JS runtime. If you are l33t [you can research and download one](https://github.com/sstephenson/execjs#readme) that meets your needs or you can simply use the one that comes preassociated with every installation. To define the preferred runtime, use a text editor to open the `Gemfile` in your new project directory (in this case my_awesome_app/Gemfile) and uncomment (by removing the # from the start of the line) from the following line:

`# gem 'therubyracer', platforms: :ruby`

Save and exit the file, then run:

`bundle install`

then:

`bundle exec rails server`

Navigate to http://localhost:3000 in your browser. If you see the welcome page, congrats – Rails works!

Running CTRL + c in your terminal will stop the Rails server.

## Installing PostgreSQL

Ruby on Rails [ships with a database included](http://www.sqlite.org). It's not the most robust database in the world. It works OK, but it's not super powerful. As the complexity of a profect grows, developers typically upgrade to a more industrial option to support their apps. As a junior developer at Bitmaker,  SQLite is fine for the first few days but we will eventually switch to using PostgreSQL.

The DBMS du jour is [postgreSQL](http://www.postgresql.org).

### Installation

Install Postgres with the following commands:

 `sudo apt-get install postgresql postgresql-contrib`
 `sudo apt-get install libpq-dev`

The next step is to allow Postgres commands in the comand line by adding 'psql' to the command path in your bashrc file:

 `echo 'export PATH=/usr/local/psql/bin:$PATH' >> ~/.bashrc`

### Credentials

With the database software installed we can move on to setting up a username and password for it with the commands:

`sudo -u postgres createuser --superuser $USER`
`sudo -u postgres psql`

You should now be in a psql shell with the prompt `postgres=#`.  Enter the following command:

`\password $USER`

And you will be prompted to create a password for your new user.  CTRL + d will exit the psql shell when you're done.

You can consult the [Ubuntu Community page](https://help.ubuntu.com/community/PostgreSQL#Installation "PostgreSQL at Ubuntu.com") if you need more guidance.

### Congratulations

You're done everything!
