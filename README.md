Automated Desktop Setup for Vision with ROS
===========================================
Original: https://github.com/lesmyrmidons/ansible-desktop-ubuntu

Modified by Emanuele Ruffaldi for ROS and CUDA

Requirements
-----------

    * curl,
    * git,
    * git-core.

Run
---

If you want to change anything :

```shell
$ curl -L https://github.com/eruffaldi/ansible-desktop-ubuntu/install.sh | sh
```

And enter your password.

Default installation
--------------------

This project will install the following packages:

    * bash-completion
    * openssh-server
    * vim
    * git, git-core, git-flow, git-email, git-extras, git-svn
    * zsh
    * curl
    * wget
    * htop
    * terminator
    * unzip, tar, gzip, bzip2
    * Java 1.7.x (Oracle)
    * Virtualbox (Oracle)
    * MongoDB
    * Drivers NVIDIA
    * Drivers CUDA
    * nodejs
    * Latex, texmaker
    * ROS Indigo

Custom installation
-------------------

if you want to customize the installation to suit your needs, you have to clone this repository :

    $ git clone https://github.com/eruffaldi/ansible-desktop-ubuntu.git

And you have to edit the file `site.yml` and comment line the list roles. For example :

```yml
##
# Ansible playbook for setting up a LAMP development server on Ubuntu 14.04.
#

---
- hosts: local
  user: lesmyrmidons
  sudo: yes

  vars_files:
    - group_vars/all.yml

  roles:
    - common    # List of essential packages
    - vim       # Configuration for vim
    - pinta     # Gimp little
    - latex     # Latex and ide texmaker
    - nvidia    # Drivers owner
    - adst      # Application for series https://github.com/lesmyrmidons/AdstSF2
#    - hhvm
    - web
#    - mongodb
#    - composer
    - nodejs
    - dotfile   # My dotfile (config : git, zsh, bash, tig, ...)
    - gnome-shell
```

Install Ansible :

    $ sudo apt-get install -y -qq python python-pip
    $ sudo pip install ansible

And execute command :

    $ ansible-playbook -i hosts site.yml -c local -K

You can also contribute to add new roles or improve existing.

License
-------

MIT / BSD