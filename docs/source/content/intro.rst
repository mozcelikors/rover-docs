.. toctree::
   :glob:

Introduction
#########################

.. image:: ../roverstatic/images/rover_logo.png
   :width: 25%
   :align: center
   :alt: ../roverstatic/images/rover_logo.png
   
*************************************************
What is rover or APP4MC-rover?
*************************************************

**Rover** (**APP4MC-rover**) is an open-source mobile robot that is designed to demonstrate the outcomes of `APP4MC <http://www.eclipse.org/app4mc>`_ and `APPSTACLE <https://itea3.org/project/appstacle.html>`_ projects. 
Rover features applications and tooling required to address complex research fields such as cloud communication, open-source tooling, multi-core and cluster computing.
Rover is equipped with powerful sensors, motors, and display units to interact with the physical world. Furthermore, Rover uses `Eclipse PolarSys project <polarsys.org/polarsys-rover-user-story-application-platform-project-multicore-app4mc>`_ for its chassis and mechanics.

Rover software, called **roverapp** features a multi-threaded (POSIX threads or Pthreads) C/C++ implementation that runs on Linux-based embedded single board computers (such as Raspberry Pi).
Rover features countless threads dedicated to communication infrastructure, sensor driving, display unit (such as OLED displays) utilization, and behavior modes (such as Parking, Adaptive Cruise Control, Manual Driving, and Booth Modes).
It also features drivers for sensors such as magnetometers, accelerometers, various ultrasonic sensors, and camera modules. Furthermore, OLED display, buttons, a buzzer are utilized.

It also features a web user interface,
called **roverweb**, that is used for many purposes such as sensor data visualization, camera streaming, displaying core utilization, and web-based robot control.
Roverweb is equipped with a powerful embedded back-end that is called `node.js <https://nodejs.org/en/>`_ and a main infrastructure library called `socket.io <https://socket.io/>`_. It makes use of the created javascript programs in order to create reactive web servers that communicate with websockets.

*************************************************
rover Motivations and Research
*************************************************

Rover is used as a demonstrator for two main subjects:

* Model-based multi-core software development evaluation and tool support (with `APP4MC <http://www.eclipse.org/app4mc>`_ tool)
	* For this purpose, threads are designed run in a schedulable and traceable fashion (with the help of **timing** library)
	* System traces are taken in Common Trace Format using Linux' perf profiler and customly created scripts.
	* APP4MC is used for modeling and deployment outcomes

* Cloud-based communication, data infrastructure testing (for `APPSTACLE <https://itea3.org/project/appstacle.html>`_ project)
	* For this purpose, a cloud instance with Eclipse Hono infrastructure is connected to using popular communication protocols such as MQTT, and REST API.
	* Eclipse Hono dashboard (using Grafana and InfluxDB) is configured.

*************************************************
rover Infrastructure
*************************************************
A small yet crucial portion of Rover's infrastructure (especially addressing network infrastructure) is given below. 

Roverapp is a C/C++ application with a single executable that makes use of its shared memory for data communication and that involves many drivers, custom libraries, external libraries, and many threads (with task functions).

Roverweb uses javascript (node.js) for its backend and javascript, jQuery, CSS, and HTML for its front-end.
Roverapp to roverweb communication is handled using NET sockets and using TCP protocol, whereas roverweb front-end and back-end is connected using HTTP websockets (using Socket.IO).

.. image:: ../roverstatic/images/complete_infra.png
   :width: 100%
   :align: center
   :alt: ../roverstatic/images/complete_infra.png