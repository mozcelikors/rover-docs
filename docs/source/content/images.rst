.. toctree::
   :glob:

Ready Images
########################################

Raspbian Jessie Image
========================================

Download `Raspbian Jessie Image <https://owncloud.idial.institute/index.php/s/owZwZY7tdUxlEII>`_.

	* Includes dependencies and current rover-app and rover-web repositories
	* Updated: 01.11.2017
	
To install the latest roverapp:

.. code-block:: bash
   :linenos:

   cd ~/rover-app
   git pull
   git checkout master
   sudo ./install_roverapp.sh

To start roverapp:

.. code-block:: bash
   :linenos:

   cd ~/rover-app/build/bin
   sudo ./roverapp
   
To download latest roverweb:

.. code-block:: bash
   :linenos:

   cd ~/rover-web
   git pull
   git checkout master
   
To start roverweb:

.. code-block:: bash
   :linenos:

   cd ~/rover-web/scripts/nodejs
   sudo node start_roverweb.js
   
.. warning:: Be sure to change the folder to ``cd <your/roverweb/root/path>/scripts/nodejs/`` before executing the script, since it'll use default directory for hosting.
