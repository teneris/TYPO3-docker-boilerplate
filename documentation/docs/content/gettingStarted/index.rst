===============
Getting Started
===============

In this section you will learn everything you need to get the TYPO3 Docker Boilerplate up and running.
We only cover the basics here, for more customization and configurations, you can visit the `usage <http://webdevops-documentation.readthedocs.io/en/latest/>`_ section of this
documentation.

------------
Requirements
------------

To run our TYPO3 Docker Boilerplate you need to meet the following requirements:

- Linux with a minimum Kernel Version of 3.10
- Docker Installed (`Docker Documentation <https://docs.docker.com/engine/installation/>`_)
- Docker Compose Installed (`Docker Compose Documentation <https://docs.docker.com/compose/install/>`_)

Optional but recommended are:

- Make (you test that with the command "make --version")
- Git (for cloning our repositories)
- WebDevOps CliTools (usefull tools when working with the boilerplate)

------------
Installation
------------

Open uo your Linux Terminal and navigate to your desired project location like this:

.. code-block:: bash
    :linenos:

    # Example for navigating to your project directory
    cd /home/<myUser>/projects

Clone our TYPO3 Docker Boilerplate repository from GitHub and navigate to your Project.
You may change "typo3demo" to any project name of your choice.

.. code-block:: bash
    :linenos:

    # Using git to clone the WebDevOps TYPO3 Docker Boilerplate
    git clone --recursive https://github.com/webdevops/TYPO3-docker-boilerplate.git typo3demo
    cd typo3demo

Enabling the development version of the configuration file:

.. code-block:: bash
    :linenos:

    # Enabling the Development Configuration via symlink
    ln -s docker-compose.development.yml docker-compose.yml
    # alternative to symlink
    cp docker-compose.development.yml docker-compose.yml

.. Hint:: You may want to edit docker-compose.yml now, if you want to enable features like Solr. To archive this, simply uncommend the service in the top list of services and the corresponding configuration bellow. Further Informations can be found in our Documentation.

.. Hint::  You also may change the target ports in the docker-compose.yml. But you should be aware to avoid port conflicts on your host system. A conflict will result in the container throwing an error and shutting down.

Navigate to the typo3demo/etc directory and adjust the environment.yml according to your project needs.

.. code-block:: bash
    :linenos:

    # Adjust your Environment Configuration to your needs.
    cd etc
    # You can choose any editor you want!
    vi environment.yml

    # Example configuration for this guide, we only change a couple of lines
    WEB_DOCUMENT_ROOT=/app
    WEB_DOCUMENT_INDEX=index.php
    CLI_SCRIPT=php /app/typo3/cli_dispatch.phpsh

Now we can add out TYPO3 files:

.. Hint::  For this Guide we will use a TYPO3 installation method, close to the one recommendet by the TYPO3 association. However you can use any structure you want, as long as you tell the correct document root and index.php in the environment.yml.

.. code-block::
    :linenos:

    # First move back to your Project directory (if you havent already)
    cd ..
    # Move to your app directory (this is the document root for your project files
    cd app

    # Getting the TYPO3 Core
    wget get.typo3.org/current --content-disposition
    # Extracting the core -- please adjust the version number to match the downloaded file!!!
    tar xzf typo3_src-7.6.x.tar.gz
    # Creating Symlink -- please match the number to match the TYPO3 core directory!!!
    ln -s typo3_src-7.6.x typo3_src
    ln -s typo3_src/index.php
    ln -s typo3_src/typo3

Now we navigate back to the project directory (where the file docker-compose.yml resides) and start our Docker Containers for the first time.

.. code-block:: bash
    :linenos:

    # First move back to your Project directory (if you havent already)
    cd ..
    # Starting the Containers
    docker-compose up

You should now see a lot of output, because the TYPO3 Docker Boilerplate is downloading images and provisioning your Project. Downloading the Images will only happen, if the required Docker image is not present on your system. When the containers are fully loaded, you should see some messages like this:

.. code-block:: bash
    :linenos:

    app_1     | [Sat Mar 12 15:39:34.126340 2016] [core:notice] [pid 716:tid 140649827633024] AH00094: Command line: 'apache2 -D FOREGROUND -D APACHE_LOCK_DIR'
    app_1     | 2016-03-12 15:39:35,128 INFO success: syslogd entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
    app_1     | 2016-03-12 15:39:35,128 INFO success: syslog-log entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)

-----
Usage
-----

