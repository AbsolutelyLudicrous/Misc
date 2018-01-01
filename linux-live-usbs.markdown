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

-

Other benefits to using a live Linux USB include:
 + [The normal benefits to using Linux](https://www.reddit.com/r/linuxmasterrace/wiki/why_linux).
 + Portability, a live USB can function as a "poor man's laptop".
   The author's first experiences with live USBs consisted of sticking MacOS on stick for use at school and home, so that they wouldn't have to deal with syncing stuff constantly.
 + System recovery, there are [dedicated distros](https://distrowatch.com/search.php?ostype=All&category=Data+Rescue&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&package=All&rolling=All&isosize=All&netinstall=All&language=All&defaultinit=All&status=Active#simple) for rescuing broken operating systems.
   It's always a good idea to have a rescue stick lying around.

---

> ## What do we cover?

0. Introduction to Linux, terminology

1. Choosing the right distro

2. Installing the distro

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


