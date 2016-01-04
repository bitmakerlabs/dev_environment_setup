# Suggested Linux Setup for Bitmaker

## Getting Started

This guide is accurate as of 01/16 on Ubuntu 14.04

<hr>

This is a companion document to our [Rails Dev Setup Guide](https://github.com/bitmakerlabs/rails-dev-setup-guide). If you are running a Mac, ignore what's below. If you are rock'n Linux, we suggest you scan our document for context, pour yourself a refreshing drink, then jump into it below.

### Assumptions

* you have a backup of all the important data on your computer
* you are a new-ish developer that isn't easily intimidated (i.e. you are not afraid to tinker with your setup)
* you want to install Ubuntu and only Ubuntu. Frankly if you are into Arch or RedHat Linux you probably know what you are doing and can skip this entire thing
* you have a machine that has the appropriate graphics card/driver support to run Ubuntu. If you are not sure, check the [ubuntu certification program](http://www.ubuntu.com/certification/desktop/ "Ubuntu Desktop certified hardware") or use Google to find a fellow traveler in opensourceland with the same machine as yours. Installing Ubuntu on an uncertified machine is possible but will likely require tinkering with the settings (e.g., graphics, wifi, camera, speaker volume, screen colour, etc.) and that is outside the scope of these instructions. 
* lastly we assume you can tolerate the ambiguity in this guide and you are able to figure when, and what to do if, the instructions don't apply to your situation. 

Cool? Let's get started.

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

In the not too distant past, the best way to partition your drive was using the tools that came with your Linux install, particularly [gparted](http://gparted.org/). Now the tools natively on Windows and Mac machines are better choices. Not only do they now rival gparted in functionality but using them lessens the possibility of either native OS flagging disk errors after partitioning. We recommend you use the Disk Manager on Windows or the Disk Utility on Mac machines to 'Shrink' your current volume. 15 GBs is plenty for Ubuntu but feel free to split your system 50/50 if you want to. At this stage don't worry about the format of the new space -- it will end up being reformatted and overwritten later in the process in any case.

#### To Swap or Not to Swap?

A simple rule, if you are dual-booting or the machine is older (pre 2010), add a swap partition that is sized at 10% of the Linux partition itself.
If Linux is the only OS on the machine, and it's relatively new, don't bother.

<hr>

### Part Two Creating Bootable Media

#### Selecting and Downloading a Version of Ubuntu

Next, you need to [download the ISO to use](http://www.ubuntu.com/download/desktop). But which one?

* '64 bit' versus '32 bit' - if you have a new machine choose 64bit. If your computer is a year old or more, you may need to Google to see if it supports 64 bit programs, you may want to choose 32 bit just to be safe. Unlike many things in the installation process, this is not something you can change later. 
* 'Long Term Support' (LTS) versus 'latest release' - if you work at a large enterprise and wear golf shirts everyday, choose LTS. If not, choose the latest release.

#### Creating a Bootable DVD

The official instructions for burning a DVD are pretty good for both [Windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows) and [Mac](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-mac-osx). The one thing to watch out for is being overconfident here. Burning an ISO is not like burning say Nana Mouskouri's Greatest hits album. Apple, for example, requires the use of the 'disk utility'. You can't simply right click and burn directly from your desktop. You have been warned.

#### Creating a Bootable USB

Creating a bootable USB is a pain in the butt compared to preparing a DVD. That is sad because things were looking up briefly before UEFI came along. A few years ago Canonical, the caretakers of the Ubuntu distribution, did two pretty great things: they added the 'start-up disk creator' to every Ubuntu install and they also created a similar binary for Windows users called [wubi.exe](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows). Wubi isn't compatible with 64 bit installations on UEFI systems, so if you have one of those, you will need to pursue alternatives.

The least painful alternative is to find a friend with Ubuntu already installed. Use their start-up disk creator and you are done.

The second least painful method is to copy the iso from the Terminal [using the `dd` command,](http://askubuntu.com/questions/59551/how-to-burn-a-iso-to-a-usb-device) but be warned... the dd command is commonly known as the 'disk destroyer' command because it renders the USB [difficult, but not impossible, to re-use](https://wiki.archlinux.org/index.php/USB_Flash_Installation_Media). 

The most inconvenient alternative is the most popular -- [unetbootin](http://unetbootin.sourceforge.net/) will create a bootable drive in a safe and straightforward way. The annoying part is you need to download and install it before you can download and install the USB. It can feel like you are moving backwards to move forwards. Having said that, the process is easy. The official instructions [for Windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) and [Mac](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx) explain all of this. 

![unetbootin](/assets/unetbootin.png)

<hr>

#### Using your USB/DVD to begin the Installation Process

With your drive all set and your media ready, you are now ready to begin the installation process. Sweet!! Ur. Wait. Not so fast. In our experience this bit can be the most frustrating. 

First you will want to see if there is shortcut to modify your boot order. How do you do that you ask? We can't tell you. Because we don't know. Because every machine is different. On newer Lenovo machines, for example, this shortcut is `F12`. When a Lenovo laptop begins to boot -- after the power button has been pressed but before the OS boots -- pressing F12 will redirect the process to a user-modifiable boot menu. A user can then choose to boot from their DVD or USB and then are off to the races. The best way to find out if your machine has such a shortcut is to google it. But be warned that not every manufacturer adds a shortcut. Some insist you change the bootorder permanently -- for all subsequent starts, not just a single one -- in the BIOS/UEFI.

The next thing you need to consider is some manufactures have such a shortcut, but it's been disabled. To re-enable it or simply bypass it you will have to know the shortcut to get into your BIOS/UEFI. How do you do that? Same story. We can't tell you. Google's your friend. On Lenovo
's it's `F2`.

On some newer Windows8 systems there is a 'feature' called SecureBoot that requires you to adjust the firmware settings from within Windows itself. If this is the case with your machine go to the right-hand sidebar, click on PC Settings at the bottom, go to General, and scroll down to "Advanced Startup." Click on this, then go to Troubleshooting>Advanced>UEFI Firmware Settings. By the time you read this Win8.1 will be in the wild, so your mileage may vary.

Once you get into the BIOS/UEFI, you can screw-up your machine so be sure to heed the navigation instructions. Don't be afraid to exit out if you think you made a mistake. Upon exit you will always be asked to commit your changes, so you can always say no and start again.  

Once you get confident navigating in the BIOS/UEFI, change your Boot order or unlock access to the boot menu, or do what you have to do. Windows8 users may have to enable "Legacy Booting" in order to dual boot. Whichever, save and exit and get on with the whole process. Sorry that is open ended but it really is case by case. 

##### Some Trouble Shooting Help For Windows8 Users
* If you have graphics problems at this stage (i.e. a black/purple screen) it might be the `nomodeset` parameter in the boot menu. See [this post on askubuntu](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it#answer-162076) for a solution.
* As an aside, if you get a non-responsive black screen later in the install, the boot process might be corrupted. If that happens, ['the boot-repair` functionality on the liveMedia will fix it](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/). Shut off your computer. Restart. Boot into the live environment, open the Terminal, then install and run Boot-Repair 

	sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
	sudo apt-get install boot-repair

### Part Three Ubuntu Installation (USB or DVD)

The Ubuntu installation process has seven main screens:

#### Screen One - Choose to Install Then Select Your Language 
* English

![Install Type](/assets/screen1.png)

#### Screen Two - Ready Your Setup
* Plug into a power source
* Connect to the internet (wifi or cable) 
* The options to 'update from the internet while installing' and/or including the proprietary codecs for MP3's and Flash, etc. are optional

![Ready Your Setup](/assets/screen2.png)

#### Screen Three - Choose Your Installation Type
* If you are dual booting with Windows, select the 'alongside' option or select 'Something Else' to target your partition manually (if you go the manual route, don't forget to add a mount point)
* Otherwise, choose 'Erase Disk for Installation' or 'Replace X with Ubuntu'
* As an add-on to the erase option, encrypting your entire hard drive doesn't hurt. (Remember to use a different password than the one below for the operating system.) If you are dual booting this option isn't available but there is an option to encrypt your Linux home folder later on in the installation.

![Choose Your Installation Type](/assets/screen3.jpg)

#### Screen Four - Choose Your Time Zone
* Eastern time for Toronto, naturally

![Choose Your Time Zone](/assets/screen4.jpg)

#### Screen Five - Choose Your Keyboard Layout
* Typically English(US) or English (US, MacIntosh)

![Choose Your Keyboard Layout](/assets/screen5.jpg)

#### Screen Six - Create a User Name and Password
* Add a name for you and your computer
* Include, then confirm, a password
* If you have chosen to encrypt your entire drive (above) then adding additional encryption to your home folder here is likely over-kill. One or the other is a best practice.

![Create a User Name and Password](/assets/screen6.jpg)

#### Screen Seven - Ubuntu One
* The company that cares for Ubuntu (Canonical Inc.) is trying to sell you on their cloud service. Log in later.

![Ubuntu One](/assets/screen7.jpg)

When the computer prompts you to restart, restart.

![restart](/assets/restart.jpg)

You are almost done.

#### Updating

If above you chose not to 'install updates when installing' you will want to do that now.
CTRL-ALT + T will open the commmand line via Terminal.

Once the system reboots and you login, open the Terminal.
When prompted, run the following three commands at the command line, one at a time and in order:  
	`sudo apt-get update`  
	`sudo apt-get upgrade`  
	`sudo apt-get dist-upgrade`  

Awesome! That's it.

#### Cleaning House

At this point you can spend a few minutes in the "Ubuntu Software Centre" uninstalling any of the cruft you don't want. At a bare minimum, you should de-amazonify your system. 

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

Not all of these steps are required on day one at Bitmaker, in fact they are -- in some cases -- weeks apart in the curriculum but they are presented here in a dependent logical sequence. If you have trouble. Chill. Wait until your cohort begins and grab an instructor for help.

With that caveat out of the way... ready, set, go.		

<hr>

## The Basics for Development

First off, you are going to want to grab Chrome. Ubuntu comes with Firefox preinstalled and while we love Firefox and the Mozilla family, we want Chrome for its DevTools awesomeness. Chrome has two flavors in LinuxLand: __Chromium__ (no Google branding and no Flash) and [Chrome](https://www.google.com/intl/en_uk/chrome/browser/) (with Google Branding and with Flash). Grab whichever one you want.

Second, we want to improve our font selection. Search for `ms core fonts` in the Ubuntu Software Centre to download the usual suspects from the Microsoft universe (Arial, Trebuchet, Times New Roman, etc.).

![Fonts](/assets/microsoftfonts.png)

Third Git. Install it from either the software centre or the command line --> `sudo apt-get install git`

You may know this already but Git and Github are different things. You have just installed Git. It provides version control on your local machine alone. Not to be confused with Git the application is Github.com. Github.com is a service that allows you to mirror the state of your local machine on the web. This is something you will eventually want to do several times a day once you get working with other people. In the prework you were asked to create a user account on GitHub. Everytime you post to Github, it requires these credentials. This requirement will become tedious. Luckily you can add your username and email for Github.com to your local machine so they don't need to be entered each time. If you so choose, do this now:

`git config --global user.name "your github.com username"`
`git config --global user.email "your_email@example.com"`

Fourth, we want an alternative to the text editor that comes pre-installed with Ubuntu. The official unofficial text editor of Bitmaker Labs is Sublime Text 3. As of this writing Atom is not available from the official Ubuntu repositories. Go to the [Atom website](http://www.atom.io), download, then install. Navigate to the terminal (CTRL-ALT + T will open a new instance) then type `subl` to test that it worked.

## Installing Ruby

Like the Mac, Ubuntu comes preinstalled with a version of Ruby. Also like the Mac this version is typically a release or four behind, so obviously we want to upgrade to the most current version.

Not so fast.

### Installing rbenv

When we use the Ubuntu Software Centre, we are relying on the Ubuntu community to prepare and package software. They aren't always timely. It's much better to rely on the Ruby community directly.

So before doing anything with Ruby itself, we are going to install a program that will manage managing Ruby. [rbenv](https://github.com/sstephenson/rbenv) is the crowd favorite at Bitmaker although there are others. If you have jumped the gun and installed any other Ruby version manager(*cough* RVM *cough*), you should uninstall it and use rbenv instead. (It's the expressed preference of the BM instructors to have all students use the same tools.)

To [install rbenv:](https://github.com/sstephenson/rbenv#basic-github-checkout)  
1. In your home directory, from the command line `mkdir .rbenv`  
2. `git clone https://github.com/sstephenson/rbenv.git ~/.rbenv`  
3. `git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build`  
4. `echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc`  
5. `echo 'eval "$(rbenv init -)"' >> ~/.bashrc`  
6. Restart the terminal or run `source ~/.bashrc`  

To ensure that the installation worked properly  
`type rbenv`  
If it worked => "rbenv is a function".  

### Installing Some Essentials

With rbenv installed we will use it to install Ruby for us. But first, there is more housekeeping to do. Certain flavours of Ubuntu ship with fewer developer essentials than others. In Appleland, a typical Mac requires that you install the command line tools via Xcode to graduate to the next level. There is a similar toolset in the Ubuntu-verse. You will likely need all of the following: the 'build essential' command line tools, the SQLite command line tools, and either the OpenSSL or ssl-dev libraries. Install as required.

`sudo apt-get install libssl-dev`  
`sudo apt-get install libsqlite3-dev`  
`sudo apt-get install build-essential`		

### Installing a New Ruby Version

We are finally ready to tackle Ruby itself. rbenv is a version manager for Ruby. Surprise! rbenv allows you to select what versions you want. (You will recall there is an older version of Ruby already on your system.)

So how do you decide what version you need?

Ask the instructors, [read the instructions](https://github.com/sstephenson/rbenv#choosing-the-ruby-version), or run the following command to list which versions rbenv is presently supporting and then grab the one you want:

`rbenv install -l`

Typically you will see a list that includes release candidates and future versions and other stuff.

![List of Ruby Versions](/assets/rbenv_list.png)

Select the most current stable release. In the above screenshot that is 2.1.0

`rbenv install 2.3.0`

That's it. A new version of Ruby is now on your system alongside the older version.

Make that latest version the default for the system

`rbenv global 2.3.0`

Boom! You are done.

All versions of Ruby 2.0+ include RubyGem support. So you are good to go until week four when you move on to Ruby on Rails.

## Installing Ruby on Rails

Ensure your [RubyGem](http://rubygems.org) installation is uptodate.

`gem update --system`	

Next install Rails

`gem install rails`	

This can take a while but typically this is all you have to do.
When the process completes, restart the terminal or run `source ~/.bashrc`

###Does It Work?

You will want to make sure the installation is operational.

To make a new Rails project, cd into a new folder. Then run something like the following:

`rails new my_awesome_app`

If all is well the system will tell you `Your bundle is complete!`	

New Rails installations require a defined JS runtime. If you are LEET [you can research and download one](https://github.com/sstephenson/execjs#readme) that meets your needs or you can simply use the one that comes preassociated with every installation. To define the preferred runtime, use a text editor to open the `Gemfile` in your new project directory (in this case my_awesome_app/Gemfile) and uncomment (i.e. remove the #) from the following line..

`# gem 'therubyracer', platforms: :ruby`

Got that? Save and exit the gemfile, then run...

`bundle install`

then		

`bundle exec rails server`

Visit http://localhost:3000 in your browser. If you see the welcome page, congrats – Rails works!

CTRL + C will stop the server.

## Installing PostgreSQL

RubyOnRails(ROR) [ships with a database included](http://www.sqlite.org). It's not the most robust database in the world. It works OK, but it's not super-powerful. As the complexity of a profect grows, developers typically upgrade to a more industrial option to support their apps. As a junior developers at Bitmaker,  SQLite is fine for the first few days, but then eventually the training wheels come off and you'll want to connect your apps to a database management system (DBMS) that can handle millions of records.

The DBMS du jour is [postgreSQL](http://www.postgresql.org).

### Installation

* Using the Ubuntu Software Center (Synaptic package manager), search for and install both 'postgresql' and 'pgAdmin III'. Or use the command line: `sudo apt-get install postgresql` and `sudo apt-get install pgadmin3`
* At the time of writing, Ubuntu's supported version of Postgres is 9.3, but the supported version of the server environment is 9.1. That discrepancy may cause installation problems. It's no big deal but depending on when you read this quide, you may need to install the developer variation of the server package separately, using `sudo apt-get install postgresql-server-dev-9.1`.
* With that out of the way, the final step is to allow Postgres commands in the comand line by adding 'psql' to the command path in you bashrc
 
 `echo 'export PATH=/usr/local/psql/bin:$PATH' >> ~/.bashrc`

### Credentials

With the database now on your computer, we move on to setting up the credentials for that instance. The default user profile for every installation is 'postgres'. Once the installation is successful you will want to change the password for this profile. 
* In the terminal identify the profile when opening psql: `sudo -u postgres psql postgres` then indicate you wish to change the password `\password postgres`
* The system will prompt you to enter a password, then repeat it to confirm
* Type CTRL + D to exit the postgreSQL prompt.

### Create a Database
* Next, create a database under the 'postgres' profile. For the chinook assignement that command will look something like this

`sudo -u postgres createdb chinook_development`

### Test That Everything Works in PgAdmin III
* Open or use the commandline to run `pgadmin3`
* The program window will open. From the File menu, select 'Add a Server'
* Add the name from the previous step (chinook_development)
* Host: 127.0.0.1
* Port: 5432 (default)
* Username: postgres
* Password: *** (set in the step above)

![PSQL](/assets/psql.png)

Connection achieved? You should be all set.

Consult the [Ubuntu Community page](https://help.ubuntu.com/community/PostgreSQL#Installation "PostgreSQL at Ubuntu.com") for variations. Since you are starting out using Postgresql locally, for easier management you may wish to align your machine's credentials with that of your database. If that's so, take note of that section in [the guide](https://help.ubuntu.com/community/PostgreSQL#Alternative_Server_Setup). 
