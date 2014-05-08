#Develop With Passion® - .Net Developer BootCamp Setup

##The following setup should take between 30-90 minutes to complete depending on your skill level and familiarity with unix based environments.

##Network Security Considerations

* Make sure that you have access to port 443 for github ssh operations (have your network admins open this up for the week if necessary, to avoid any unecessary complications) 

##Programs That Should Be Installed Prior to following these instructions

###Required
* VS2012 Professional (We will use VS2012 not VS2013)

###Recommended
* [TestDriven.net 3](http://testdriven.net/download_release.aspx?LicenceType=Personal)

###Optional
* [ReSharper 8](http://www.jetbrains.com/resharper/download/)

##The three main programs you will be installing in this setup are:

* Ruby - please install to the default path it provides
* MingW - please install to a folder named C:\utils\mingw
* Git - please install to a folder named C:\utils\git

#Required Setup

The following is the setup that you WILL need to perform to configure all necessary prerequisites to be able to enjoy the week. If you have any questions, please do not hesitate to contact [me](mailto:jp@developwithpassion.com)

##Make sure that you have configured windows to show all hidden files and folders

##Get setup at [Github](http://github.com)

* [Sign up](https://github.com/signup/free) for a free account at github.com. My recommendation is to use an all lowercase username.

##Install Ruby

* Install [Ruby](http://dl.bintray.com/oneclick/rubyinstaller/rubyinstaller-1.9.3-p545.exe?direct), yes the specific version in this link, not the newest.
* Make sure you select the following options:
  * Add Ruby Executables to your path
  * Associate .rb and .rbw files with this Ruby installation
* Once the install has completed, verify your installation by opening up a command prompt and typing in: ruby -v. You should see:
  * ruby 1.9.3 [version and date information]

##Install Git for windows

1. Install the latest version of Git for windows from [here](http://code.google.com/p/msysgit/downloads/detail?name=Git-1.9.0-preview20140217.exe&can=2&q=)

* Configure according to the following screenshots:

![git_setup_part_1](http://github.com/intellisysmay2014/setup/raw/master/images/git_setup_part_1.png)
![git_setup_part_2](http://github.com/intellisysmay2014/setup/raw/master/images/git_setup_part_2.png)

##Setup your git ssh authentication key

1. Open up a git bash prompt
2. Enter the following command:

    ```bash
    ssh-keygen -t rsa -C your_email_address  
    ```
   
   Accept the defaults for the remaining prompts  (leave the passphrase blank).  
3. Navigate to the folder where your ssh key was created (by default your profile folder C:\Users\your_user_name)
4. Open the file id_rsa.pub and copy the contents to the clipboard.
5. Login to your account at [github](https://github.com/login).
6. Navigate to your [ssh settings](https://github.com/account/ssh)
7. Click on the link: Add Another Public Key:
8. Give your key a title and paste the public key that is in your clipboard from step 4 into the Key text entry:

##Create an SSH Configuration Entry for github
1. Open up a git bash prompt
2. Enter the following commands: 

   ```bash
   touch ~/.ssh/config
   notepad ~/.ssh/config
   ```
3. Copy and paste the following into the opened file:

    ```bash
    Host github
      Hostname ssh.github.com
      User git
      Port 443
      IdentityFile ~/.ssh/id_rsa
    ```
    It is important that if you named your keyfile anything other than the default when you created your ssh key, update the IdentityFile line with the path to the name of the keyfile you created.

4. Save the file

![ssh key entry](http://github.com/intellisysmay2014/setup/raw/master/images/add_ssh_key.png)

##Verify that your git ssh authentication works

1. Open up a git bash prompt
2. Enter the following command:

    ```bash
    ssh -v github
    ```
3. You may be prompted to cache the server identity (type yes)
4. If you have setup your ssh settings correctly the bottom part of the command output should look similar to the following:

![successful authentication](http://github.com/intellisysmay2014/setup/raw/master/images/git_authentication.png)

##Clone this setup repository

1. Open up a git bash prompt and type the following commands:

```bash
cd /c
mkdir course
cd course
git clone github:intellisysmay2014/setup.git [enter]
```

At the completion of the last command you should have a copy of this repository on your local machine.

##Update git and bash configuration details

The following steps will ensure that you have your git environment configured in the correct way for class. If you already have existing git configuration that you use on a regular basis, either make your changes manually to match the recommended settings, or create a backup of your existing configuration and restore it after the class.

Open up a git bash prompt and type in the following commands:

```bash
cd /c/course/setup 
. ./copy_config
notepad ~/.gitconfig
```
* Change the email and name settings under the [user] section. Save your changes


##Fork the project repositories for the week

1. Login to your account at [github](https://github.com/login)
2. Navigate to the following url: http://github.com/intellisysmay2014 
3. Click on the prep repository: ![repository](http://github.com/intellisysmay2014/setup/raw/master/images/github_shawaugp.png)
4. Click on the fork button to create your own copy of this repository <br>![fork](http://github.com/intellisysmay2014/setup/raw/master/images/github_fork.png)
5. Repeat steps 2-5 for the app and prep repositories.

## Checkout your local copies of the code

1. Open up a git bash prompt and type the following commands:
    ```bash
    cd /c/course 
    git clone github:[your github user name]/prep.git
    git clone github:[your github user name]/app.git
    ```
    Assuming your github username is jp the commands would look as follows:

    ```bash
    git clone github:jp/prep.git
    git clone github:jp/app.git
    ```

2. Once you have completed cloning the repositories your course folder should look as follows:

![checked out directory](http://github.com/intellisysmay2014/setup/raw/master/images/checked_out_directory.png)

##Install Mingw

Open up a git bash prompt and type the following commands:

```bash
cd /c/course/setup
explorer .
```
Double click the mingw-get-inst-20111118.exe installer and install using the following screenshots:

![mingw_setup_part_1](http://github.com/intellisysmay2014/setup/raw/master/images/mingw_setup_part_1.png)
![mingw_setup_part_2](http://github.com/intellisysmay2014/setup/raw/master/images/mingw_setup_part_2.png)
![mingw_setup_part_3](http://github.com/intellisysmay2014/setup/raw/master/images/mingw_setup_part_3.png)
![mingw_setup_part_4](http://github.com/intellisysmay2014/setup/raw/master/images/mingw_setup_part_4.png)
![mingw_setup_part_5](http://github.com/intellisysmay2014/setup/raw/master/images/mingw_setup_part_5.png)

##Configuring MingW Paths

Open up a git bash prompt and type the following commands:

```bash
cd /c/course/setup
notepad dev_tools/mingw/profile
```

Change lines 20 and 23 so that the location of your ruby bin directory and git bin directory match up with where you installed the programs. I would strongly recommend using spaceless paths so that you won't have to fiddle around with escaping spaces. The default values of the lines are where I have installed those tools to.

Run the following command

```bash
./copy_mingw_config [enter]
```

The above step copies the modified config file into the folder where you should have installed mingw (c:\utils\mingw). 

##Test Your Mingw Install

Open up a git bash prompt and type the following commands:

```bash
ruby -v
```
You should see a ruby version, if you don't see anything, you will have to repeat the Configuring MingW Paths section above, and make corrections as necessary.

```bash
git --version
```
You should see a git version, if you don't see anything, you will have to repeat the Configuring MingW Paths section above, and make corrections as necessary.

##Install IIS Express 7.5

* If you already have a version of IIS Express installed (even if it is >= 7.5) please follow these steps.

Install iis_express following these steps:
  1. Download the installer from [here](http://www.microsoft.com/en-us/download/confirmation.aspx?id=1038)
  2. Run the IIS Express installer. 
  3. Copy (not cut) the entire folder C:\Program Files (x86)\IIS Express
  4. Paste the copied folder into your C:\utils folder.
  5. Rename the pasted IIS Express folder to iis_express.
  6. Rerun the IIS Express installer and remove the installed version of IIS Express. This will just leave your copied, registry-less version on the system.
  
##Install TestDriven .Net

* Download and install the latest student version of [TestDriven.Net](http://testdriven.net/download_release.aspx?LicenceType=Personal)
