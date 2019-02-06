.. _widgets:

Widgets
-------

A widget is a reusable web application hosted within a Docker container. 

Widgets can consist of one or more pages that perform a specific function. There are times when a widget will require another :ref:`tool<tools>` to provide any solid functionality, but they should always strive to be self-contained, stand-alone applications. 

An experience cannot be created without the presence of at least one widget. Widgets are the backbone of an :ref:`experience<experiences>` allowing the user to create customizable experiences with specific functionality.  
 
Widgets should be used when the application:
 * Requires server-side hosted code
 * Implements multilabel pages
 * Contains stand-alone function with accompanying UI 

.. _Accepted File Typesw:

Accepted File Types
^^^^^^^^^^^^^^^^^^^ 

Widgets need to be either a **gzip** or **tar** file in order to be upload to the Lumavate platform. 

For more information about uploading tools to the platform, consult :ref:`Uploading A Tool`. 

.. _API Endpoints W:

Implementing API Endpoints
^^^^^^^^^^^^^^^^^^^^^^^^^^

Any widget developed for Lumavate must implement two key API endpoints, **Discover** and **Render**.

Each endpoint will contain dynamic parts that correspond to both the type of widget uploaded (denoted as widget_type) and the logical location of the widget (denoted as integration_cloud). Both of these URI parts are in the form of a string and should be handled dynamically.

Required Endpoints
++++++++++++++++++

All widgets require the following API endpoints:

1. DISCOVER

.. code-block:: python

  /<string:integration_cloud>/<string:widget_type>/discover/properties

This endpoint informs the platform which properties exist for the widget, via a JSON payload of an array of properties. The platform automatically adds a few platform level properties outside of this endpoint. An empty set should be sent if the widget does not require any properties.

**Sample Response**

.. code-block::  rest

  METHOD: GET
  CONTENT-TYPE: application/json
  RESPONSE:
    {
      "payload": {
        "data": [
          {
            "classification": "General",
            "default": false,
            "helpText": "",
            "label": "Display Background Image",
            "name": "displayBackgroundImage",
            "section": "Settings",
            "type": "toggle"
          },
          {
            "classification": "General",
            "helpText": "",
            "label": "Background Image",
            "name": "backgroundImage",
            "section": "Settings",
            "type": "image-upload"
          }
        ]
      }
    }

2. RENDER

.. code-block:: python

  /<string:integration_cloud>/<string:widget_type>

This endpoint is called when the widget renders itself either for preview or production. This is the core endpoint that produces the end user UI for the widget.


Optional Endpoints
++++++++++++++++++

* ON_CREATE_VERSION

.. code-block:: python

  /<string:integration_cloud>/<string:widget_type>/instances/<int:instance_id>/on-create-version

This endpoint is called BEFORE the properties are saved within the Lumavate :ref:`studio <studio>`. This allows the developer to modify and/or override property data before saving.


* AFTER_CREATE_VERSION

.. code-block:: python

  /<string:integration_cloud>/<string:widget_type>/instances/<int:instance_id>/after-create-version

This endpoint is called AFTER the properties are saved within the Lumavate :ref:`studio <studio>`. This allows the developer to adjust property data after saving.
