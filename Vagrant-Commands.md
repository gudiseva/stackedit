# Vagrant Commands
##### Note: Commands should be executed where Vagrantfile is located.

## Initialize the Vagrant file with the O/S Specifications

    $ vagrant init --minimal wesmcclure/ubuntu1404-docker

## Start Vagrant VM

    $ vagrant up

## SSH into Vagrant VM

    $ vagrant ssh <vm_name>

## List the Vagrant box that was initialized

    $ vagrant box list

## Status of Vagrant VMs

    $ vagrant status

## Status of all the Vagrant VMs

    $ vagrant global-status

## Resume a suspended Vagrant VM

    $ vagrant resume

## Halt Vagrant VMs

    $ vagrant halt

## Destroy Vagrant VMs

    $ vagrant destroy -f <vm_name>

###### Note: The source code and the content of the data directory will remain unchanged. Only the VM instance will be destroyed.
######  To build the machine again, use the 'vagrant up' command. This command is useful if you want to save disk space.
###### Warning: this command will destroy your site databases. Backup them using `drush sql-dump > db.sql` for each site.

## Reconfigure the Vagrant VM after a source code change

    $ vagrant provision

## Reload the Vagrant VM

    $ vagrant reload

###### Useful when you need to change network or synced folder settings
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYxNjM0NDAwOSwtMTY4NDk2MjA2Ml19
-->

## Install the Vagrant VBGuest

    $ vagrant plugin install vagrant-winnfsd
    $ vagrant plugin install vagrant-vbguest

## Install the Vagrant HostsUpdater

    $ vagrant plugin install vagrant-hostsupdater


## Tasklist / Taskkill

    C:\> tasklist /fi "status eq running"
    C:\> tasklist /fi "imagename eq VBoxSVC.exe"
    C:\> taskkill /F /IM VBoxSVC.exe


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQxNTUyODg3MSwtMjAxMDk4MTA2NiwxNj
UyMDkzODE0LDc3Njg0MzI1NV19
-->