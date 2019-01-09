Microservices
-------------

Implementing Microservice API Endpoints
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Every widget developed to be registered within Lumavate must implement two key API endpoints.
Each endpoint will contain dynamic parts that correspond to both the type of widget uploaded (denoted as widget_type), along with the logical location of the
widget itself (denoted as integration_cloud).  Both of these URI parts are in the form of a string & should be consumed dynamically.

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

.. include:: ../PROPERTIES.rst
