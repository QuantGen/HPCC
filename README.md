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
