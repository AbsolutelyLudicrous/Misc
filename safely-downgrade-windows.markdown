*(Author note:*

*Windows is shit.*
*Modern "user-friendly" Linuxes, such as Solus or Antergos, are heckin' easy to use.*

*You should use those, instead of an operating system which spies on you and takes control of ****your**** computer.)*

---

# So you want to downgrade Windows?

There's loads of reasons for wanting to do this.

Maybe you're mad about the forced """upgrade""" to Windows 10.

Maybe 10 is running too slowly on your computer.

Maybe you just liked 7 better.

Whatever, it doesn't matter.
If you want to super-safely install a previous version of Windows, this is the guide for you.

---

### What you'll need:

 + A storage medium capable of storing every file on your disk.
   If you have used only 50Gb of storage, you only need a 50Gb storage medium.
   This will commonly take the form of an external hard-drive, but an internal drive can be used if you have more than one.
   We'll call this disk "*cptarget*".

 + (Optional) A storage medium(s) with space greater than or equal to all of your current storage space.
   If you have more than one internal disk, you can split the mediums across multiple storage media, or you can stick the image of each individual disk on a single medium.
   This will be used to take a bit-for-bit clone of your disks.
   We'll call this disks "*ddtarget*(s)".

 + A Windows installer for your desired version.
   You can use the CD that came with your computer, or you can use less legal methods to obtain an installer.
   To make a Windows installer from Windows, you'll need Rufus and a Windows ISO.
   To make a Windows installer from MacOS X, **//TODO**.
   To make a Windows installer from a Linux, give up and cry.

 + A [Live Linux USB](https://github.com/AbsolutelyLudicrous/Misc/blob/master/linux-live-usbs.markdown).
   The Live Linux will act as a temporary environment from which we will perform the backup.

---

### General procedure:

#### (Scan this before folling the in-depth guide, make sure you have the resources to perform each step.)

0. Boot into the Live Linux.

1. `dd` the contents of every disk onto *ddtarget(s)*.

2. `cp` the contents of every disk onto *cptarget*.

3. Disconnect *ddtarget* and *cptarget*.

4. Boot into the Windows installer, perform the install.

5. Boot into the Live Linux.

6. Connect *cptarget*, copy over any missing files.

7. Boot the new Windows installation.

---

### More in-depth procedure:

#### (References the above outline.)

## `sudo su -`

We'll need to run a *lot* of commands as root.
To ensure that we don't have go typing `sudo` a whole bunch or risk having `sudo` time-out on us, just log in as root in most new terminals.

---

**0:**

To boot the live Linux, you'll need access to your computer's BIOS.
The key to access BIOS is commonly displayed on bootup.
If not, check Google for your motherboard's BIOS key.

From the BIOS, you should be able to select a boot medium.

The Live Linux should show up with the manufacturer's designation for your USB stick.

---

**1:**

**CAUTION:**

 + ***Do not*** mount the disks before `dd`ing.

 + ***Do*** mount *ddtarget*.

We'll need to discover which `/dev/sd` device our computer's disks and *ddtarget* got assigned to.
An easy way to do this is to open GParted and click the drop-down disk selector in the upper right.

Once you've discovered which `/dev/sd` device belongs to what, run the following:

    mkdir /mnt/ddtarget
    mount /dev/sdX /mnt/ddtarget #where sdX is the device ddtarget got assigned to

This will "mount" *ddtarget* at position `/mnt/ddtarget`.

Then ensure that we have some pre-existing files to act as images for our disks.
To do this, we'll `touch` those files.

    touch /mnt/ddtarget/hard-disk-0.img
    touch /mnt/ddtarget/hard-disk-1.img
    ...

for every disk on your computer.

`dd` is a UNIX utility for copying and formatting files.
We'll just be using it for the copying part.

The general form of this kind of `dd` is as follows:

    dd if=/path/to/input of=/path/to/output

Our specific `dd` will look like the following:

    dd if=/dev/sdX of=/mnt/ddtarget/hard-disk-#.img
    #where sdX is the device of our computer's disk, and hard-disk-#.img is the backup image file
    #make sure to replace sdX and disk-# with the appropriate letter and number!

**Be warned that this is going to take a *****long***** time!**

I recommend performing the `dd` overnight, or shortly before leaving for work.
The author can attest to gigantic `dd`s taking several hours, `dd`ing several terabytes of data over a USB 3 port can take over ten hours.

*Wanna make it faster?*

Of course you do!

Pop open a new terminal, run the following command:

    ps aux | grep -ie dd

This will list all currently running processes and search the list for our `dd`.
The first column should say "root", the second column is our `PID`, Process ID.

To increase the amount of resources available to `dd`, run the following:

    sudo renice -19 PID #where PID is the process ID you just discovered.

This gives the `dd` the second-highest priority available, second only to critical operating-system processes.

**Do not** give the `dd` a priority of -20.
-20 should *only* be used for OS-critical processes, such as the kernel integrity checker, or the kernel multithreading daemon.
Increasing the nice-level to -20 has a miniscule benefit, and can cause major harm to the Live Linux.
Most processes run at a nice-level of 0 or 19, the ones that don't are *really fucking important*.

---

**2:**

Imaging the system is great and all, but is better suited to backups than fiddling around with mounting disk images.
To alleviate this problem, we're going to use the UNIX `cp` (CoPy) command to make an easily-accessible copy of our disks.

This is different from `dd` in that our `dd` takes a snapshot of every individual bit on the disks, whereas `cp` copies files, including the contents of links on UNIX file systems.

**CAUTION:**

If your Windows install contains a set of recursive links, `tar` the filesystems first.
Windows makes it hard for you to create recursive links, only delve into the witchcraft that is `tar` if you're aware of any.
If you aren't sure, continue with these steps; we'll check for discrepencies in filesystem size a bit later.
