
.. _Developing tools:

================
Developing Tools
================

There are three types of tools that the Lumavate platform uses: widgets, microservices, and component sets. 

 :ref:`Widgets` are the base that the other tools add on to and build off of. This tool should always allow studio users to customize part of the end user UI. 

 :ref:`Microservices` are the data-driven portion of experiences. This tool takes information that studio users provide to create a recurring service or data-set that the rest of the tools can use. Microservices almost never have their own end user UI, instead they add functionality to widgets.

 :ref:`Component sets <component-sets>` are elements that are used by widgets or microservices. This tool has two primary functions. It allows studio users to redistribute information collected in one widget or microservice to another. It also provides identical functionality across multiple widgets. Component sets will never have their own UI, but they frequently add UI elements to compatible widgets.  
|
*Widgets* and *microservices* consist of four primary parts:
 #. The :ref:`Docker container <Setting-up Docker>` that provides the operating environment needed to fully execute and render the tool. 
 #. A standard set of :ref:`widget REST APIs <API Endpoints W>` and :ref:`microservice REST APIs <API Endpoints M>` that simplify common tasks and provide key capabilities to efficiently integrate the tool into the broader Lumavate platform.
 #. A :ref:`list of properties <properties>` studio users can set to adopt the tool functionality to their specific experience.
 #. The :ref:`code <Code Samples>` that implements the tool's specific logic and capability (back-end processing, web page(s) rendering, etc.).
|
*Component sets* consist of a :ref:`component.json metadata file <metadata>` that contains two primary parts:
 #. A :ref:`list of properties <properties>` studio users can set to adopt the tool functionality to their specific experience.
 #. The :ref:`code <Code Samples>` that implements the tool's specific logic and capability (called template and style in the metadata file) 

________________________________________________________________________________________________________________________________________

.. _Setting-up Docker:

Setting-up Docker
-----------------

To build a tool, a dedicated Docker container for the tool needs to be uploaded and registered with the Lumavate platform. 

The platform provides pre-built Docker containers to help developers get started as part of our total solution. However, a developer can use any preferred web development technology stack. The developer will need to build his/her own Docker container if the preferred stack is not listed as a pre-built Docker template.

We currently provide the following Docker container types as a template:

  * Python / Flask / Angular 2 / Nginx / GUnicorn
  * C# / .NET
  * Go

In the following sections, we will explain how to:

* Install :ref:`Docker locally <Installing Locally>`
* Set up the Lumavate :ref:`prebuilt containers <Set Up Lumavate Containers>`
* Create your :ref:`own web-development stack <Set Up Custom Docker Containers>` 
* :ref:`Upload your web-devlopment stack <Uploading Docker Containers>` to Lumavate

.. _Installing Locally:

Installing Locally
^^^^^^^^^^^^^^^^^^

 Docker must be installed on your development machine in order to upload a tool to the Lumavate platform. 

  .. Docker must be added to your local environment for you to access the :ref:`Lumavate Test Harness <thor>`.

 To set up Docker on your local machine:
 
  #. Download at least the Community Edition of Docker. The community edition is free and can be downloaded from the `Docker site <https://www.docker.com/community-edition>`_.
  
  #. You will be taken to a download page. Select the correct Docker Engine for your operating system.
  
  #. Login to Docker or create an account. 
  
  #. Click the Get Docker button
  
  #. Open and run the Docker Installer
  
  #. Docker should now be set up on your machine. Run ``docker version`` in a command prompt to make sure Docker downloaded correctly. A version number should be returned:
  
     .. code-block:: bash
     
        Client: Docker Engine - Community
	Version:           18.09.2
	API version:       1.39
	Go version:        go1.10.8
	Git commit:        6247962
	Built:             Sun Feb 10 04:12:31 2019
	OS/Arch:           windows/amd64
	Experimental:      false
	
	Server: Docker Engine - Community
	Engine:
	 Version:          18.09.2
	 API version:      1.39 (minimum version 1.12)
	 Go version:       go1.10.6
	 Git commit:       6247962
	 Built:            Sun Feb 10 04:13:06 2019
	 OS/Arch:          linux/amd64
	 Experimental:     false


 Additional instructions on how to install Docker are available through `the Docker help documentation <https://docs.docker.com/get-started/>`_.

 Docker provides troubleshooting information for both `Windows <https://docs.docker.com/docker-for-windows/troubleshoot/>`_ and `Macs <https://docs.docker.com/docker-for-mac/troubleshoot/>`_ if you encounter issues with your download. 

 .. tip::
   Lumavate relies heavily on Docker for its tool development. Many of the commands, options, and syntax that are required when developing a tool will come from Docker. Therefore, we recommend that you learn more about Docker and how it works at: https://docs.docker.com.

