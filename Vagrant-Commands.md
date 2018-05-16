# Vagrant Commands
##### Note: Commands should be executed where Vagrantfile is located.

## Initialize the Vagrant file with the O/S Specifications

    $ vagrant init --minimal wesmcclure/ubuntu1404-docker

## Start Vagrant VM

    $ vagrant up

## SSH into Vagrant VM

    $ vagrant ssh <box_name>

## List the Vagrant box that was initialized

    $ vagrant box list

## Status of Vagrant VMs

    $ vagrant status

## Share Vagrant VM via a temporary and unique url

    $ vagrant share

## Halt Vagrant VMs

    $ vagrant halt

## Destroy Vagrant VMs

    $ vagrant destroy -f consul-server

###### Note: The source code and the content of the data directory will remain unchanged. Only the VM instance will be destroyed.
######  To build the machine again, use the 'vagrant up' command. This command is useful if you want to save disk space.
###### Warning: this command will destroy your site databases. Backup them using `drush sql-dump > db.sql` for each site.

## Reconfigure the Vagrant VM after a source code change

    $ vagrant provision

## Reload the Vagrant VM. Useful when you need to change network or synced folder settings

    $ vagrant reload

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg3NzYxOTM5NV19
-->