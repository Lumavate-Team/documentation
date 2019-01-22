.. _Developing tools:

Developing Tools
================

  There are three types of tools that the Lumavate platform uses :ref:`widgets <widgets>`, :ref:`microservice <microservices>`, & :ref:`component-sets <component-sets>`. 

  :ref:`Widgets` make-up the base :ref:`tools <tools>` that the other tools add on to and build off of. The tool should always provide a function that allows the :ref:`studio <studio>` user to set-up a UI for a function that is unique to that widget. 

  :ref:`Microservices` are the data-driven portion of :ref:`experiences <experiences>`. The tools take information that the :ref:`studio <studio>` user provides to create a recurring service or data-set that the rest of the tools can use. Microservices never have their own UI, but it can add UI functionality to a :ref:`widget <widgets>`.

  :ref:`Component-sets` are elements that will be reused by multiple :ref:`widgets <widgets>` or :ref:`microservices <microservices>`. The :ref:`tool <tools>` allows :ref:`studio <studio>` user to redistribute information collected in one widget or microservice to another or to provide identical functionality across multiple widgets or microservices. Component-sets will never have its own UI, but it will frequently add UI elements to compatible widgets and microservices.  

All Tools consist of four primary parts:

1. The :ref:`Docker container <Setting-up Docker>` that provides the operating environment needed to fully execute and render the tool
2. A standard set of :ref:`REST APIs <REST APIs>`, for widgets & microservices, that simplifies common tasks and provides key capabilities to efficiently integrate the tool into the broader Lumavate platform
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

To set-up Docker on your local machine download at least the Community Edition of Docker. 

The community edition is free and can be downloaded at this site: https://www.docker.com/community-edition.

Instructions on how to install Docker are avalible through `the Docker help documentation <https://docs.docker.com/get-started/>`_.

Docker provides troubleshooring information for both `Windows <https://docs.docker.com/docker-for-windows/troubleshoot/>`_ and `Mac <https://docs.docker.com/docker-for-mac/troubleshoot/>`_ if you encounter issues with your download.

.. note::
  Lumavate relies heavely on Docker for its tool develpoment. Many of the commands, options, and syntax that are requared when devloping   a tool will comes from Docker. Therfore, we recomand that you learn more about Docker and how it works at: https://docs.docker.com.

.. _Setup Lumavate Containers:

Setup Lumavate Containers
^^^^^^^^^^^^^^^^^^^^^^^^^
Coming soon!

.. include:: ../widget-base-go/blob/master/README.md

.. _Setup Custom Docker Containers:

Setup Custom Docker Containers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Coming soon!

.. _Uploading Docker Containers:

Uploading Docker Containers
^^^^^^^^^^^^^^^^^^^^^^^^^^^
Coming soon!

.. include:: ../PROPERTIES.rst

.. include:: ../WIDGETS.rst

.. include:: ../MICROSERVICES.rst

.. include:: ../COMPONENTS.rst

.. _Lumavate tools:

Lumavate Tools
==============
Coming soon.