.. _Set Up Lumavate Containers:

Set Up Lumavate Prebuilt Containers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
 Lumavate provides three base containers to help developers start developing tools for the Lumavate platform. The following explanation uses Go. For the full Go container, please see the `Go Github repository <https://github.com/Lumavate-Team/widget-base-go>`_. Additional :ref:`Python sample <python sample>` and :ref:`C# sample <C# sample>` containers are provided.

.. _Build The Container:

Build The Container
+++++++++++++++++++

 #. Clone the `Lumavate sample repo <https://github.com/Lumavate-Team/widget-base-go>`_.
 
 #. Unzip the file you just downloaded. 
 
 #. Open a command window, and CD into the file you downloaded from the sample repo.
 
    .. code-block:: go
 
  	$ cd C:/User/FileLocation/RepoDownload/widget-base-go-master

 #. Run the following command to install all the required node packages for the tool. Docker reads the package.json file to get the list of required node packages. 
 
    .. code-block:: go
    
       $ npm install
 
 #. Run the following command from the root directory of the repo.
 
    .. code-block:: go
 
  	$ docker build --no-cache --rm -t gobasetool:1.0 .
	
    | The ``docker build .`` command tells Docker you want to build the current file. You can specify the full path if you do not want to cd into the file.
    
    | The ``--no-cache`` command specifies that cache will not be used when building containers.
    
    | The ``--rm`` command removes intermediate containers after a successful build.
    
    | The ``-t gobasetool:1.0`` command names the tool gobasetool and tags the tool as 1.0. 

 #. An image will be built with the sample Docker file. 

 .. note::
  	Additional Docker build options are available at: https://docs.docker.com/engine/reference/commandline/build/

.. _Run The Container:

Run The Container
+++++++++++++++++

 A container must finish building before it can be run. 

 #. Cd into the tool's file you wish to run.
 
    .. code-block:: go
    
       $ C:/User/FileLocation/RepoDownload/widget-base-go-master 
 
 #. Run the following command in a command window.
 
    .. code-block:: go
	
	$ docker run -d -p 5000:8080 --volume "$(pwd)"/widget:/go/src/widget gobasetool:1.0
	
    | The ``docker run gobasetool:1.0`` command tells Docker you want to run the gobasetool:1.0 container. 
    
    | The ``-d`` option puts the container in detached mode.
    
    | The ``-p 5000:8080`` command maps port 5000 on the machine to port 8080 on the container.
    
    | The ``--volume "$(pwd)"/widget:/go/src/widget`` command maps the widget directory to the path /go/src/widget inside the current directory. The absolute path can be specified instead of the current directory by replacing ``"$(pwd)"`` with the complete file path.
    
    .. tip::
       Mapping to a directory allows the developer to modify files in his/her local tool directory. It also reloads the process by restarting Go when the files change allowing the developer to update the files inside the container in real time.  

 #. The container will now be running in detached mode. A sample of the tool will be running on http://localhost:5000.

 .. note::
    Additional Docker run options can be found here: https://docs.docker.com/engine/reference/commandline/run/

.. _Check The Logs:

Check The Logs
++++++++++++++

 #. Open a command window, and Run the following command to collect container info.

    .. code-block:: go
 
       $ docker ps

 #. The command will return a list of containers, shown below. Collect the Container ID or Name of the tool whose logs you wish to stream.

    .. code-block:: go
 
  	CONTAINER ID        IMAGE                  COMMAND                  CREATED             STATUS              PORTS                       NAMES
 	676f62d88565        gobasemac4:dev021418   "/bin/sh -c 'bee run'"   15 minutes ago      Up 16 minutes       0.0.0.0:5000- >8080/tcp     gobasetool

 #. Using the Container ID or Name, run the command:

    .. code-block:: go
 
       $ docker logs -f 676f62d88565

 #. The selected container's logs will now be streaming directly to your terminal.

