# Proxmox-ve
This builds a Proxmox VE 6.3 Vagrant basebox.

# Usage
If you want to troubleshoot the packer execution see the `.log` file that is created in the current directory.  
Create the basebox :  
`packer build proxmox-ve.json`  
After you create the basebox you can start an example environment with :  
`vagrant up`  
And access the Proxmox Web Interface at this [link](https://192.168.56.1:8006) with the default `root` user and password `vagrant`.

# Packer boot_command
As Proxmox does not have any way to be pre-seeded, this environment has to answer all the
installer questions through the packer `boot_command` interface. This is quite fragile, so
be aware when you change anything. The following table describes the current steps and
corresponding answers.

| step                              | boot_command                                          |
|----------------------------------:|-------------------------------------------------------|
| select "Intall Proxmox VE"        | `<enter>`                                             |
| wait for boot                     | `<wait10><wait10><wait10><wait10>`                    |
| OK for no KVM virt on VirtualBox  | `<enter><wait>`                                       |
| agree license                     | `<enter><wait>`                                       |
| target disk                       | `<enter><wait>`                                       |
| type country                      | `United States<wait><enter><wait><tab><wait>`         |
| timezone                          | `<tab><wait>`                                         |
| keyboard layout                   | `<tab><wait>`                                         |
| advance to the next button        | `<tab><wait>`                                         |
| advance to the next page          | `<enter><wait5>`                                      |
| password                          | `vagrant<tab><wait>`                                  |
| confirm password                  | `vagrant<tab><wait>`                                  |
| email                             | `pve@example.com<tab><wait>`                          |
| advance to the next button        | `<tab><wait>`                                         |
| advance to the next page          | `<enter><wait5>`                                      |
| hostname                          | `pve.example.com<tab><wait>`                          |
| ip address                        | `<tab><wait>`                                         |
| netmask                           | `<tab><wait>`                                         |
| gateway                           | `<tab><wait>`                                         |
| DNS server                        | `<tab><wait>`                                         |
| advance to the next button        | `<tab><wait>`                                         |
| advance to the next page          | `<enter><wait5>`                                      |
| install                           | `<enter><wait5>`                                      |
| wait 1m for install to finish     | `<wait10><wait10><wait10><wait10><wait10><wait10>`    |
| wait 1m for install to finish     | `<wait10><wait10><wait10><wait10><wait10><wait10>`    |
| wait 1m for install to finish     | `<wait10><wait10><wait10><wait10><wait10><wait10>`    |
| wait 1m for install to finish     | `<wait10><wait10><wait10><wait10><wait10><wait10>`    |
| reboot                            | `<enter>`                                             |

**NB** Do not change the keyboard layout. If you do, the email address will fail to be typed.

# Inspiration
https://github.com/sticky-note/proxmox-ve  
https://github.com/rgl/proxmox-ve
