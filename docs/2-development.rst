.. _Developing tools:

Developing Tools
================

  There are three types of tools that the Lumavate platform uses :ref:`widgets <widgets>`, :ref:`microservice <microservices>`, & :ref:`component-sets <component-sets>`. 

  :ref:`Widgets` make-up the base :ref:`tools <tools>` that the other tools add on to and build off of. The tool should always provide a function that allows the :ref:`studio <studio>` user to set-up a UI for a function that is unique to that widget. 

  :ref:`Microservices` are the data-driven portion of :ref:`experiences <experiences>`. The tools take information that the :ref:`studio <studio>` user provides to create a recurring service or data-set that the rest of the tools can use. Microservices never have their own UI, but it can add UI functionality to a :ref:`widget <widgets>`.

  :ref:`Component-sets` are elements that will be reused by multiple :ref:`widgets <widgets>` or :ref:`microservices <microservices>`. The :ref:`tool <tools>` allows :ref:`studio <studio>` user to redistribute information collected in one widget or microservice to another or to provide identical functionality across multiple widgets or microservices. Component-sets will never have its own UI, but it will frequently add UI elements to compatible widgets and microservices.  

All Tools consist of four primary parts:

1. The :ref:`Docker container <Setting-up Docker>` that provides the operating environment needed to fully execute and render the tool
2. A standard set of REST APIs, for :ref:`widgets <API Endpoints W>` & :ref:`microservices <API Endpoints M>`, that simplifies common tasks and provides key capabilities to efficiently integrate the tool into the broader Lumavate platform
3. A list of :ref:`properties <properties>` studio users can set to adopt the tool functionality to their specific experience
4. The :ref:`code` that implements the specific logic & capability (back-end processing, web page(s) rendering, etc.)

.. _Setting-up Docker:

Setting-up Docker
-----------------

  To build a :ref:`tool <tools>`, a dedicated Docker container for the tool needs to be uploaded & registered with the Lumavate platform. The platform provides pre-built Docker containers for a starting point as part of the total solution. However, a developer can use any preferred web development technology stack. The developer will need to build his/her own Docker container if the preferred stack is not listed as a pre-built Docker template.

We currently provide the following Docker container types as a template:

  * Python / Flask / Angular 2 / Nginx / GUnicorn
  * C# / .NET
  * Go

In the following sections, we will explain how to:

* Install :ref:`Docker locally <Installing Locally>`
* Setup the Lumavate :ref:`pre-built containers <Setup Lumavate Containers>`
* Create your :ref:`own web-devlopment stack <Setup Custom Docker Containers>` 
* :ref:`Upload <Uploading Docker>` your web-devlopment stack to Lumavate

.. _Installing Locally:

Installing Locally
^^^^^^^^^^^^^^^^^^

Docker must be installed on your development machine in order to upload the :ref:`tool <tools>` you are creating to lumavate. Uploading Docker to your local envrioment will also give you acces to the :ref:`Lumavate Test Harness <thor>`.

To set-up Docker on your local machine, download at least the Community Edition of Docker. 

The community edition is free and can be downloaded at this site: https://www.docker.com/community-edition.

Instructions on how to install Docker are avalible through `the Docker help documentation <https://docs.docker.com/get-started/>`_.

Docker provides troubleshooring information for both `Windows <https://docs.docker.com/docker-for-windows/troubleshoot/>`_ and `Mac <https://docs.docker.com/docker-for-mac/troubleshoot/>`_ if you encounter issues with your download.

.. note::
  Lumavate relies heavily on Docker for its tool develpoment. Many of the commands, options, and syntax that are requared when devloping   a tool will come from Docker. Therfore, we recomand that you learn more about Docker and how it works at: https://docs.docker.com.

.. _Setup Lumavate Containers:

Setup Lumavate Containers
^^^^^^^^^^^^^^^^^^^^^^^^^
Lumavate provides three base containers to help devlopers start devloping tools with the Lumavate platform. The following explanation uses Go. Additional sample containers are provided for :ref:`python <python sample>` and :ref:`C# <C# sample>`.

Build the container
+++++++++++++++++++

1) Clone the `Lumavate sample repo <https://github.com/Lumavate-Team/widget-base-go>`_. 

2) Run the following command from the root directory of the repo.

		.. code-block:: html

		  docker build --no-cache --rm -t gobasewidget:1.0 .

	The --no-cache command is specifying that we do not want to use cache when building containers, and the --rm is specifiying that we want to remove intermediate containers after a successful builld.

