# Set up a LUKS+ZFS RAID-1+0 storage, and simulate failure and replacement

This is an automated environment to set up LUKS + ZFS RAID-1+0 tank.  Once that's configured you
can then simulate a failure.

For this to work it's neccessary to use the jessie-backports 4.9 kernel or stretch.

## Usage

0. Update `boostrap/config` to meet your needs, using `bootstrap/config.sample` as a basis.

1. Install dependencies

        host $ vagrant plugin install vagrant-vbguest

2. Bring up the instance

        host $ vagrant up

2. Connect to the instance 

        host $ vagrant ssh

4. Initialize the system.  This is interactive, so it's not auto provisioned.

        guest $ sudo /vagrant/booststrap/run
