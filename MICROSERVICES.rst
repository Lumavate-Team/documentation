Microservices
-------------

Microservices are container-based applications used within Experiences. A Microservice is intended to be a behind-the-scenes addition to an Experience, providing additional business logic and/or data access to an Experience.

Implementing API Endpoints
^^^^^^^^^^^^^^^^^^^^^^^^^^

Any microservice developed for Lumavate must implement two key API endpoints, **Discover** and **Render**.
Each endpoint will contain dynamic parts that correspond to both the type of microservice uploaded (denoted as service_type), along with the logical location of the
microservice (denoted as integration_cloud).  Both of these URI parts are in the form of a string & should be handled dynamically.

Required Endpoints
^^^^^^^^^^^^^^^^^^

All microservices require the following API Endpoints:

1. DISCOVER

.. code-block:: python

  /<string:integration_cloud>/<string:service_type>/discover/properties

This endpoint informs the platform of which properties exist for the microservice, via a JSON payload of an array of [properties](#PROPERTIES). The platform automatically adds a few platform level properties outside of this endpoint. An empty set should be sent if the microservice does not require any properties.

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

  /<string:integration_cloud>/<string:service_type>

This endpoint is called when the microservice renders itself for preview.


Optional Endpoints
^^^^^^^^^^^^^^^^^^

* ON_CREATE_VERSION

.. code-block:: python

  /<string:integration_cloud>/<string:widget_type>/instances/<int:instance_id>/on-create-version

This endpoint is called BEFORE the properties are saved within the Lumavate studio. This allows the developer to modify and/or override any property data before saving.


* AFTER_CREATE_VERSION

.. code-block:: python

  /<string:integration_cloud>/<string:widget_type>/instances/<int:instance_id>/after-create-version

This endpoint is called AFTER the properties are saved within the Lumavate studio. This allows the developer to adjust any property data after saving.