.. _Set Up Custom Docker Containers:

Set Up Custom Docker Containers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

 Any Docker container may be used to create Tools within Lumavate allowing developers to use the Docker Hub Image they want. Truly, custom Docker containers can also be used by creating a custom base image. These two options allow developers to create the precise runtime environment needed for a given tool.
 
Docker Hub Images
+++++++++++++++++
 
 The `Docker Hub <https://hub.docker.com/search?q=&type=image>`_ contains all publicly available registered Docker images, called containers, for use with a variety of technologies. The containers range from programming language libraries to dev ops applications to fully functioning programs. These containers can be downloaded using ``docker pull <<container name from Docker hub>>`` and run using ``docker run <<container name from Docker hub>>``.
 
 Base Lumavate containers all start with a base image from the Docker Hub:
 
  * `Docker hub Go container <https://hub.docker.com/_/golang>`_ 
  * `Docker hub Python container <https://hub.docker.com/_/python>`_ 
  * `Docker hub .Net container <https://hub.docker.com/_/microsoft-dotnet-core>`_
 
Custom Base Images
++++++++++++++++++
 
 As Docker expects users to use a base image when creating a new Docker file, there are extra steps one needs to take in order to make a completely custom Docker container. If you are interested in this option, we recommend that you read `the Docker documentation for base images <https://docs.docker.com/develop/develop-images/baseimages/>`_. 
 
.. _Uploading Docker Containers:

Uploading Docker Containers
^^^^^^^^^^^^^^^^^^^^^^^^^^^

 Docker containers can be uploaded to the Lumavate platform in two different ways, through the platform and through the CLI. This section will explain how to manually upload containers using the Lumavate platform. The CLI documentation explains how to :ref:`upload containers using the CLI <CLI>`.

 .. note::
    The developer must be a user in the command center in order to upload containers through the platform. Developers need a CLI profile in order to upload containers through the CLI.

.. _Uploading A Tool:

