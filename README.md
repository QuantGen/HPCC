# HPCC

## Prerequisites

- Familiarity with the Unix shell (command line)
    - Check iCER's [upcoming seminars and workshops](https://icer.msu.edu/upcoming-workshops) calendar for the next monthly "Introduction to Linux" workshop
- Familiarity with iCER's HPCC
    - Read iCER's [HPCC Documentation and User Manual](https://wiki.hpcc.msu.edu/display/hpccdocs/Documentation+and+User+Manual)
    - Check iCER's [upcoming seminars and workshops](https://icer.msu.edu/upcoming-workshops) calendar for the next monthly "Introduction to HPCC" workshop
    
## Getting Started

1. Get an HPCC account (requested by the PI)
2. Get added to the `quantgen` group
3. Check if you can access the `quantgen` research space:

        cd /mnt/research/quantgen

4. Use our shared configuration files:

        echo -e "\nsource /mnt/research/quantgen/tools/configfiles/bash/bashrc" >> ~/.bashrc &&
        echo -e "\nsource /mnt/research/quantgen/tools/configfiles/bash/bash_profile" >> ~/.bash_profile &&
        touch /mnt/research/quantgen/tools/configfiles/bash/subscribers/$USER

    Currently, these files
    - add our own modules to the HPCC module system
    - automatically load software commonly used in the lab (e.g., R, PLINK), and
    - make new files writable to the group to allow for better collaboration.

    To run R simply type `R`.
    To run PLINK simply type `plink`.

    For other installed software check the `module avail` output.

## Logging in without a Password

If you are tired of typing your password every time you connect to the HPCC you can use public key authentication instead. Public key authentication relies on two files, a public key (that is public in a way that you can give it to other people) and a private key (that is private in a way that you have to keep it to yourself).
These files can be generated with the `ssh-keygen` command on your computer: `ssh-keygen -t rsa -b 4096 -C nameofyourcomputer` where `nameofyourcomputer` is some nickname for your computer (`-C nameofyourcomputer` is optional, but helps if you have a lot of machines). Leave every prompy empty and simply enter through. You will now have two files called `id_rsa` and `id_rsa.pub` in your `~/.ssh` directory. `id_rsa` is your new private key and `id_rsa.pub` is your new public key. Open the public key file `id_rsa.pub` and copy the contents. Make sure you didn't copy the contents of the private key file `id_rsa`. Connect to the HPCC, and paste the public key into the `~/.ssh/authorized_keys` file on a new line. Disconnect, and you should now be able to reconnect without providing a password. Your password will instead be the private key file (`~/.ssh/id_rsa`), so make sure it is unavailable to other people. There is no problem if you lose the file (e.g., your computer breaks down) as you still have your NetID password as a backup and can simply create a new key to replace the old one (after removing the old entry in the `~/.ssh/authorized_keys` file).

## Plotting on the HPCC

To see plots on the HPCC you need to enable X11 forwarding. On a Mac, you need to install [XQuatz](https://www.xquartz.org/) and restart your computer to use this feature. X11 forwarding can be enabled by setting the `-X` in the `ssh` command: `ssh -X username@hpcc.msu.edu`. After you have connected that way, you should be able to see the plots. You will also be able to see PDF files with a program called evince: `evince file.pdf`.

Unfortunately, X11 forwarding is subject to a default timeout of 20 minutes after which it stops working. This is way to short for the tasks that we are typically doing. To increase the timeout, you need to create a config file in the `.ssh` folder in your home directory on your computer called `~/.ssh/config` that should contain the following information (replace `yourusername` with your username):

```
Host msu
    HostName hpcc.msu.edu
    User yourusername
    ForwardX11 yes
    ForwardX11Timeout 596h
```

A nice side effect of this configuration file is that from now on you can simply connect to the HPCC via `ssh msu` and get a connection with X11 forwarding with a timeout of 596 hours (i.e. almost 25 days).
