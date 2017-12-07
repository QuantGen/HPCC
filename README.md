# HPCC

## Prerequisites

- Familiarity with the Unix shell (command line)
    - Check iCER's [upcoming seminars and workshops](https://icer.msu.edu/upcoming-workshops) calendar for the next monthly "Introduction to Linux" workshop
- Familiarity with iCER's HPCC
    - Read iCER's [HPCC Documentation and User Manual](https://wiki.hpcc.msu.edu/display/hpccdocs/Documentation+and+User+Manual)
    - Check iCER's [upcoming seminars and workshops](https://icer.msu.edu/upcoming-workshops) calendar for the next monthly "Introduction to HPCC" workshop
    
## Getting Started

1. Get an HPCC account (ideally requested by the PI)
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
