
Hey Everyone! The link I originally recommended for upgrading from Python 2.7 to 3.6 was good and ***here it is, but I thought I would expand this topic a little bit so no one gets hung up on this.

Also, I found that my Python 2.7 was insufficient to run Django 2.0 because it requires Python 3.4+ so I thought now would be a good time to give a little more detail about this. So here we go!

## How do I know what version of Python I’m using?

In your terminal, run the command ‘python –version’ and it will tell you what version you are using.

If that doesn’t work

Try ‘python2 –version’ or ‘python3 –version’  because sometimes your python command can be named those as well
If none of those work, you have NO Python installed.

## What do I do if I don’t have any Python installed?

Yay! Just skip to the 2nd step in Option 3, download and use the installer from the link, and go merrily on your way! If you want to use Python 2 later, you can learn about Option 1 to create another anaconda environment for Python 2 that you can use form time to time.

## What’s the SMART way to do this?

I started with options 1 and 2 and then 3, ultimately deciding that option 3 is the best way to go (at least for me) because I want to program primarily in Python 3 and I want to just type ‘python’ and get there; I want it to be my default environment. If I want to program in Python 2 I can always use Option 1 to get started with Python 2 for a limited time. If you want to do a Python 2 session in your terminal, then you have to get into that environment each session, but it’s only one command away. Also, with Anaconda, you can have many many different versions if you want and that’s why I’m choosing option 1 as my backup for Python 2, while using option 3 to set up my primary coding environment in Python 3.6

## (Option 1) Get Python 3.6 with Anaconda

‘conda search python’
‘conda create -n py36 python=3.6 anaconda’
‘source activate py36’
This will get you to a spot like this so you have (py36) prepended onto your command line.

That prepended thing isn’t my favorite because it makes my CLI cursor really long. What other options do we have?

## (Option 2) Get Python 3.6 with an Installer

Go to Python’s website and get an installer appropriate for your operating system. I picked the ‘macOS 64Bit Installer’.
Go through the installation process like normal. There aren’t any significant options to choose through, so just keep clicking ‘next’.
After it’s done installing, use the command ‘python3’ to use Python 3.6.
(You can still use ‘python’ to use Python 2.7.)

## (Option 3) Uninstall Anaconda 2 and Install Anaconda 3

Uninstall your current Anaconda 2 installation in the way that is normal for your operating system
Windows: Windows Key > Add / Remove Programs… > Anaconda 2 > Uninstall (I assume. I’m preferentially a Mac guy, but I generally know my way around Windows)
macOS: Use Finder to find the ‘anaconda2’ folder at one of the following locations and drag it to the Trash
Macintosh HD > Users > -yourname- > anaconda2
Macintosh HD > anaconda2
Then download the installation package appropriate for your operating system at this link (Choosing Python 3.6 version)
When the download finishes, start the installer and install it in the default place. That’s it!
You are done! You will find that using the command ‘python’ in your terminal will bring an interactive Python environment just like you want it to and the command ‘python –version’






