.. _component-sets:

Component-Sets
--------------

Component-sets are bundled web components that can be registered for use by widgets and microservices within experiences. For more information on web components, please consult `webcompoents.org <https://www.webcomponents.org/introduction>`_.  

Any component-set upon upload, regardless of framework, can be used by any widget or microservice via supplementing the distributable with a metadata file and proper tags. For widgets, these tags allow extra UI features and functionality to be distributed across multiple widgets. For microservices, these tags allow the component-set to compile and redistribute microservice information to other tools.

Component-sets cannot be used to create an experience without the presence of a widget. Instead, component-sets help by adding additional UI and functions that can be used by multiple tools.

Component-sets should be used when an application:
 * Provides client-side rendering and logic
 * Provides frequently used UI/UX tasks
 * Communicates information between multiple tools

.. _Accepted File Types C:

Accepted File Types
^^^^^^^^^^^^^^^^^^^

 Component-sets must be a **compressed zip file** in order to be uploaded to the Lumavate platform. The compressed file needs to contain a schema file written in JSON that defines what the component-sets :ref:`properties <properties>` are and a file with the actual distributable web component. 

 For more information about uploading tools to the platform, consult :ref:`Uploading A Tool`. 

.. _metadata:

Metadata
^^^^^^^^

 A Component-set's metadata defines general information for the component-set along with its properties via the component-set JSON file. For more information on properties and a list of property types, please consult the :ref:`Properties` page. 
 
 The component-sets JSON file must be included within the root folder of the distributable that is uploaded to Lumavate.
 
  
  The component-set file adheres to the following JSON structure:

  .. code-block:: javascript

     'label': 'Component Label',
     'icon': 'Relative path within the Distributable to an SVG icon that will be displayed when previewed in the Studio',
     'tags': ['Array of Tags which can be used within a widget or microservice to denote where a component-set can be used'],
     'type': 'Unique Label (each component-set needs its own unique label names)',
     'properties':
     [  
       {
         'section': 'Section name',
         'help': 'Help text for the property. Use Markdown to add additonal formatting to the help text',
         'name': 'Property name which will be used to reference this property',
         'label': 'Property label',
         'type': 'Property type --see property page',
         'default': 'Default value',
         'label': 'Display label',
         'options': {},
       },
       // Array of Properties to be shown within the studio
     ],
     
     'template': '<component-tag property1='{{componentData.property1}}'></component-tag>'

 The template field is special as it must be written in HTML. The template field defines what the component-set will do when it is displayed in the preview or in production. Properties that are exposed can be substituted with the studio users input within the template using the templating syntax. 
 
 For instance, a property field labeled ``property`` would send the studio users input for that property to the template by writing ``{{ componentData.property }}``.
