.. toctree::
   :glob:

Rover Software: roverapp
#########################

.. image:: ../roverstatic/images/roverapp_logo.png
   :width: 40%
   :align: center
   :alt: ../roverstatic/images/roverapp_logo.png
   
   
*************************************************
What is roverapp?
*************************************************

**Roverapp** is an open-source C/C++ project for single board Linux computers (Raspberry Pi), especially designed for **rover**.
It features multi-threaded schedulable and traceable software under GNU/Linux environment. For multi-threading, POSIX threads (Pthreads)
and its synchronization implementations such as mutexes are widely used. 

**Roverapp** complete feature list is given below:

* Cloud communication to `Hono 0.5-M9 <https://www.eclipse.org/hono/api/>`_ infrastructure using REST API.
* Utilized drivers for Linux modules such as bluetooth (bluetooth-dev).
* I2C drivers and applications (threads) for OLED display, SRF02 ultrasonic sensor, HMC5883L magnetometer, GY-521Y accelerometer, etc.
* Temperature and humidity measurement using DHT22 sensor.
* Reactive implementations for TCP socket server and TCP socket client, with proper JSON formatted data for communication.
* OLED display application that is able to display bluetooth, Hono cloud, ethernet, wireless interface, and internet with the help of **status_library** library.
* OpenCV 2.4.9 utilization and image processing application (currently Traffic cone detection).
* SHARP Analog Proximity measurement sensor interfacing and implementations.
* SRF-02, HCSR-04, and Grove Ultrasonic sensor interfacing and implementations.
* Motor driving implementations.
* Timing measurement implementations with the help of **timing** library.
* CPU core utilization measurement implementation.
* Adaptive Cruise Control behavior implementation.
* Parking behavior implementation.
* Booth mode implementations.
* Implementations for bluetooth-based driving from Android phones.

*************************************************
roverapp Infrastructure
*************************************************
.. image:: ../roverstatic/images/roverapp_infra.png
   :width: 100%
   :align: center
   :alt: ../roverstatic/images/roverapp_infra.png

*************************************************
Downloading roverapp
*************************************************

.. note:: Rover-app source code is maintained under the following repository:

          `https://github.com/app4mc-rover/rover-app <https://github.com/app4mc-rover/rover-app>`_
		  
*************************************************
Getting started with roverapp
*************************************************
Installation
=================================================
.. note:: In order to see how roverapp is installed and compiled, please see :ref:`roverapp Installation <roverappinstallation>` section.


*************************************************
roverapp Complete Reference
*************************************************

Drivers
=================================================

External Libraries
=================================================

Created Libraries
=================================================

Tasks and Threads
=================================================