3) An image will be built with the sample Docker file. 

.. note::
  Additional Docker Build Options are avaliable at: https://docs.docker.com/engine/reference/commandline/build/

Run the container
+++++++++++++++++

A container must finish building before it can be run. 

1) To start the container, run the following command.

		.. code-block:: html

		  docker run -d -p 5000:8080 --volume "$(pwd)"/widget:/go/src/widget gobasewidget:1.0

	The -d option puts the container in detached mode. while, the -p 5000:8080 command maps port 5000 on your machine to port 8080 on the container. Finally, the widget directory is maped to /go/src/widget directory inside the container through the --volume "$(pwd)"/widget:/go/src/widget gobasewidget:1.0 command. Mapping to the widget directory will allow you to modify files in your local widget directory, and it will reload the process when the files change. 

2) The container will now be running in detached mode. A sample of the tool will be running on http://localhost:5000.

.. note::
  Additional Docker Run Options can be found here: https://docs.docker.com/engine/reference/commandline/run/

Check the logs
++++++++++++++

1) Run the following command to collect container info.

	.. code-block:: html

	  docker ps

2) The command will return a list of containers, shown below. Collect the Container ID for the tool who's logs you wish to stream.

	.. code-block:: html
	
	  CONTAINER ID        IMAGE                  COMMAND                  CREATED             STATUS              PORTS                       NAMES
	  676f62d88565        gobasemac4:dev021418   "/bin/sh -c 'bee run'"   15 minutes ago      Up 16 minutes       0.0.0.0:5000->8080/tcp       dreamy_albattani

3) Using the Container ID, run the command:

	.. code-block:: html

	  docker logs -f 676

4) The selected container's logs will now be streaming directly to your terminal.

Run Inside Thor
++++++++++++++

.. code-block:: html

  DOCKER_IP=`ifconfig | grep "inet " | grep -Fv 127.0.0.1 | awk '{print $2}'`
  docker run --rm -d \
    -e "PUBLIC_KEY=mIhuoMJh0jbA5W4pUUNK" \
    -e "PRIVATE_KEY=LXycaMpw5BzgfhsS4ydNxGzJ36qMnPrQHI8u2x3wQCZCZyGtZ4sOQbkEWnHmVchZEa79a0Y3xK7IKCymSLkugyabbJUGuXfyuoKL" \
    -e "HOST_IP=$DOCKER_IP" \
    -e "WIDGET_PORT=8091" \
    -e "HOST_PORT=80" \
    --name=thor \
    -p 80:4201 \
    quay.io/lumavate/thor:latest

  docker run -d --rm \
    --volume "$(pwd)"/widget:/go/src/widget:rw \
    -e "PUBLIC_KEY=mIhuoMJh0jbA5W4pUUNK" \
    -e "PRIVATE_KEY=LXycaMpw5BzgfhsS4ydNxGzJ36qMnPrQHI8u2x3wQCZCZyGtZ4sOQbkEWnHmVchZEa79a0Y3xK7IKCymSLkugyabbJUGuXfyuoKL" \
    -e "BASE_URL=http://$DOCKER_IP" \
    -e "WIDGET_URL_PREFIX=/ic/widget/" \
    -e "PROTO=http://" \
    --name=widget-base-go \
    -p 8091:8080 \
    quay.io/lumavate/widget-base-go:latest

.. _Setup Docker Containers:

Setup Custom Docker Containers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This section will explain how to setup custom stacks and containers to work with the Lumavate platform. It will not explain what stacks are, how to create one, or how they relate to containers. Stack and container information can be found in the `Docker help documentation <https://docs.docker.com/get-started/part5/>`_. 

Coming Soon!

.. _Uploading Docker Containers:

Uploading Docker Containers
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Docker containers can be uploaded to the Lumavate platform in two different ways, through the platform and through the CLI. This section will explain how to manually upload containers using the Lumavate platform. The CLI documentation explains how to :ref:`upload containers using the CLI <CLI Syntax>`.

.. note::
	The developer must be a user in the command center in order to upload containers through the platform. Developers only need a CLI profile in order to upload containers through the CLI.

Uploading A Tool
++++++++++++++++

1) Login to the platform and select the command center where you want to upload the container.

	image goes here 
	