Uploading A Tool
++++++++++++++++

 #. Login to the platform and select the command center where you want to upload the container.
	
    .. figure:: ../images/enviromentselect.PNG
       :align: center
       :width: 400px
       :alt: Image of the Lumavate Organization Select Page.
      
       The Organization Select page allows users to select the command center or studio he/she wishes to edit. Command centers are shown with a gear Settings icon. Studios are shown with a paint palette Color_Lens icon.
	
 #. Once inside the command center, you will have the option to view the uploaded :ref:`widgets <widgets>`, :ref:`microservices <microservices>`, or :ref:`component sets <component-sets>`. Click on the corresponding tab in the sidebar for the tool you wish to add. You will be taken to that tool’s Library page.

    .. figure:: ../images/sidebarcc.PNG
       :align: center
       :width: 550px
       :alt: Image of the Lumavate command center navigation sidebar with the Widget, Microservice, and Component set tabs highlighted.
      
       The navigation sidebar links to the Widget, Microservice, Component set, Users, and CLI pages.

 #. Inside the tool Library page, you will have the option to add a new container or edit an existing one. A tool's versions are grouped in a container. New tool will need a new container. New versions of old tools will be added to the original version’s container. 

    * To add a new container: 

       a. Click the blue + Add button in the bottom right corner of the tool's Library page.

         .. figure:: ../images/toolpagewithbuttonhighlighted.PNG
	    :align: center
	    :width: 450px
	    :alt: Image of the Lumavate tool Library page with the Add button highlighted.
	   
	    The tool Library pages list all the containers the command center has access to for the specified tool.

       b. A pop-up will appear asking for the tool container's name, URL ref, and icon. Fill out all the fields, and click the Save button.

         .. figure:: ../images/addcontainerpopup.PNG
	    :align: center
	    :width: 600px
	    :alt: Image of the Lumavate Add Container pop-up.
	   
	    The Add Container pop-up asks for the container's Name, URL Ref, and Icon.
        
         The required fields are:
	   * Name: what the container will be called in the platform.
	   * URL ref: what the tool will be called in the experience URL.
	   * Icon: the image shown alongside the tool in the platform.

    * To edit an existing container, click on the Lumavate Container Card for the container you wish to edit. 
      
       .. figure:: ../images/toolpagewithcontainercardhighlighted.PNG
	  :align: center
	  :width: 450px
	  :alt: Image of the Lumavate Container Card.
	   
	  The Container Info Card displays the container’s name, icon, publisher, highest version number, highest version label, number of experiences using the container, total running versions, and last modified date.

       .. warning::
          Developers are unable to add or edit versions in containers that other command centers have shared with them.

 #. You will be taken into the Container Info page for the container you just created or selected. Click the blue + Add button in the bottom right corner of the page to add a new version of your tool.

    .. figure:: ../images/containerinfopagewithhighlightedaddbutton.PNG
       :align: center
       :width: 500px
       :alt: Image of the Lumavate Container Info page with the Add button highlighted.
      
       The Container Info page shows the container’s basic information, share status, and version information.

 #. You will be redirected to an Add Version page. You will have the option to add a new version from scratch or to use an existing version as a template. 

    .. figure:: ../images/addversionpage.PNG
       :align: center
       :width: 500px
       :alt: Image of the Lumavate Add Version page.
      
       The Add Version page asks for the Version Template, Port, Version Number, Label, Includes, and Image for the new version.
   
    The Add Version page is split into four sections:
      * Section one allows users to use a previous version as a template
      * Section two asks for basic version information
      * Section three allows users to add additional variables
      * Section four asks users to upload their version image
    
    * To make a version from scratch:
   
       a. Go to the second section of fields in the Version Add form. Fill out the Port, Version Number, and Label fields.
      
          .. figure:: ../images/versioninfofields.PNG
	     :align: center
	     :width: 400px
	     :alt: Image of the version info fields in the second edit section.
	   
	      The Port, Version Number, and Label fields are found in the the second edit section.

          The required fields are:
            - Port: which is the port number for the  programing language used in the image
	    - Version number: which is the version's major, minor, and patch
	    - Label: which labels the version as in-development (dev), ready-for-production (prod), or deprecated (old)
	 
	  .. note::
             The port number will either be the port number set in the tool’s code or the tool’s programming language’s standard port number. The port number must match the tool code’s port number. The tool will error while starting up if they do not match. 

       b. Scroll to the bottom of the page to the last section. Click the Upload button to upload your new Docker container image.
      
          .. figure:: ../images/imageuploadfield.PNG
	     :align: center
	     :width: 450px
	     :alt: Image of the content container section which contains the Upload button.
	   
	     The upload image field is in the content container section and contains the Upload button. 	

          .. warning::
             Different tools accept different file types. Check that the correct file type for the tool was used if you are unable to find the image file. For more information on accepted file types, please visit the :ref:`widget <Accepted File Types W>`, :ref:`microservice <Accepted File Types M>`, or :ref:`component set <Accepted File Types C>` pages. 

    * To use an existing version:
      
       a. Go to the first section at the top of the Add Version form, and open the version template dropdown. Select the version you wish to use as your base. 
      
          .. figure:: ../images/versionfield.PNG
	     :align: center
	     :width: 450px
	     :alt: Image of the Version Template dropdown in the first edit section.
	   
	     The Version Template field is in the first edit section. The page will automatically update when a version is selected from the dropdown clearing any previously filled-out fields.

       b. All fields other than the Version Number field should have updated with the previous version’s information. Fill out the Version Number field with the new version number. 

          .. note::
	     Component sets will also need a new image uploaded as the previous version’s image will not carry over. 

 #. Fill-out any additional fields that your tool requires. 
   
    * To add environment variables:
   
      .. figure:: ../images/envfield.PNG
         :align: center
         :width: 500px
         :alt: Image of the Environment Variables edit section from the widget and microservice Add Version page.
      
         The widget and microservice Add Version pages allow users to add environmental variables using the Environment Variables edit section.
      
      a. Click the + add_circle_outline button by the Environmental Variables header. This will create a new environmental variable field. 
      
      b. Fill out the Environment Key and Environment Value fields with the necessary information.   
   
    * To add direct includes: 

      .. figure:: ../images/directfield.PNG
         :align: center
         :width: 500px
         :alt: Image of the Direct Includes edit section from the component set Add Version page.
      
         The component set Add Version page allows users to add direct includes using the Direct Include edit section.
   
      a. Click the + add_circle_outline button by the Direct Includes header. This will create a new direct include variable field. 
      
      b. Fill out the Direct Include field with the necessary information.
   
    * To add CSS includes:
   
      .. figure:: ../images/cssfield.PNG
         :align: center
         :width: 500px
         :alt: Image of the CSS Includes edit section from the component set Add Version page.
      
         The component set Add Version page allows users to add CSS using the CSS Include section.
   
      a. Click the + add_circle_outline button by the CSS Includes header. This will create a new CSS variable field.
      
      b. Add your CSS variables to the CSS Include field.   
	
    .. warning::
       Any error in the Direct Include, CSS Include, or Environment Variables fields will cause a tool to error when starting up. 

 #. Click Save. 

 #. You will be redirected back to the Container Info page where the new version’s info card can be seen. The Version Info Card will contain basic information about the version and its status. 

    .. figure:: ../images/versioncard.PNG
       :align: center
       :width: 800px
       :alt: Image of a version card found on the Container Info page.
      
       The version card displays the version number, label, created at date, number of experiences using the version, and status. 

