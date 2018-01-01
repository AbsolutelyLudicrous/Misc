# Linux Live USBs for Dummies

### (No, seriously, it's pretty idiot proof)

---

> ## Why?

Because Reddit user [DJWalnut wanted an expanded guide covering Linux Live USBs, tor, and encrypted persistent storage](https://www.reddit.com/r/traaaaaaannnnnnnnnns/comments/7n8afa/when_your_transphobic_parents_overhear_your/ds0qobk/).

> ## No, I mean "Why should I use a Linux Live USB?"

Because your computer is under attack!

Maybe.

If your computer is threatened, then a live USB is the thing for you.
The use case that spawned this guide was a transgender man threatened by his parents;
 other use cases might include hiding from a hostile government,
 performing legally questionable actions on the internet,
 and needing to use otherwise compromised computers.

> That last one, what?

[Software keyloggers exist!](https://github.com/gsingh93/keylogger)
(Author interjection: how cool is it that there are open source keyloggers?
Stuff normally used by TLAs and spooky hackers is available to dissect and improve.
I love the FOSS community.)
If you're regularly using hardware that belongs to somebody else, or is publicly available (library computers),
 you should assume that they have keyloggers.
Most software keyloggers can be defeated by, you guessed it!, using a live Linux USB.

(The ones which can survive a reboot and a transition to Linux are super scary, probably just destroy the machine if you've got one of those.)

[Hardware keyloggers](https://www.amazon.com/Keyllama-4MB-USB-Value-Keylogger/dp/B004ZGXU48/) also exist, you can buy them cheaply.
These are easier to defend against, just check your USB ports when you go to plug in your live USB.

Other benefits to using a live Linux USB include:
 + [The normal benefits to using Linux](https://www.reddit.com/r/linuxmasterrace/wiki/why_linux).
 + Portability, a live USB can function as a "poor man's laptop".
   The author's first experiences with live USBs consisted of sticking MacOS on stick for use at school and home, so that they wouldn't have to deal with syncing stuff constantly.
 + System recovery, there are [dedicated distros](https://distrowatch.com/search.php?ostype=All&category=Data+Rescue&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&package=All&rolling=All&isosize=All&netinstall=All&language=All&defaultinit=All&status=Active#simple) for rescuing broken operating systems.
   It's always a good idea to have a rescue stick lying around.

---

> ## What do we cover?

0. Introduction to Linux, terminology

1. The inherent security of Live Linux USBs

2. Choosing the right distro

3. Installing the distro

Great, ready?

Let's get started!

---

## Introduction to Linux and Terminology

What is Linux?
Linux is a kernel, technically.
More commonly, you'll see Linux used a name for a family of operating systems.

An [operating system](https://en.wikipedia.org/wiki/Operating_system) is the thing which allows you to use your computer.
It's a bunch of software which all works together so that you can ~~watch porn~~ do productive computer things.
It provides *everything* except the hardware.
The two most common desktop operating systems are Windows and MacOS X.

Linux is not an operating system, it's a kernel\*.
A kernel is this little piece of software which allows the rest of the operating system to interact with the hardware.
Every operating system which uses the Linux kernel is called a GNU/Linux software distribution.
"GNU/Linux software distribution" is commonly shortened to just "distro".
For the purposes of this document, "Linux", "a Linux", and "distro" are all the same thing.

\*some people say that Linux is an operating system. These people are wrong, and should kindly direct their arguments to `/dev/null`.

Normally, a distro would be installed to a more permaneant storage medium.
You'd use it the same way you would use Windows or MacOS X.
We are not doing that, we are using what's called a "live USB".
Instead of installing a Linux on your computer's internal storage, we'll be installing it on a USB stick.
A live USB is just that, a USB stick you've put a fully functioning GNU/Linux software distribution on.
I'll also use the terms "live Linux", "live BSD", "stick", and "live stick" to refer to a live USB.

Linux distros aren't your only choice, another common family of operating systems is called "BSD".
BSD stands for Berkeley Software Distribution.
The BSD family traces its lineage all the way back to the version of original AT&T UNIX licensed to UC Berkeley.
Today, BSD is commonly used for computer servers and hobbyists;
nerds, basically.

Power users who aren't afraid of getting their hands dirty with the command line might consider using a BSD instead of a Linux.
Anybody who wants a pain-free computer experience should just use a Linux.

---

## The Inherent Security of Live Linux USBs

Simply put, there are two attack vectors for any computer,
software and hardware.

Live Linuxes cover both excellently.

Software-wise, Linux is hella secure.
A strong UNIX permissions ensures that viruses can't damage critical system files.
A low use rate means that, in total, only 39 viruses targetting Linux have ever been designed.
Different system architectures between distros mean that, what works on Ubuntu Linux probably will fail on Arch Linux; and vice-versa.

Hardware is tougher to secure.
Simply put, ***Phyiscal Access Is Root(Administrator) Access***.
The instant the enemy has access to your hardware, you are fucked.
Commonly-used programs can be swapped out for malicious versions, all kinds of viruses can be installed, storage mediums can be cloned, etc.
Traditional desktop workstations are vulnerable to hardware keyloggers, storage seizure, and just plain being moved.
Laptops can be seized and have their storage mediums cloned.

***There is no protection against a sufficiently motivated enemy with phyiscal access to your computer.***

This is where the live stick comes in;
protect against phyiscal threats by minimizing phyiscal access.
The enemy can not clone your disk, can not install viruses, can not pwn you, if the enemy can not access your computer.
Because the live stick effectively becomes your computer, you can easily minimize phyiscal access by keeping your stick secure.
It's easier to hide [one of these](https://images-na.ssl-images-amazon.com/images/I/61x9W1gGUIL._SL1000_.jpg) than it is to hide [one of these](https://www.cnet.com/products/alienware-18-gaming-laptops/review/).

---

## Choosing the Right GNU/Linux Software Distribution.

There's loads of distros.
[Distrowatch, a highly respected and used site documenting distros, tracks over 300](https://distrowatch.com/search.php?ostype=All&category=All&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&package=All&rolling=All&isosize=All&netinstall=All&language=All&defaultinit=All&status=Active#simple).
This is no cause for fear, this is part of the beauty of Linux: there's a distro for every use case.

I'll just list a few of the "best" operating systems for each use case:

**Under attack, being threatened, need maximum security from phyiscal threats:**

[Tails](https://distrowatch.com/table.php?distribution=tails).
Tails is for the Snowden in all of us.

Tails offers [the following features](https://tails.boum.org/about/index.en.html) with minimal set up:

 + All internet traffic goes through Tor.
   Yeah, Tor; you know, that super scary thing all the 1337 h4x0r drug dealers use?
   The Tor network is an encrypted series of computers which your traffic bounces through before getting to the actual internet.
   This has the effect of anonymising your location and concealing which websites you're visiting.
   A bit like a VPN, really.

 + The stick is encrypted.
   All your files are encrypted; if your live stick is stolen, the thiefs cannot read your files.

### *If phyiscal threats are your attack vector, Tails is the distro for you.*

**Protection from phyiscal threats, but not to the degree that Tails provides:**

Sometimes, the inherent security of a live stick is enough.
Your enemy isn't tech savvy enough to intercept your internet traffic or can't quite understand this whole computering thing.

Read: if you're trying to protect yourself from your parents.

In this situation, any old distro will do.

> Why not use Tails?

Tails kinda sucks for day-to-day usage.
Routing traffic through Tor is slow, plus power users may find it bloated at first.
Tails is very much designed for maximum phyiscal security, attempting to use it as a daily distro is suboptimal.

I recommend using [Solus Mate Edition](https://distrowatch.com/table.php?distribution=solus), but ultimately any distro will do.

Solus offers the following:

 + It offers encryption on install.
   You can encrypt your system on install.

 + It's rolling-release.
   Most operating systems are point-releases.
   You get a big update every few months.
   E.G., Windows 7, Windows 8, Windows 10 and MacOS X 10.6, MacOS X 10.7, ..., MacOS X 10.13.
   Solus is rolling.
   You do not have traditional major releases, all software is updated constantly.
   You will have access to the latest stable versions of the software you use.
   This generally makes for fewer security holes and bugs being patched faster.

 + It's relatively lightweight.
   Compared to some other "beginner" distros (\*cough\* \*cough\* Ubuntu!), Solus is downright slim.
   A fresh Solus install will run on under 10Gb of storage.
   A fresh Ubuntu install takes 25Gb.

 + It's idiot-resistant.
   Solus is easy to use, it features graphical tools for everything, it has a simple installation procedure, it can be used without ever touching a terminal.
   That being said, learners will enjoy how simple it is to "git gud" on it.

#### If you need just a basic live distro, with few additional security features, use Solus.

---

## Installing ~~gentoo~~ to USB

Installing Linux on a USB is pretty simple.

*As an aside, Tails provides a guide tailored to Tails.
If you chose to use Tails, you can follow it [here](https://tails.boum.org/install/index.en.html).*

### Here's what you'll need:

0. One *good* USB stick.
   This stick will be our Live Linux USB, this will contain the actual live system.
   "Good" means that the stick has a high read/write speed.
   A low read/write speed will cause your system to lag.
   When choosing a stick, check if it's USB 3 or USB 2.
   USB 3 is the most recent USB standard, and offers read/write speeds of over 150Mb/s.
   USB 2 is capped at 44Mb/s.
   The author highly recommends using [this](https://www.amazon.com/SanDisk-Ultra-SDCZ43-128G-GAM46-Newest-Version/dp/B01BGTG41W/) stick in particular,
   but any stick with more than 16Gb of storage will work.

1. Another USB stick.
   This stick can be garbage, it just needs more than 8Gb of storage.
   This stick will be used for the installer, it does not need to have good read/write speeds.

2. A computer.
   The computer must have two free USB ports and an unlocked BIOS.
   If the computer requires a password to access the BIOS, find a different computer.
   If you do not own a computer of your own, check your local library.

3. A USB Image writer.
   [Etcher](https://etcher.io/) provides a simple GUI for burning images to USB sticks.
   More advanced users running MacOS X, Linux, or BSD may want to look into using the `dd` command-line utility.

### Now you need to obtain the installer image

An installer image, often just called an "ISO" ("Eye-soh"), is a stripped down version of an operating system desgined to install a fully-functioning version of itself.
ISOs are so named because of their file extension, `.iso`, which is derive from the name of the ISO-9660 file system commonly used in ISOs.

Linux installers are usually named `nameOfDistro-versionNumber-architecture.iso`.
BSD installers' names vary, and usually end with `.img` or `.img.gz`.

To obtain the ISO, you'll usually need to go to your chosen distro's "Downloads" page.
Solus provides theirs [here](https://solus-project.com/download/), Tails provides theirs [here](https://tails.boum.org/install/download/index.en.html).

Other operating systems should have a big ol' "**Download**" button on their homepage.

*Many ISOs are distributed as torrents.
If possible, you should use your torrent client to obtain the ISO.
Not only is torrenting more secure than a direct download, it also takes a load off of your distro's file servers.*

**Checklist:**

At this point, you should have the following:

 + Two USB sticks

 + Etcher, or other image burning software

 + A file ending with `.iso` or `.img`.

Good?

### Burning the installer image

ISOs are useless on your computer, you have to "burn" them to a USB stick to actually use them.
To do that, perform the following:

0. Plug in your crappy USB stick, the one you're using for the installer.

1. Fire up Etcher

2. Click "Select image"

3. Navigate to the folder you downloaded the ISO to, usually `Downloads`

4. Double-click the ISO.
   Etcher may warn you that the image is invalid.
   If this is the case, choose a different distro.

5. Etcher will either autodetect the USB stick you want to burn to, if you only have one stick plugged in, or Etcher will offer a selection of sticks to burn to.
   If asked, choose your crappy USB stick as the destination.

6. Flash!
   You may be asked to enter your password, this is because interacting with external storage mediums is generally an action which requires root privelages.

7. Wait for the image to finish burning, Etcher will give you a notification when this happens.

8. Unplug the USB stick.

Congratulations, you now have an installer USB!

We can now move on to the actual installation.

### Installing the Live System

To use the installer, you'll need to boot to it.

0. Plug in both your installer USB stick and your "good" USB stick.

1. Close any applications you have open, save all your work, etc., because you need to reboot your computer to access the installer.

2. Boot to either your computer's "One-time boot" screen or to your BIOS/(U)EFI menu.
   This is usually done by holding down a certain key on your keyboard while booting.
   You can check this by Googling for your laptop, or checking your motherboard's specification.
   E.G.: "asus k501 bios key" or "asrock bios key".

*Stock Apple Macs don't have a BIOS, they have a boot screen which allows you to select a drive to boot to.
This can be accessed by holding down the "Alt" key when booting.
From the boot menu, you boot to your main MacOS X install, another operating system you may have installed, a "Recovery Volume" - a stripped down MacOS X designed for system recovery, and the USB stick you have plugged in.
Use the arrow keys or the mouse to select and boot to the USB stick.*

3. From the BIOS or boot menu, boot to your USB stick.

4. Perform the install normally, except instead of installing Linux to your computer's internal storage, install to your "good" USB.
   Installation instructions vary between distro, so I won't list them here.
   All major distros should have tutorials available online, if needed.

If extra help is needed, the author can provide distro-specific instructions.
Contact them through Telegram as @mdanne

Congratulations!
You should now have a bootable Live Linux USB!

To load the live Linux, repeat the steps you used to load the installer.
Once you get to the boot menu, boot to your "good" USB.

From there, enjoy your secure Linux operating system!
