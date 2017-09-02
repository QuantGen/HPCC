# HPCC

## Prerequisites

- Familiarity with the Unix shell (command line)
    - Check iCER's [upcoming seminars and workshops](https://icer.msu.edu/upcoming-workshops) calendar for the next monthly "Introduction to Linux" workshop
- Familiarity with iCER's HPCC
    - Read iCER's documentation and user manual: https://wiki.hpcc.msu.edu/display/hpccdocs/Documentation+and+User+Manual
    - Check iCER's [upcoming seminars and workshops](https://icer.msu.edu/upcoming-workshops) calendar for the next monthly "Introduction to HPCC" workshop
    
## Getting Started

1. Get an HPCC account (ideally requested by the PI): https://contact.icer.msu.edu/account
2. Get added to the `quantgen` group (requested by [@gdlc](https://github.com/gdlc) or [@agrueneberg](https://github.com/agrueneberg)): https://www.hpcc.msu.edu/contact
3. Check if you can access the `quantgen` research space:

        cd /mnt/research/quantgen

4. Use our shared configuration files:

        echo -e "\nsource /mnt/research/quantgen/tools/configfiles/bash/bashrc" >> ~/.bashrc
        echo -e "\nsource /mnt/research/quantgen/tools/configfiles/bash/bash_profile" >> ~/.bash_profile
        touch /mnt/research/quantgen/tools/configfiles/bash/subscribers/$USER 
