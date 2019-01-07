Development
===========

Getting Started
---------------

Within Lumavate, Experiences are created by studio users using a set of reusable Tools that provide discrete web functionality.

Lumavate provides a set of common tools as a standard feature of the platform. However, as a platform, Lumavate allows developers to develop their own tools that can be managed and made available in the Lumavate Studio so studio users can build Experiences using your own specific functionality.

A Tool consists of four primary things:

1. The code that implements the specific logic & capability (back-end processing, web page(s) rendering, etc.)
2. A list of properties studio users can set to adapt the tool functionality to their specific Experience
3. The Docker container that provides the operating environment needed to fully execute and render the tool
4. A standard set of REST APIs that simplifies common tasks and provides key capabilities to efficiently integrate the tool into the broader Lumavate platform

To build a tool, the dedicated Docker container for the tool is uploaded & "registered" with the Lumavate Platform. As part of the total solution, the platform provides pre-built Docker containers as a starting point.

We currently provide the following Docker container types as a template:

* Python / Flask / GUnicorn
* Python / Flask / Angular 2 / Nginx / GUnicorn
* C# / .NET
* Go

Within the Docker container, you may use any technology stack you prefer for web development. If your stack is not listed as a pre-built Docker template, you may build up your own Docker container that does support your development preference. The only requirement for a widget to become part of the Lumavate platform is it must implement a set of standard REST API endpoints that Lumavate uses to register your widget with the platform. A Docker container using any technology stack that implements our standard REST API endpoints is the foundation of every widget.

Installing Docker
-----------------

Docker must be installed on your development machine to use the Lumavate Test Harness.  Since Lumavate Tools are all container-based, a working knowledge of
Docker is not a bad thing.

The Community Edition of Docker is sufficent for Lumavate Development: https://www.docker.com/community-edition

You can also learn more about Docker at https://docs.docker.com

Installing Thor
---------------

Testing a Tool Locally
----------------------

Implementing Tool API Endpoints
-------------------------------

Every Tool developed to be registered within Lumavate must implement two key API endpoints

* DISCOVER

.. code-block:: python

  /<string:integration_cloud>/<string:widget_type>/discover/properties

This endpoint is how the widget informs the platform of which properties exist for this widget. The platform automatically adds a few platform level properties outside of this endpoint. They include the page_type, page_title, etc.  This is only used to add additional, widget specific properties. If the widget does not require any additional properties, this can return an empty set.

* RENDER

.. code-block:: python
  /<string:integration_cloud>/<string:widget_type>

This endpoint is called every time the tool must render itself either in preview or in production. This is the core endpoint that actually produces the UI for this tool.  In many cases, a microservice simply returns a status code for this route.


## Optional Endpoints

* ON_CREATE_VERSION

.. code-block:: python
  /<string:integration_cloud>/<string:widget_type>/instances/<int:instance_id>/on-create-version

This endpoint is called just BEFORE the properties are saved within the Lumavate Studio. This allows the developer to adjust any property data before saving. This is an optional endpoint.

* AFTER_CREATE_VERSION

.. code-block:: python
  /<string:integration_cloud>/<string:widget_type>/instances/<int:instance_id>/after-create-version

This endpoint is called just AFTER the properties are saved within the Lumavate Studio. This allows the developer to adjust any property data after saving.  This is an optional endpoint.

* DEFAULT

.. code-block:: python
  /<string:integration_cloud>/<string:widget_type>/instances/<int:instance_id>/index.html

This is a simple redirect endpoint that redirects the base URL to the fully qualified URL.

Understanding Lumavate Properties
---------------------------------

* Translatable Text - translated-text
* Text - text
* Color - color
* Image - image-upload
* Checkbox - checkbox
* toggle - toggle
* Dropdown - dropdown
* Numeric - numeric
* Multiple Selection - multiselect
* Page Link - page-link


