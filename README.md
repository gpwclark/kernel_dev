# The Eudyptula Challenge
> I'm working on the linux kernel's secret-ish [eudlypta challenge](http://eudyptula-challenge.org/) and while you can't post any actual code, I figured it would behoove me to post different things I found helpful for setup, configuration, reference, etc. 


## Configure your computer (I'm on fedora)

### Install VirtualBox (This article was a godsend)
- You never know what stupid things you could do to your own kernel, so use a VM. 
- [Install VBox on fedora](http://www.if-not-true-then-false.com/2010/install-virtualbox-with-yum-on-fedora-centos-red-hat-rhel/)

### Install Vagrant, download provided, the rest is in your capable hands
- Vagrant makes it painfully easy to set up a virtual box with command line access...
- [Vagrant download](http://www.vagrantup.com/downloads)

### Alt Instructions for VBox and Vagrant
- This process can be fairly complicated depending on your OS. Check out [these instructions](http://tott-meetup.readthedocs.org/en/latest/setup.html) if you need more help.
- As a sidenote, occasionally it may be the case that your actual hardware is not set up to enable virtualization. As a last ditch attempt (I had to do this) check the specs for you computer/manufacturer to figure out how to boot into the BIOS and make sure that virtualization is enabled. I have a Lenvo: [how to enable virtualization in BIOS on lenovo](http://amiduos.com/support/knowledge-base/article/enabling-virtualization-in-lenovo-systems)

### Getting Ubuntu set up for kernel development
- [Use this vagrant box](https://vagrantcloud.com/ubuntu/boxes/trusty32)... although the thing you really need from the link is this one-liner:

```
vagrant init ubuntu/trusty32; vagrant up --provider virtualbox
```

- Once you get the vagrant box initialized you just need to run 
```
vagrant ssh
```
- Vagrant is pretty cool (while linux containers are waaaay cooler, containers don't get their own kernel), so if you want to do more with the box I recommend going [here](http://tott-meetup.readthedocs.org/en/latest/sessions/vagrant.html), playing around with some exercises and reading some of the links.
- This is the part that I know much less about, but I found [this link](http://buttle.anu.edu.au/mediawiki/index.php/How_to_set_up_Kernel_Development_in_Virtual_Box) pointed me to some packages I needed.

### Notes on style
- [First Kernel Patch](http://kernelnewbies.org/FirstKernelPatch)
- The [linux kernel coding style](https://www.kernel.org/doc/Documentation/CodingStyle) guide-- an absolute must read.
- When in doubt default to [this](https://hassanolity.files.wordpress.com/2013/11/the_c_programming_language_2.pdf) book. This is the 2nd edition to *The C Programming Language* by Kernighan and Ritchie. Linux calls it K&R in the codying style docs. 

### The End All Be All Kernel Documentation
- [Kernel Docs](https://www.kernel.org/doc/Documentation/HOWTO)


## Making a small kernel module

### A book on kernel modules
- Some very highly [recommended reading](http://www.tldp.org/LDP/lkmpg/2.6/html/c38.html) on a really great site.

### Building External Modules
- [Direction straight from the man!](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/Documentation/kbuild/modules.txt)

### Writing a Simple Kernel Module
- [directions for code and makefile](http://www.thegeekstuff.com/2013/07/write-linux-kernel-module/)
- Debugging and printing messages kernel style is [important](http://elinux.org/Debugging_by_printing#Log_Levels).
  - Keep in mind with kernel printing you can use the printk functions with an appropriate log level, however, when you run the checkpatch.pl script it will yell ("warn") at you to use the alias functions, e.g.

```
printk(KERN_DEBUG "I am a debug message");
/* versus */
pr_debug("I am a better debug message");
```

## Working with the linux kernel

### Efficiently searching the source
- Searching the source code can be invaluabe when looking for a solution. Using ctags or cscope can greatly assist you here.
- [cscope](http://cscope.sourceforge.net/large_projects.html) makes a database of the source code that you can use to quickly search.
- [ctags](https://tejparkash.wordpress.com/2011/03/07/ctags-with-linux-source/) are also a useful tool for jumping around source code.

### Using Git on the linux kernel source
- [This](http://www.landley.net/writing/git-bisect-howto.html) is an excellent how-to that will help you navigate the gritty gitty core of torvald's kernel.

### Compiling a kernel
- [This](http://kernelnewbies.org/KernelBuild) is a guide to building your own linux kernel from the source.
- [This](http://free-electrons.com/doc/books/lkn.pdf) is a book about customizing and building a kernel... Probably the best resource. Keep in mind it is for the 2.6 kernel so some of the information may be a little dated.
- I ended up compiling and running my kernel natively. Fedora uses grub2 which can be a moderate headache. I highly recommend using the program "grub-customizer" if you need to edit your configuration after you have installed the kernel.


### Documentation?
- Obviously there is kernel documentation and you should build it so you can have access to the fabled man 9 pages.

```
// In the kernel source directory run (make sure you have xmlto installed):
$ make mandocs
# make installmandocs
// Now you can run:
man 9 printk
```

## Making a kernel module for USB
- For background [chapter 14](http://www.makelinux.net/ldd3/chp-14) of linux device drivers is a must read.
- Although [this](http://www.linuxjournal.com/article/7353) article is a little outdated. This how-to demonstrates much of what needs to be done.
- [This](https://www.kernel.org/doc/Documentation/usb/hotplug.txt) kernel documentation is more up to date and should be read to see necessary changes from the greg kh linux journal article above.
- [This](http://lxr.free-electrons.com/source/drivers/hid/usbhid/usbkbd.c) is a sample driver for a usb keyboard.
