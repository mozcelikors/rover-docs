.. toctree::
   :glob:

Rover Web UI: roverweb
#########################


.. image:: ../roverstatic/images/roverweb_logo.png
   :width: 40%
   :align: center
   :alt: ../roverstatic/images/roverweb_logo.png
   
   
*************************************************
What is roverweb?
*************************************************
**roverweb** is a Web-based user interface that includes not only powerful back-end communication infrastructure with roverapp, but also provides functionalities such as driving the rover, camera streaming, visualizing core utilization, displaying sensor information, and sensor calibration.

Roverweb is equipped with a powerful embedded back-end that is called `node.js <https://nodejs.org/en/>`_ and a main infrastructure library called `socket.io <https://socket.io/>`_. It makes use of the created javascript programs in order to create reactive web servers that communicate with websockets.


*************************************************
roverweb Infrastructure
*************************************************
Roverweb's communication infrastructure is given below:

.. image:: ../roverstatic/images/roverweb_infra.png
   :width: 100%
   :align: center
   :alt: ../roverstatic/images/roverweb_infra.png
   
*************************************************
roverweb Features
*************************************************


*************************************************
Downloading roverapp
*************************************************

.. note:: Rover-web source code is maintained under the following repositories:

          `https://github.com/app4mc-rover/rover-web <https://github.com/app4mc-rover/rover-web>`_


*************************************************
Getting started with roverweb
*************************************************

Installation
=================================================
.. note:: In order to see how roverapp is installed and compiled, please see :ref:`roverweb Installation <roverwebinstallation>` section.

.. _roverwebstart: 
Running the Application
=================================================
Before running the application, make sure that installation steps are successfully completed.
In order to run the server after installation, the following command must be executed from roverweb root:

.. code-block:: bash
   :linenos:

   node scripts/nodejs/start_roverweb.js

After reading from the console that HTTP server is running, the web interface could be accessed using ``http://192.168.168.1/roverweb.html``.
Before the web interface can be opened, it is important for one to connect to the network (using SSID/PSK) of the rover. 

For roverweb's operation, it is not necessary for roverapp to be running. However, full functions of roverweb could be benefited when roverapp is also running.
   
*************************************************
roverweb Complete Reference
*************************************************
Some Words on Infrastructure
=================================================

Ports
=================================================
roverweb uses several ports in the network stack in order to keep communication running. The allocated ports are given below:

* HTTP server: 5500
* Socket.IO server: 5502
* Roverweb TCP server end: 8502
* Roverweb TCP client end: 8501

Data Formats
=================================================
Four types of data is currently passed between roverapp and roverweb's reactive socket processes. Those data are all JSON formatted, concatenated with
end of file (EOF) string ``\r\n``.

* Sensor Data (from roverapp to roverweb), denoted by ``sensor``
* Core Utilization Data (from roverapp to roverweb), denoted by ``util``
* Rover Control Data (from roverweb to roverapp), denoted by ``control``
* Rover Speed Data (from roverweb to roverapp), denoted by ``speed``

Example data are shown below for each of the given data format types:

* Sensor Data
	Data is periodically sent from roverapp to roverweb.
	
	.. code-block:: python
	   :linenos:

		{
			"rover_dtype"   : "sensor",
			"data" :
			{
				"infrared0"   : 100.0, 
				"infrared1"   : 100.0, 
				"infrared2"   : 100.0, 
				"infrared3"   : 100.0, 
				"front"       : 20, 
				"rear"        : 15, 
				"temperature" : 22.0, 
				"humidity"    : 67.0, 
				"bearing"     : 47.0
			}
		}\r\n
		
* Utilization Data
	Data is periodically sent from roverapp to roverweb.
	
	.. code-block:: python
	   :linenos:

		{
			"rover_dtype"   : "util",
			"data" :
			{
				"core0"   : 100.0, 
				"core1"   : 100.0, 
				"core2"   : 100.0, 
				"core3"   : 100.0, 
			}
		}\r\n
		
* **Control Data**
	Data is asynchronously (upon user events) sent from roverweb to roverapp.
	
	.. code-block:: python
	   :linenos:

		{
			"rover_dtype"   : "control",
			"data" :
			{
				"command"   : "F",  
			}
		}\r\n
		
	``command`` entry can indicate many integrated functions, such as the ones listed below:

	* P -> Parking Mode Left
	* O -> Parking Mode Right
	* U -> Compass Calibration
	* M -> Adaptive Cruise Control Mode
	* X -> Manual Drive Mode
	* L -> Booth Mode - Demo1
	* N -> Booth Mode - Demo2
	* R -> Shutdown Hook
	* U -> Compass Calibration
	* F -> Stop Movement
	* Q -> Go Forward-Left
	* W -> Go Forward
	* E -> Go Forward-Right
	* A -> Go Backward-Left
	* S -> Go Backward
	* D -> Go Backward-Right
		
* Speed Data
	Data is asynchronously (upon user events) sent from roverweb to roverapp.
	
	.. code-block:: python
	   :linenos:

		{
			"rover_dtype"   : "speed",
			"data" :
			{
				"speed"   : 360, 
			}
		}\r\n