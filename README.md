# The Eudylpta Challenge
> I'm working on the linux kernel's secret-ish eudlypta challenge and while you can't post any actual code I figured
it would behoove me to post different things I found helpful for setup, configuration, reference, etc. 

- ##Configure your computer (I'm on fedora)
  - ###Install VirtualBox (This article was a godsend)
    - http://www.if-not-true-then-false.com/2010/install-virtualbox-with-yum-on-fedora-centos-red-hat-rhel/?PageSpeed=noscript
  - ###Install Vagrant (download provided, the rest is in your capable hands)
    - http://www.vagrantup.com/downloads
  - ###Getting Ubuntu set up for kernel development
    - Use this vagrant box
      - https://vagrantcloud.com/ubuntu/boxes/trusty32
    - Configure the VM
      - http://buttle.anu.edu.au/mediawiki/index.php/How_to_set_up_Kernel_Development_in_Virtual_Box
  - ###Notes on style
    - http://kernelnewbies.org/FirstKernelPatch
- ##Making a small kernel module
  - ###The End All Be All Kernel Documentation
    - https://www.kernel.org/doc/Documentation/HOWTO
  - ###Building External Modules
    - http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/Documentation/kbuild/modules.txt
  - ###Writing a Simple Kernel Module
    - http://www.thegeekstuff.com/2013/07/write-linux-kernel-module/

