# Application Note: GitHub Deployment Keys and Pulling Updates

At Leeman Geophysical we use git as our system of version control and GitHub as
our central repository of software and hardware development files. Version
control is a way to keep track of all changes to files with a history. We can
roll back to old versions, read comments of what changes were made, and more.
Version control is a clean way to keep track of changes on the many projects we
manage without the dreaded “sept_2_works_morning_use_this_one” file names that
are all too common. While there is a significant learning curve to use git, the
good news is you don’t need to worry about more than a few simple commands.

Our team uses what are called “deploy keys” that mean your computer can receive
updates from our repository (only when you tell it to). The deployment key does
not give us access to your computer, remote control capabilities, or the ability
to see any files. It is simply a way for us to grant that computer access to
read files from our repository and all actions are initiated by you.

Before you can get a copy of the repository or pull any new changes, we need to
add your system to our list of authorized users for your project’s repository.
Authentication is done with SSH keys. They are fast to generate if you follow
the following steps.

## Verify git is Installed
First, we need to make sure git is installed on your system.

### Linux In all likelihood git is already on your system,
but it is easy to check. Open a command prompt or terminal window and run

*git --version*

to see if a version comes back or if the command is not recognized.

If you need to install git, generally the best way is through your
distribution’s package manager. this would be dnf for Fedora, RHEL, CentOS, or
other RPM based distributions or apt for Debian based distributions like Ubuntu.

*sudo dnf install git-all*

*sudo apt install git-all*

There are also more installation options available at :
[https://git-scm.com/download/linux](https://git-scm.com/download/linux)

### Mac
Open a command prompt or terminal window and run

*git --version*

to see if a version comes back or if the command is not recognized. On Mavericks
(10.9) and above trying to run git from the terminal will prompt you to install
Xcode command line tools automatically. This is the recommended installation
method.

The most up to date git versions have installers available at
[https://git-scm.com/download/mac](https://git-scm.com/download/mac) as well. 

### Windows

Unless you have used git on your Windows system before, it is unlikely that it
is installed. Open Windows Power Shell and run

*git --version*

to see if a version comes back or if the command is not recognized. If git is
not installed, go to
[https://git-scm.com/download/win](https://git-scm.com/download/win) and
download the installer and run it.

## Check for Existing Keys
If your system already had git or has had prior SSH activities performed on it,
you may already have a key created. From a terminal (power shell on Windows) try
running the command

*cat ~/.ssh/id_rsa.pub*

and see if the file exists. If it does not, proceed to the next step to create a
key. If it already exists, proceed to the share the key with us.

## Create a Key
Now that we know you have git and don’t have a key generated, we’ll create one
by running a few commands in the terminal (power shell). The first command will
generate the key:

*ssh-keygen -t rsa -b 4096 -C "your_email@example.com"*

If you don’t want to use a real email here, that’s okay. We often use fakes that
help us remember what machine this is. For example triax3@midvale.edu or similar.
Just make it something sensible.

The system will prompt you about where the key should be saved, just press enter
to accept the default. Press enter to set the passphrase and empty and confirm
that. You’ve made a new key!

## Share Your Key
Your key consists of a public and private pair. Never share your private key
anywhere! We do need to know your public key though. Run the command

*cat ~/.ssh/id_rsa.pub*

and send us the output of it (starts with ssh-rsa). Once you
do, we’ll add it to the repository and you’re ready to get your local copy of
the files. 

## Clone the Repository
Once we’ve added your key to the list of authorized users, we’ll send you a link
to the repository that has your files. It looks something like 

*git@github.com:LeemanGeophysicalLLC/YOURPROJECT.git*

Open a terminal (Power Shell) and use the cd command to change to a directory
where you want to put the files. Your home folder is a good option on Mac/Linux
and on Windows we recommend the Documents folder. So, for example cd Documents
would change your prompt to be working in that directory.

Next, clone (copy) the files by running the command

*git clone git@github.com:LeemanGeophysicalLLC/YOURPROJECT.git*

and now you have a copy of the repository on your computer!

## Getting Updates
If we tell you that there are updates ready for you to pull down, you’ll need to
run the command

*git pull*

which should complete successfully and will copy the newest files from the
repository to your computer. Make sure you have changed directory into the
repository before doing this or the command will fail. If you see a message
about files that will be overwritten, it means that some files on your system
have changed since the repository was updated and git isn’t sure which ones you
want. It’s a good idea to contact us here for help. If you know that those files
aren’t critical or have changes you made that you don’t need, you can run git
stash followed by git pull to hide your local changes and bring down the most
recent version.


## Important Note!
If you have made changes to files locally we have no way of knowing! Please tell
us before we do ANY work to update your files so we can work with you to get a
copy of your changes before we do our work. If you don’t, this can result in
lost time, duplicated work, and other issues that cause delays for all of us.
Not sure if you’ve changed anything? Run the command git status while inside the
repository directory and send us the output - we’re happy to check with you!
