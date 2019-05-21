.. _widgets:

Widgets
-------

Widgets are reusable web applications hosted within a Docker container. 

Widgets can consist of one or more pages that perform a stand-alone function. There are times when a widget will require another tool to provide any solid functionality, but they should always strive to be self-contained, stand-alone applications. 

Widgets are the backbone of an experience providing studio users with a customizable UI and/or functionality. An experience cannot be created without the presence of at least one widget.  
 
Widgets should be used when the application:
 * Requires server-side hosted code
 * Implements multiple pages
 * Contains a stand-alone function with accompanying UI
 
.. note::
    Widgets can function as shells for microservices or component-sets providing a convenient place for studio users to customize the UI. These widgets can then be used to create web pages or data displays.
    
.. warning::
    All widgets that make platform level calls must send their URI signed. Lumavate provides signing libraries for Go, Python, and #C. All other containers will be unable to send signed URIs. :ref:`Visit the sample code section for a link to each of these signed libraries <Code Samples>`. 

.. _Accepted File Types W:

File Requirements
^^^^^^^^^^^^^^^^^

 Widgets need to be either a **gzip** or **tar** file in order to be uploaded to the Lumavate platform. 

 For more information about uploading tools to the platform, consult :ref:`Uploading A Tool`. 
 
 There is no required file names or structure. A widget is only required to define two endpoints: Discover and Render.

.. _API Endpoints W:

Implementing API Endpoints
^^^^^^^^^^^^^^^^^^^^^^^^^^

 Any widget developed for Lumavate must implement two key API endpoints, **Discover** and **Render**.
 
 All endpoint will contain two dynamic parts and a route:
  
  * The first part corresponds to the logical location of the widget denoted as ``integration_cloud``. 
  
  * The second part corresponds to the type of widget uploaded denoted as ``widget_type``. 

    .. code-block:: python
   
       /<string:integration_cloud>/<string:widget_type>/<route>
   
  Some endpoints will also contain a specific instance of the widget denoted by ``instance_id``.
  
    .. code-block:: python
  
       /<string:integration_cloud>/<string:widget_type>/instances/<int:instance_id>/<route>

Required Endpoints
++++++++++++++++++

 All widgets require the following API endpoints:

 #. DISCOVER

    This endpoint informs the platform via JSON which :ref:`properties <properties>` exist for the widget. The platform automatically adds a few platform level properties outside of this endpoint. An empty data set should be sent if the widget does not require any properties.

     .. code-block:: python

       /<string:integration_cloud>/<string:widget_type>/discover/properties

    Properties need to be written in the following format:

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
    
    .. Tip::
      Lumavate provides property libraries for Go, Python, and C# that allow properties to be written in alternate formats that better match those languages normal style. For the property libraries as well as example containers that use them, :ref:`please consult the sample code section<Code Samples>`.
       
 #. RENDER

    This endpoint is called when the widget renders itself for preview and production. This is the core endpoint that produces the end user UI for the widget.
   
     .. code-block:: python

        /<string:integration_cloud>/<string:widget_type>


Optional Endpoints
++++++++++++++++++

 * ON_CREATE_VERSION
  
   This endpoint is called **before** the properties are saved within the Lumavate studio. This allows the developer to modify and/or override property data before saving.

   .. code-block:: python

      /<string:integration_cloud>/<string:widget_type>/instances/<int:instance_id>/on-create-version


 * AFTER_CREATE_VERSION
  
   This endpoint is called **after** the properties are saved within the Lumavate studio. This allows the developer to adjust property data after saving.

   .. code-block:: python

      /<string:integration_cloud>/<string:widget_type>/instances/<int:instance_id>/after-create-version
     
