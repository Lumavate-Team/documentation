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

Every Tool developed to be registered within Lumavate must implement two key API endpoints.
Each endpoint will contain dynamic parts that correspond to both the type of Tool uploaded (denoted as widget_type), along with the logical location of the
Tool itself (denoted as integration_cloud).  Both of these URI parts are in the form of a string & should be consumed dynamically.

Required Endpoints
^^^^^^^^^^^^^^^^^^

* DISCOVER

.. code-block:: python

  /<string:integration_cloud>/<string:widget_type>/discover/properties

This endpoint is how the widget informs the platform of which properties exist for this widget. The platform automatically adds a few platform level properties outside of this endpoint. They include the page_type, page_title, etc.  This is only used to add additional, widget specific properties. If the widget does not require any additional properties, this can return an empty set.

* RENDER

.. code-block:: python

  /<string:integration_cloud>/<string:widget_type>

This endpoint is called every time the tool must render itself either in preview or in production. This is the core endpoint that actually produces the UI for this tool.  In many cases, a microservice simply returns a status code for this route.


Optional Endpoints
^^^^^^^^^^^^^^^^^^

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

Registering Properties
----------------------

The Discover endpoint enables the ability to expose properties through the Lumavate Studio.
Each property is defined by denoting the tab, section, name, & label using the following JSON structure:

.. code-block:: javascript

  var property = {
  'classification': 'Tab Name',
  'section': 'Section Name',
  'help': 'Help text for the property.  Use Markup to provide additional help to the Studio User',
  'name': 'Property Name which will be used to reference this property',
  'label': 'Property Label',
  'type': 'Property Type - see below'
  }

The following list of properties are available & can be implmented by including the appropriate JSON in the Discover endpoint.

* Translatable Text
* Text
* Color
* Image
* Checkbox
* Toggle
* Dropdown
* Numeric
* Multiple Selection
* Page Link

Translatable Text
^^^^^^^^^^^^^^^^^

This property will allow the Studio user to set a property value which might be language specific.  This allows the application to render the proper text
based on the end user's language settings.

.. code-block:: javascript

  type: 'translatable-text'

Text
^^^^

A simple text property, which is not typically end-user visible (othreiwse translatable text is recomended).

.. code-block:: javascript

  type: 'text'

Color
^^^^^

Rather than setting a HEX or RGB color, use this property to enable the Stuiod User to use a color picker when setting a color, like background, text, or
header styles.

.. code-block:: javascript

  type: 'color'

Image
^^^^^

.. code-block:: javascript

  type: 'image-upload'

Checkbox
^^^^^^^^

.. code-block:: javascript

  type: 'checkbox'

Toggle
^^^^^^

.. code-block:: javascript

  type: 'toggle'

Dropdown
^^^^^^^^

.. code-block:: javascript

  type: 'dropdown',
  options: {
    'value1': 'Display Value',
    'value2': 'Display Value Too'
  }

Numeric
^^^^^^^

.. code-block:: javascript

  type: 'numeric',
  options: {
    'min': 0,
    'max': 99999
  }

Multiple Selection
^^^^^^^^^^^^^^^^^^

.. code-block:: python

  type: 'multi-select'

Page Link
^^^^^^^^^

Used to provide a link to another Tool included in the Experience, useful for navigation between Widgets.

.. code-block:: python

  type: 'page-link'

