.. _microservices:

Microservices
-------------

Microservices are container-based applications hosted inside a Docker container. 

Microservices provided additional behind-the-scenes functions within :ref:`experiences <experiences>`. However, microservices rarely have their own UI. Instead, they add UI functionality to :ref:`widgets<widgets>` through the use of :ref:`component-sets<component-sets>`. 

Microservices cannot be used to create a unique experience without the addition of a widget. They, instead, assist widgets by adding additional logic and/or data access to an experience. 

Microservices should be used when an application:
 * Delivers access to an external API
 * Provides authentication or authorization to a widget
 * Uses or provides access to a database 

.. _Accepted File Typesm:

Accepted File Types
^^^^^^^^^^^^^^^^^^^

Microservices need to be either a **gzip** or **tar** file in order to be upload to the Lumavate platform. 

For more information about uploading tools to the platform, consult :ref:`Uploading A Tool`. 

.. _API Endpoints M:

Implementing API Endpoints
^^^^^^^^^^^^^^^^^^^^^^^^^^

Any microservice developed for Lumavate must implement two key API endpoints, **Discover** and **Render**.

Each endpoint will contain dynamic parts that correspond to both the type of microservice uploaded (denoted as service_type) and the logical location of the microservice (denoted as integration_cloud). Both of these URI parts are in the form of a string and should be handled dynamically.

Required Endpoints
++++++++++++++++++

All microservices require the following API Endpoints:

1. DISCOVER

.. code-block:: python

  /<string:integration_cloud>/<string:service_type>/discover/properties

This endpoint informs the platform which properties exist for the microservice, via a JSON payload of an array of properties. The platform automatically adds a few platform level properties outside of this endpoint. An empty set should be sent if the microservice does not require any properties.

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

  /<string:integration_cloud>/<string:service_type>

This endpoint is called when the microservice renders itself for preview. If the microservice does not have a UI, a default image should be sent.


Optional Endpoints
++++++++++++++++++

* ON_CREATE_VERSION

.. code-block:: python

  /<string:integration_cloud>/<string:service_type>/instances/<int:instance_id>/on-create-version

This endpoint is called BEFORE the properties are saved within the Lumavate studio. This allows the developer to modify and/or override any property data before saving.


* AFTER_CREATE_VERSION

.. code-block:: python

  /<string:integration_cloud>/<string:service_type>/instances/<int:instance_id>/after-create-version

This endpoint is called AFTER the properties are saved within the Lumavate studio. This allows the developer to adjust any property data after saving.
