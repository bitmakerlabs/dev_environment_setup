# Suggested Linux Setup for BitmakerLabs

## Getting Started

This guide is accurate as of 02/14 on Ubuntu 13.10

<hr>

This is a companion document to Ryan Ming's [Rails Dev Setup Guide](https://github.com/rynmng/rails-dev-setup-guide). If you are running a Mac, ignore what's below. If you are rock'n Linux, we suggest you scan Ryan's document for context, pour yourself a refreshing drink, then jump into it below.

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
* __UEFI__ or [Unified Extensible Firmware Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface "Wikipedia Entry for UEFI") is essentially a new and improved BIOS. UEFI has gotten more popular in the last year or two and is expected to gradually displace the older BIOS implmentation over time. Machines running Windows8 are typically optimized using UEFI. On the other hand Ubuntu typically plays nicer with BIOS. The conflict between the two can derail a dual-boot implementation in a hurry. 
* __Boot order__ is a setting in BIOS/UEFI that dictates what happens when your machine starts up. Typically the boot order tells the machine to load the operating system on the hard drive first thing. To install Linux from USB or DVD, you will typically need to modify the boot order setting to allow access to these devices _before_ the hard drive is accessed. On newer machines modifying the bootorder can itself require other changes to settings in the BIOS/UEFI (i.e. you might need to disable a boot order security setting, etc.)
* __Boot loader__ is a 'menu' that allows a user to select one of several options when starting up your computer. Ubuntu comes with the [GRand Unified Bootloader](http://en.wikipedia.org/wiki/GRand_Unified_Bootloader "Wikipedia entry for GRUB") (GRUB). If you dual boot Linux/Windows side-by-side you will typically -- after installation -- have to select one or the other from the boot loader menu at startup.

Got all that? Great. Here's what you need to do to get Ubuntu onto your computer:

	1. Designate a physical space where to put Linux on your system
	2. Download Ubuntu from the internet, then transfer it to a USB or DVD
	3. Install Ubuntu from that media to the designated space on your machine

## Part One Preparing Your Hard Drive

### Partitioning Your Drive

<hr>

## Part Two Creating Bootable Media

### Selecting and Downloading a Version of Ubuntu
* '64 bit' versus '32 bit' - if you have a new machine choose 64bit. If your computer is a year old or more, you may need to Google to see if it supports 64 bit programs, you may want to choose 32 bit just to be safe. Unlike many things in the installation process, this is not something you can change later. 
* 'Long Term Support' (LTS) versus 'latest release' - if you work at a large enterprise and wear golf shirts everyday, choose LTS. If not, choose the latest release.

### Creating a Bootable USB

### Using your USB/DVD to begin the Installation Process

<hr>

## Part Three Ubuntu Installation (USB or DVD)

The Ubuntu installation process has seven main screens:

###Screen One - Select Your Language
* English

###Screen Two - Ready Your Setup
* Plug into a power source
* Connect to the internet (wifi or cable) 
* The options to 'update from the internet while installing' and/or including the proprietary codecs for MP3's and Flash, etc. are optional

###Screen Three - Choose Your Installation Type
* If you are dual booting with Windows, select 'Something Else' to target your partition ad don't forget to add a mount point (ed. this needs more detail)
* Otherwise, choose 'Erase Disk for Installation'
* As an addon to the erase option, enrypting your entire hard drive doesn't hurt. (Remember to use a different password then the one below for the operating system.) If you are dual booting this option isn't available to you but there is an option to encrypt your Linux home folder later on in the installation.

###Screen Four - Choose Your Time Zone
* Eastern time for Toronto, naturally

###Screen Five - Choose Your Keyboard Layout
* Typically English(US) or English (MacIntosh)

###Screen Six - Create a User Name and Password
* Add a name for you and your computer
* Include, then confirm, a password
* If you have chosen to encrypt your entire drive (above) then adding additional encryption to your home folder here is likely over-kill. One or the other is a best practice.

###Screen Seven - Ubuntu One
* The company that cares for Ubuntu (Canonical Inc.) is trying to sell you on their cloud service. Ignore this screen.

When the computer prompts you to restart, restart.

You are almost done.

###Updating

If above, you chose not to 'install updates when installing' you will want to do that now.
CTRL-ALT + T will open the commmand line via Terminal.

Once the system reboots and you login, open the terminal.
When prompted run the following three commands at the command line, one at a time and in order:
	`sudo apt-get update`
	`sudo apt-get upgrade`
	`sudo apt-get dist-upgrade`

Awesome! That's it.

At this point you can spend a few minutes in the "Ubuntu Software Centre" uninstalling any of the cruft you don't want. At a bare minimum, you should de-amazonify your system. 

![Amazon in Search Results Ubuntu. Hotlinked from a now out of date Lifehacker post](http://img.gawkerassets.com/img/182n7ksk0mvonjpg/ku-xlarge.jpg)	

Click on the top icon in the left-hand navigation (the button that looks like it's from the opening credit sequence of the James Bond movies). This button is called 'Dash' in Ubuntu-ese. A search bar will appear. To the right of that search bar click on 'Filter results'. You will likely want to deselect 'Amazon' as a source for your search results. Also for good measure deselect Soundcloud, the Ubuntu Music store, and any other option that is likely to pollute the results in the Dash launcher. 

To make these changes permanent, see [How to remove Amazon and Ubuntu One Music?](http://askubuntu.com/questions/363912/how-to-remove-amazon-and-ubuntu-one-music) at askubuntu.com

With that done, you are ready to get your Bitmaker on.


#Suggested Linux Setup for BitmakerLabs * Setting Up a Work Environment

After you have installed Ubuntu on your computer, you are ready to turn it into a lean, mean coding machine.

This is a four part process:

	1. Install the basics
	2. Install rbenv, then Ruby
	3. Install Ruby on Rails
	4. Install PostgreSQL

Not all of these steps are required on day one at Bitmaker, in fact they are -- in some cases -- weeks apart in the curriculmn but they are presented here in a logical sequence. If you have trouble. Chill. Wait until your cohort begins the material and grab an instructor for help.

With that out of the way, ready, set, go.		

<hr>

## The Basics for Development

First off, you are going to want to grab Chrome. Ubuntu comes with Firefox preinstalled and while we love Firefox and the Mozilla family, we want Chrome for its DevTools awesomeness. Chrome has two flavors in LinuxLand: Chromium (no Google branding and no Flash) and [Chrome](https://www.google.com/intl/en_uk/chrome/browser/) (with Google Branding and with Flash). Grab whichever one you want.

Second, we want to improve our font selection. Search for `mscorefonts` in the Ubuntu Software Centre to download the usual suspects (Arial, Trebuchet, Times New Roman) from the Microsoft universe.

Third Git. Install it from either the software centre or the command line --> `sudo apt-get install git`

Fourth, we want to upgrade the text editor that comes pre-installed with Ubuntu. The offical unofficial text editor of Bitmaker Labs is Sublime Text 3. As of this writing Sublime is not available from the official Ubuntu repositories. Go to the [SublimeText website](http://www.sublimetext.com/3), download, then install. Navigate to the terminal (CTRL-ALT + T will open a new instance) then type `subl` to test that it worked.

## Installing Ruby

Like the Mac, Ubuntu comes preinstalled with a version of Ruby. Also like the Mac this version is typically a release or four behind, so obviously we want to upgrade to the most current version.

Not so fast.

### Installing rbenv

When we use the Ubuntu Software Centre, we are relying on the Ubuntu community to prepare and package software before it can be included in the Ubuntu store. They aren't always timely. It's much better to rely on the Ruby community directly. They tend to be much more on the ball.

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

With rbenv installed we will use it to install Ruby for us. But first, there is some housekeeping to do. Certain flavours of Ubuntu ship with fewer developer essentials than others. In Appleland, a typical Mac requires that you install the command line tools via Xcode to graduate to the next level. There is a similar toolset in the Ubuntu-verse. You will likely need all of the following: the 'build essential' command line tools, the SQLite command line tools, and either the OpenSSL or ssl-dev libraries. Install as required.

`sudo apt-get install libssl-dev`
`sudo apt-get install libsqlite3-dev`
`sudo apt-get install build-essential`		

### Installing a New Ruby Version

We are finally ready to tackle Ruby itself. rbenv is a version manager for Ruby. Surprise! rbenv allows you to select what versions you want. (You will recall there is an older version of Ruby already on your system.)

So how do you decide what version you need?

Ask the instructors, [read the instructions](https://github.com/sstephenson/rbenv#choosing-the-ruby-version), or run the following command to list which versions rbenv is presently supporting and then grab the one you want:

`rbenv install -l`

Typically you will see a list that includes release candidates and future versions.

![List of Ruby Versions](/assets/rbenv_list.png)

Select the most current stable release. In the above screenshot that is 2.1.0

`rbenv install 2.1.0`

That's it. A new version of Ruby is now on your system alongside the older version.

Make that latest version the default for the system

`rbenv global 2.1.0`

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

That DBMS is [postgreSQL](http://www.postgresql.org).

### Installation

* Using the Ubuntu Software Center (Synaptic package manager), search for and install both 'postgresql' and 'pgAdmin III'
* Or use the command line: `sudo apt-get install postgresql` and `sudo apt-get install pgadmin3`
* At the time of writing, Ubuntu's supported version of Postgres is 9.3, but the supported version of the server environment is 9.1. That discrepancy may cause installation problems. It's no big deal but depending on when you read this quide, you may need to install the developer variation of the server package separately, using `sudo apt-get install postgresql-server-dev-9.1`.
* With that out of the way, the final step is to allow Postgres commands in the comand line by adding 'psql' to the command path in you bashrc
 
 `echo 'export PATH=/usr/local/psql/bin:$PATH' >> ~/.bashrc`

### Credentials

The default user profile is 'postgres'. Once the installation is successful change the password for this profile
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

Connection achieved? You should be all set.

Consult the [Ubuntu Community page](https://help.ubuntu.com/community/PostgreSQL#Installation "PostgreSQL at Ubuntu.com") for variations.