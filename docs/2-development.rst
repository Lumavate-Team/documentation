.. _Developing tools:

Developing Tools
================

  There are three types of tools that the Lumavate platform uses :ref:`widgets`, :ref:`microservice`, & :ref:`component-sets`. 

  :ref:`Widgets` make-up the base tool that the other tools add on to and build off of. The tool should always provide a function that allows the :ref:`studio` user to set-up a UI for a function that is unique to that :ref:`widget`. 

  :ref:`Microservices` are the data-driven portion of :ref:`experiences`. The tools take information that the :ref:`studio` user provides to create a recurring service or data-set that the rest of the tools can use. :ref:`Microservices` never have their own UI, but it sometimes adds UI functionality to a widget.

  :ref:`Component-sets` are elements that will be reused by multiple widgets or microservices. The tool allows :ref:`studio` user to redistribute information collected in one widget or microservice to another or to provided identical functionality across multiple widgets or microservices. :ref:`Component-sets` will never have its own UI, but it will frequently add UI elements to compatible widgets and microservices.  

All Tools consists of four primary parts:

1. The :ref:`Docker container <Setting-up Docker>` that provides the operating environment needed to fully execute and render the tool
2. A standard set of :ref:`REST APIs`, for :ref:`widgets` & :ref:`microservices`, that simplifies common tasks and provides key capabilities to efficiently integrate the tool into the broader Lumavate platform
3. A list of :ref:`properties` :ref:`studio` users can set to adopt the tool functionality to their specific :ref:`experience`
4. The :ref:`code` that implements the specific logic & capability (back-end processing, web page(s) rendering, etc.)


Setting-up Docker
-----------------

  To build a tool, a dedicated Docker container for the tool needs to be uploaded & registered with the Lumavate platform. The platform provides pre-built Docker containers as a starting point as part of the total solution. However, a developer can use any preferred web development technology stack he/she prefers. The developer will need to build his/her own Docker container if the preferred stack is not listed as a pre-built Docker template.

  We currently provide the following Docker container types as a template:

  * Python / Flask / Angular 2 / Nginx / GUnicorn
  * C# / .NET
  * Go

In the following sections, we will explain how to:

* Install :ref:`Docker locally <Installing Locally>`
* Setup the Lumavate :ref:`pre-built containers <Setup Lumavate Containers>`
* Create your :ref:`own web-devlopment stack <Setup Custom Docker Containers>` 
* :ref:`Upload <Uploading Docker>` your web-devlopment stack to Lumavate

Installing Locally
^^^^^^^^^^^^^^^^^^

Docker must be installed on your development machine in order to upload the tool you are creating to lumavate. Uploading Docker to your local envrioment will also give you acces to the Lumavate Test Harness.

To set-up Docker on your local machine:

1) Download at least the Community Edition of Docker. The community edition is free and can be downloaded at this site: https://www.docker.com/community-edition.

.. note::
  Lumavate relies heavely on Docker for its tool develpoment. Many of the commands, options, and syntax that are requared when devloping   a tool will comes from Docker. Therfore, we recomand that you learn more about Docker and how it works at: https://docs.docker.com.


Setup Lumavate Containers
^^^^^^^^^^^^^^^^^^^^^^^^^

Link to pre-fab docker images
Briefly explain how to build & save a Docker container that can be used to upload into Lumavate

Setup Custom Docker Containers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Uploading Docker Containers
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. _Lumavate tools:

Lumavate Tools
==============

.. include:: ../PROPERTIES.rst

.. include:: ../WIDGETS.rst

.. include:: ../MICROSERVICES.rst

.. include:: ../COMPONENTS.rst
