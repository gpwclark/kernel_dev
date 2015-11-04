# The Eudylpta Challenge
> I'm working on the linux kernel's secret-ish eudlypta challenge and while you can't post any actual code I figured
it would behoove me to post different things I found helpful for setup, configuration, reference, etc. 


## Configure your computer (I'm on fedora)

### Install VirtualBox (This article was a godsend)
- You never know what stupid things you could do to your own kernel, so use a VM. 
- [Install VBox on fedora](http://www.if-not-true-then-false.com/2010/install-virtualbox-with-yum-on-fedora-centos-red-hat-rhel/?PageSpeed=noscript)

### Install Vagrant, download provided, the rest is in your capable hands
- vagrant makes it painfully easy to set up a virtual box with command line access...
- [Vagrant download](http://www.vagrantup.com/downloads)

### Getting Ubuntu set up for kernel development
- Once you get vagrant installed you just need to run 
  ```
  vagrant up
  vagrant ssh
  ```
- [Use this vagrant box](https://vagrantcloud.com/ubuntu/boxes/trusty32)
- [Configure the VM](http://buttle.anu.edu.au/mediawiki/index.php/How_to_set_up_Kernel_Development_in_Virtual_Box)

### Notes on style
- [First Kernel Patch](http://kernelnewbies.org/FirstKernelPatch)


## Making a small kernel module

### The End All Be All Kernel Documentation
- [Kernel Docs](https://www.kernel.org/doc/Documentation/HOWTO)

### Building External Modules
- [Direction straight from the man!](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/Documentation/kbuild/modules.txt)

### Writing a Simple Kernel Module
- [directions for code and makefile](http://www.thegeekstuff.com/2013/07/write-linux-kernel-module/)
