Logging In
==========

- Part 1: Logging into the shell
  - Commands: bash, login, ssh
  - Connecting to a remote shell.  

There are many ways of accessing Linux. To start for educational purposes, I encourage you to take the path of "Other" below and use this from within your browser.

Go to **https://HostTheBox.com/** or **https://linux.farm/**

Linux
-----

- You're at the office and you've got a Linux workstation in front of you with a piece of paper with your username and password. You start up the computer, a bunch of text flows by and now you're looking at a prompt that says "`Username`." Now what?

In this case most likely you have a graphical interface in front of you and a box to enter text. Into the box labeled "`Username`" you'll enter the **username** provided and then hit `<ENTER>`. After that you'll be prompted for a *password* and again you'll enter the information provided and hit `<ENTER>`.

Once you hit `<ENTER>` the second time you should be logged in and presented with a user interface. I encourage you to click around and see what has been provided for you. In most of the graphical desktop environments there is an Applications menu that will either operate like the "Start" menu in Windows or pop up a "Search" box when you click on Applications. When you're ready to move on to the exercises into this box type "**Terminal**" and hit enter, a black box with a "`$`" prompt should appear.

macOS
-----

- You use a macOS for graphics editing, now you want to expand your portfolio to include websites. You got your first client and they provide you a hostname, user, and password and expect you to edit the website. How do you connect and login securely?

macOS is a cousin of Linux so you'll have many of the tools you need. Like the first login, you'll do the same. Then you'll go into Utilities and open Terminal. A black box with a "$" prompt should appear. Your client should have provided you `ssh` credentials which you'll enter as such:

From the shell prompt:

`$`: **ssh** *user*@*host*

`Password`: < ExampleSecret > `<ENTER>`

and another "`$`" prompt should appear.

Windows
-------

- You use a Windows system at the office and were put in charge of auditing the security of your Linux server farm before an audit comes due and you've never touched a Linux server before and first need to know how to login.

The fastest way to get Linux on a Windows system, is to install the Windows Subsystem for Linux or WSL. In order to do this in Windows 10 or later, open a Command Shell via "Run as Administrator" or PowerShell Window and run the command "wsl --install" and Ubuntu Linux will be installed into a virtual machine which you can run as the application "Ubuntu" after which you'll be at a graphical interface and can follow the instructions above.

Other
-----

- Finally, you're only passingly interested in Linux and don't want to spend much time learning it right now but would like to experience it. How can you do that?

Go to **https://HostTheBox.com/** or **https://linux.farm/**

Click on the starter Linux distribution and a black box will open and a "`$`" prompt should appear.

