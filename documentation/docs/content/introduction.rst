============
Introduction
============

In this documentation, you can learn everything you need to use and master the TYPO3 Docker Boilerplate.
We use various technologies such as Docker and Ansible which we may reference to, if required.

-----------------------------------------
What is the TYPO3 Docker Boilerplate for?
-----------------------------------------

The TYPO3 Docker Boilerplate is a convenient way to setup fully working environments for TYPO3 Projects.

When working with TYPO3 you may have to repeatedly setup your working environments. When working with many different
systems, you may come across different environments. This can be a tricky task to handle, especially in development
where you should simulate the productive system.

One approach to tackle this problem is to setup a whole environment for each project. This can be done with Virtual
Machines, that can be built using automated scripts such as Vagrant and Ansible.
However with the increasing number ob projects, switch times and the space required increases dramaticaly.

This is where Docker comes into play! Other than a Virtual Machine, Docker allows you to use the current linux kernel
to simulate another linux distribution. This is a low profile approach and doesnt require as much ressources as a
Virtual Machine, because the ressources are reused.

The TYPO3 Docker Boilerplate is using Docker with Docker-Compose to provice a set of containers that simulate
complete environments. You can add containers like Solr on demand, with the Version you require or even switch linux
distributions and php versions within minutes.
