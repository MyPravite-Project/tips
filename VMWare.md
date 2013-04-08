# Guide

* http://packages.vmware.com/tools/docs/manuals/osp-esx-41-install-guide.pdf
* http://www.vmware.com/download/packages.html
* https://help.ubuntu.com/community/VMware/Tools

# Bæta við lyklum:

http://packages.vmware.com/tools/keys/index.html

    sudo apt-key add http://packages.vmware.com/tools/keys/VMWARE-PACKAGING-GPG-DSA-KEY.pub
    sudo apt-key add http://packages.vmware.com/tools/keys/VMWARE-PACKAGING-GPG-RSA-KEY.pub

# Búa til source-lista

    sudo vim /etc/apt/sources.list.d/vmware-tools.list

## Setja inn:

    deb http://packages.vmware.com/tools/esx/4.1u1/ubuntu lucid main restricted

# Disablea multiverse

    sudo vim /etc/apt/sources.list

*Commenta út allar multiverse línur*

# Setja upp kernel dót

    sudo apt-get install vmware-open-vm-tools-kmod-server

# Setja upp Server Tools

    sudo apt-get install vmware-tools-nox

# Reboot
    
    sudo reboot

# Errors/failures

    Setting up vmware-open-vm-tools-common (8.3.7-0.381511) ...
       Checking acpi hot plug                                              done
    Starting VMware Tools services in the virtual machine:
       Switching to guest configuration:                                   done
       Guest memory manager:                                              failed
       VM communication interface:                                        failed
       VM communication interface socket family:                          failed
       Guest operating system daemon:                                      done
       Virtual Printing daemon:                                            done