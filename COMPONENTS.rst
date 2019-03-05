.. _component-sets:

Component-Sets
--------------

Component-sets are bundled web components. For more information on web components, please consult `webcompoents.org <https://www.webcomponents.org/introduction>`_.  

Any component-set can be used by any widget or microservice immediately after upload as long as the proper tags are used. For widgets, these tags allow extra UI features and functionality to be used by multiple widgets. For microservices, these tags allow the component-set to compile and redistribute microservice information to other tools.

Component-sets cannot be used to create an experience without the presence of a widget. Instead, component-sets help by adding additional UI and functions that can be used by multiple tools.

Component-sets should be used when an application:
 * Provides client-side rendering and logic
 * Provides frequently used UI/UX tasks
 * Communicates information between multiple tools

.. _Accepted File Types C:

Accepted File Types
^^^^^^^^^^^^^^^^^^^

 Component-sets must be a **compressed zip file** in order to be uploaded to the Lumavate platform. 
 
 The compressed file needs to contain a metadata file named, component.json, written in JSON that defines the component-set :ref:`properties <properties>` and code. Optionally, the component-set code and resources can be split into multiple files. However, these files will need to be correctly referenced in the component.json's template and/or icon sections. 

 For more information about uploading tools to the platform, consult :ref:`Uploading A Tool`. 

.. _metadata:

Metadata
^^^^^^^^

 A Component-set's metadata defines general information for the component-set along with its properties via the component-set JSON file. For more information on properties and a list of property types, please consult the :ref:`Properties` page. 
 
 The component-sets JSON file must be included within the root folder of the distributable that is uploaded to Lumavate.
 
 The component-set file adheres to the following JSON structure:

  .. code-block:: javascript
     
     {
       "components": [
        {
         'label': 'Component Label',
         'icon': 'Relative path within the Distributable to an SVG icon that will be displayed when previewed in the Studio',
         'tags': ['Array of Tags which can be used within a widget or microservice to denote where a component-set can be used'],
         'type': 'Unique Label (each component-set needs its own unique label names)',
         'properties':
         [  
           {
             'classification': 'Tab name',
             'section': 'Section name',
             'help': 'Help text for the property. Use Markdown to add additonal formatting to the help text',
             'name': 'Property name which will be used to reference this property',
             'label': 'Property label',
             'type': 'Property type --see property page',
             'default': 'Default value',
             'label': 'Display label',
             'options': {},
           },
           {
           // Array of Properties to be shown within the studio
           }
         ],

         'template': '<component-tag property1='{{componentData.property1}}'></component-tag>'
        }
      ],
      "styleData": []  
     }
     
 The template defines the HTML that is output upon the component-sets use. The properties exposed can be substituted within the template using the templating syntax: ``{{ componentData.propertyName }}``. For instance, the template defined above will set the ``property1`` attribute to the value set within the platform.
