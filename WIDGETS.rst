Widgets
-------

A widget is a reusable web application component that can consist of one or more pages. It can be utilized across multiple Lumavate :ref: 'experiences'. For example, “Locator” is a standard widget. It provides a location service to its experiences.

Implementing API Endpoints
^^^^^^^^^^^^^^^^^^^^^^^^^^

Any widget developed for Lumavate must implement two key API endpoints, :ref: '**Discover**' and :ref: '**Render**'.
Each endpoint will contain dynamic parts that correspond to both the type of widget uploaded (denoted as widget_type), along with the logical location of the widget (denoted as integration_cloud). Both of these URI parts are in the form of a string & should be handled dynamically.

Required Endpoints
^^^^^^^^^^^^^^^^^^

All widgets require the following API endpoints:

1. DISCOVER

.. code-block:: python

  /<string:integration_cloud>/<string:widget_type>/discover/properties

This endpoint informs the platform which properties exist for the widget, via a JSON payload of an array of properties. The platform automatically adds a few platform level properties outside of this endpoint. However, a majority of a widget's properties are contained in the endpoint. An empty set should be sent if the widget does not require any properties.

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

This endpoint is called when the widget renders itself either for preview or production. This is the core endpoint that produces the UI for the widget.


Optional Endpoints
^^^^^^^^^^^^^^^^^^

* ON_CREATE_VERSION

.. code-block:: python

  /<string:integration_cloud>/<string:widget_type>/instances/<int:instance_id>/on-create-version

This endpoint is called BEFORE the properties are saved within the Lumavate :ref: 'studio'. This allows the developer to modify and/or override property data before saving.


* AFTER_CREATE_VERSION

.. code-block:: python

  /<string:integration_cloud>/<string:widget_type>/instances/<int:instance_id>/after-create-version

This endpoint is called AFTER the properties are saved within the Lumavate :ref: 'studio'. This allows the developer to adjust property data after saving.
