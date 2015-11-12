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
- This process can be fairly complicated depending on your arch ( and simply because VMs are complicated). Check out [these instructions](http://tott-meetup.readthedocs.org/en/latest/setup.html) if you need more help.
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

### The End All Be All Kernel Documentation
- [Kernel Docs](https://www.kernel.org/doc/Documentation/HOWTO)


## Making a small kernel module

### A book on kernel modules
- Some very highly [recommended reading](http://www.tldp.org/LDP/lkmpg/2.6/html/c38.html) on a really great site.

### Building External Modules
- [Direction straight from the man!](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/Documentation/kbuild/modules.txt)

### Writing a Simple Kernel Module
- [directions for code and makefile](http://www.thegeekstuff.com/2013/07/write-linux-kernel-module/)
- Debugging and printing messages kernel style is [important](http://tuxthink.blogspot.com/2012/07/printk-and-console-log-level.html).


## Working with the linux kernel

### Using Git on the linux kernel source
- [This](http://www.landley.net/writing/git-bisect-howto.html) is an excellent how-to that will help you navigate the gritty gitty core of torvald's kernel.
- [This](http://kernelnewbies.org/KernelBuild) is a guide to building your own linux kernel from the source.
- [This](http://free-electrons.com/doc/books/lkn.pdf) is a book about customizing and building a kernel... Probably the best resource.

### Compiling a kernel
- Compiling a kernel is a pain if you don't have enough resources (because you decided to not allocate much to your VM) I recommend using distcc to compile on any spare computers you may or may not have lying around.
  help you compile.
