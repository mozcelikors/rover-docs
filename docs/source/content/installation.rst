.. toctree::
   :glob:

Installation Instructions
#########################

.. _roverappinstallation: 
*************************************************
roverapp Installation
*************************************************

Requirements
=================================================


Manual Installation Instructions
=================================================

.. Fetch, Extract, Patch, Configure, Build, Install
.. *************************************************


Automated Installation Instructions
=================================================

.. _roverwebinstallation: 
*************************************************
roverweb Installation
*************************************************

Requirements
=================================================
The following are requirements for the roverweb:

* Build-time dependencies python-pip, build-essential, cmake, git
* Raspbian with Access Point (with IP 192.168.168.1)
* Python 2.7
* psutil Python module
* node.js with version 8.x or higher
* node.js modules: net, connect, server-static, http, socket.io
* mjpg-streamer-experimental
* curl

Manual Installation Instructions
=================================================

Installing build-time dependencies
*************************************************

The following are must-have build-time dependencies that are partially required by not only roverweb, but also many open-source packages.

.. code-block:: bash
   :linenos:

   sudo apt-get update
   sudo apt-get install build-essential cmake git curl

   
Installing Python 2.7
*************************************************

Raspberry Pi 3 comes with Python 2.7 installated. For other Linux distributions, it might be required to install:

.. code-block:: bash
   :linenos:

   sudo apt-get install python

   
Installing psutil
*************************************************

psutil is a performance tool library that is written in Python and that is able to provide information about GNU/Linux-based systems.
First, ``python-pip`` must be installed:

.. code-block:: bash
   :linenos:

   sudo apt-get install python-pip
   pip install psutil
   
If you already have psutil installed, you can upgrade it:

.. code-block:: bash
   :linenos:

   pip install psutil --upgrade
   
Installing node.js and its required modules
*************************************************

For roverweb to serve web-pages and handle communications, node.js is an important dependency. 
The following commands can be used to download and install node.js:

.. code-block:: bash
   :linenos:

   sudo apt-get update
   curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
   sudo apt install nodejs

At this point, if the following command does not result in any errors, that means that node is successfully installed:

.. code-block:: bash
   :linenos:

   node -v
   
There are also node.js modules which are required for roverweb. Those modules must be installed by running the following:

.. code-block:: bash
   :linenos:

   npm install net connect server-static http socket.io
   
   
Downloading (Fetching) roverweb
*************************************************

.. code-block:: bash
   :linenos:

   git clone https://github.com/app4mc-rover/rover-web.git
   

Automated Installation Instructions
=================================================

*************************************************
Cross-Compiling roverapp on Raspberry Pi
*************************************************