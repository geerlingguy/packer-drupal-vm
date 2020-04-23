# Packer Build - Drupal VM

**Current Ubuntu Version Used**: 18.04.4

Download from Vagrant Cloud: [`geerlingguy/drupal-vm`](https://app.vagrantup.com/geerlingguy/boxes/drupal-vm).

This example build configuration installs and configures a default Drupal VM installation on Ubuntu using Ansible, and then generates a Vagrant box file for VirtualBox, and uploads it to Vagrant Cloud: [`geerlingguy/drupal-vm`](https://app.vagrantup.com/geerlingguy/boxes/drupal-vm).

See related project [`packer-ubuntu-1804`](https://github.com/geerlingguy/packer-ubuntu-1804), and minimal base box [`geerlingguy/ubuntu1804`](https://vagrantcloud.com/geerlingguy/boxes/ubuntu1804).

## Requirements

The following software must be installed/present on your local machine before you can use Packer to build the Vagrant box file:

  - [Packer](http://www.packer.io/)
  - [Vagrant](http://vagrantup.com/)
  - [VirtualBox](https://www.virtualbox.org/) (if you want to build the VirtualBox box)
  - [Ansible](http://docs.ansible.com/intro_installation.html)

## Usage

Make sure all the required software (listed above) is installed, then cd to the directory containing this README.md file, and run:

    $ git clone git@github.com:geerlingguy/drupal-vm.git
    $ packer build -var 'version=2.0.9' drupal-vm.json

After a few minutes, Packer should tell you the box was generated successfully, and the box was uploaded to Vagrant Cloud.

> **Note**: This configuration includes a post-processor that pushes the built box to Vagrant Cloud (which requires a `VAGRANT_CLOUD_TOKEN` environment variable to be set); remove the `vagrant-cloud` post-processor from the Packer template to build the box locally and not push it to Vagrant Cloud. You don't need to specify a `version` variable either, if not using the `vagrant-cloud` post-processor.

## Testing built boxes

There's an included Vagrantfile that allows quick testing of the built Vagrant boxes. From this same directory, run the following command after building the box:

    $ vagrant up

## License

MIT license.

## Author Information

Created in 2018 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