2) Once inside the command center, you will have the option to add a :ref:`widget <widgets>`, :ref:`microservice <microservices>`, or :ref:`component-set <component-sets>`. Click on the corresponding tab in the sidebar for the tool you wish to add. You will be taken to that tool’s library page.

	image goes here

3) Inside the tool library page, you will have the option to add a new container or edit an existing one.

	a) To add a new container: 
	
	- Click the blue + button in the bottom right corner of the tool Library page.

		image goes here
	
	- A pop-up will appear asking for the tool container name, urlref, and icon. Fill out all the fields, and click the add button.

		image goes here

	b) To edit an existing container:
	
	- Click on the info card for the container you wish to edit. 

		image goes here

		.. warning::
			Developers are unable to add or edit versions in containers that other command centers have shared with him/her.

4) You will be taken into the Container Info page for the container you just created or selected. Click the blue + button in the bottom right corner of the page to add a new version of your tool.
	
	image goes here

5) You will be redirected to an Add Version page. You will have the option to add a new version from scratch or to use an existing version as a template. 

	image goes here

	a) To make a version from scratch:
	
	- Go to the second section of fields in the Version Add form. Fill out the port, version number, and label field.
		
		image goes here
		
		.. note::
			The :ref:`port numbers <port>` and corresponding programing languages can be found :ref:`here <port>`. 
	
	- Scroll to the bottom of the page, and click the upload button to upload your new Docker container.
			
			Image goes here
			
		.. warning::
		Different tools accept different file types. If you are experiencing problems finding your file when trying to upload it, check to make sure it is the correct file type for the tool you are creating. For more information, please visit the :ref:`widget <widget port>.`, :ref:`microservice <microservice port>`, or :ref:`component-set <component-set port>` page. 

	b) To use an existing version:
	
	- open the version template drop-down located in the first section at the top of the Add Version form. Select the version you wish to use as your base. 
	
		image goes here

	- All of the fields other than the version number field should have updated with the previous version’s information. Fill out the Version Number field with the new version’s version number. 

		.. note::
			Component-sets will also need a new image uploaded as the previous version’s image will not carry over. The platform does not save component-sets as a unit but instead as a series of files, so the image cannot be recompiled. Widgets and microservices will populate with the previous version’s image. 

6) Fill-out any additional fields that your tool requires. 

	images go here
	
	.. warning::
		Any error in the Direct Include, CSS Include, or Environment Variables fields will cause a tool to error when starting up. 

7) Click Save. 

8) You will be redirected back to the Container Info page where the new version’s info card can be seen. The version info card will contain basic information about the version and its status. 

	image goes here  

Start A Version
+++++++++++++++

1) Hover over the version info card. Several buttons will appear that allow the user to refresh status, edit, view logs, delete, and stop/start the version.  

	image goes here
	
2) To start the version, click the green arrow on the rightmost edge of the version info card.

3) The status of the version will change from stopped to a spinning icon. You can refresh the status by click the refresh status button. The tool will take a minute or two to finish validating. The larger the tool the longer the validation period.     

4) After finishing validating, the status will change to either started or error. If the status is error, the version was unable to connect with the platform.  

Sharing A Tool
++++++++++++++

1) To share your version with a studio or command center, click the edit button inside the share section located on the Container Info page.

	image goes here
	
	.. note:: 
		Developers can share tools that have been shared with them.
		
2) A pop-up will appear with all the child command centers and studios your command center has access to. Check the checkbox next to all the command centers and studios you want to share the tool container with.  

	image goes here
	
	.. note::
		The platform shares containers so any versions added to the container will automatically be shared with the selected child command centers and studios. To restrict studio access to versions, label the version dev or old. Old is for deprecated versions. Dev is for development versions. Studios will be unable to add old or dev versions to experiences and will be prevented from published experiences with old versions.

3) Click Save. The share section on the container page should update to show the command centers and studios you are currently 		sharing your container with. 
	
	image goes here
	
	.. note::
		There are three types of children shown in the share section list, command centers, dev/prod studios, and prod studios. Dev/prod studios can add and publish dev versions. Prod studios can only use prod versions.  

.. include:: ../PROPERTIES.rst

.. include:: ../WIDGETS.rst

.. include:: ../MICROSERVICES.rst

.. include:: ../COMPONENTS.rst

.. _Lumavate tools:

Lumavate Tools
==============
Coming soon.