.. _Start A Version:

Start A Version
+++++++++++++++

 #. Hover over the version info card. Several buttons will appear that allow the user to refresh status, edit, view logs (receipt), delete, and start(play_arrow)/stop the version.  

    .. figure:: ../images/versioncardhover.PNG
       :align: center
       :width: 800px
       :alt: Image of a version card with icons that appear on hover highlighted. The icons are Refresh, Edit, Receipt (view logs), Delete, and Play_Arrow(start)/Stop respectively.
      
       The Version Info Card displays the version number, label, created at date, number of experiences using the version, and status.

 #. To start the version, click the green arrow Start button on the rightmost edge of the version info card.

 #. The status of the version will change from stopped to a spinning icon. You can refresh the status by clicking the Refresh button. The tool will take a minute or two to finish validating. The larger the tool is the longer the validation period.     

 #. After finishing validating, the status will change to either started or error. If the status is error, the image uploaded had an error in it that prevented it from running in the platform.  

.. _Sharing A Tool:

Sharing A Tool
++++++++++++++

 #. To share a container with a studio or command center, click the Edit button inside the Share section located on the Container Info page.

    .. figure:: ../images/sharesection.PNG
       :align: center
       :width: 800px
       :alt: Image of a Share section with the Edit button located inside the section.
      
       The Share section shows what studios and command centers you have shared your container with.

    .. note:: 
       Developers can share tools that have been shared with them.
		
 #. A pop-up will appear with your command center's child command centers and studios. Check the checkbox next to all the command centers and studios you want to share the tool container with.  

    .. figure:: ../images/sharesectionpopup.PNG
       :align: center
       :width: 500px
       :alt: Image of the Share section pop-up.
      
       The Share section pop-up allows users to share or unshare a container with any of their child studios or command centers. However, the user cannot unshare from a studio or command center that is currently using the tool in an experience. 
	
    .. note::
       The platform shares containers so any version added to the container will automatically be shared with the selected child command centers and studios. To restrict studio access to versions, label the version dev or old. Most studios will be unable to add or publish old or dev versions of tools.

 #. Click Save. The Share section on the container page should update listing the command centers and studios you are currently sharing your container with. 
	
    .. figure:: ../images/sharesectionupdated.PNG
       :align: center
       :width: 800px
       :alt: Image of the Share section that lists the studio and command center that the tool has been shared with.
      
       There are three types of child organizations shown in the share section list, command centers, dev/prod studios, and prod studios. Dev/prod studios can add and publish prod, dev, and old versions. Prod studios can only add or publish prod versions.  

________________________________________________________________________________________________________________________________________

.. include:: ../PROPERTIES.rst

________________________________________________________________________________________________________________________________________

.. include:: ../WIDGETS.rst

________________________________________________________________________________________________________________________________________

.. include:: ../MICROSERVICES.rst

________________________________________________________________________________________________________________________________________

.. include:: ../COMPONENTS.rst
