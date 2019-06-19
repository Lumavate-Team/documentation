.. _component-sets:

Component Sets
--------------

Component sets are bundled web components. For more information on web components, please consult `webcomponents.org <https://www.webcomponents.org/introduction>`_.  

Any component set can be used by any widget or microservice immediately after upload as long as the proper tags are used. For widgets, these tags add extra UI features and functionality. For microservices, these tags allow the component set to compile and redistribute microservice information to other tools.

Component sets cannot be used to create an experience without the presence of a widget. Instead, component sets help by adding additional UI and functions that can be used by multiple tools.

Component sets should be used when an application:
 * Provides client-side rendering and logic
 * Provides frequently used UI/UX tasks
 * Communicates information between multiple tools

.. _Accepted File Types C:

File Requirements
^^^^^^^^^^^^^^^^^

 Component sets must be a **compressed zip file** in order to be uploaded to the Lumavate platform. 
 
 The compressed file needs to contain a metadata file named component.json in the root folder of the zip file that is uploaded to Lumavate. The component.json file must be written in JSON and define the component set :ref:`properties <properties>` and code. 
 
 Optionally, the component set code and resources can be split into multiple files. However, these files will need to be correctly referenced in the component.json's template and/or icon sections. 

 For more information about uploading tools to the platform, consult :ref:`Uploading A Tool`. 

.. _metadata:

Metadata File
^^^^^^^^^^^^^

 A Component set's metadata defines general information for the component set along with its properties via the component set JSON file. For more information on properties and a list of property types, please consult the :ref:`Properties` page. 
 
 The component set file adheres to the following JSON structure:

  .. code-block:: javascript
     
     {
       "components": [
        {
         "label": "Name of the component in the studio.",
         "icon": "Relative path within the zip file to an SVG icon that will accompany the component in the studio.",
         "tags": ["Array of Dynamic component Values used within widget and microservices to denote where the component set can be used. A current list of Lumavate tags can be found below."],
         "type": "Used when referencing the component. This must be a unique value that is different from all other component types in the command center.",
         "properties":
         [  
           {
             "classification": "Tab name",
             "section": "Section name",
             "helpText": "Help text for the property. Use Markdown to add additional formatting to the help text",
             "name": "Property name which will be used to reference this property",
             "label": "Property label",
             "type": "Property type --see property page",
             "default": "Default value",
             "label": "Display label",
             "options": {},
           },
           {
             // Array of component properties. 
             // These properties only apply to this component.
             // Will be shown when this component is added to a compatible widget or microservice in the studio.
           }
         ],
         
         "template": "<component-tag property1='{{componentData.propertyName}}'></component-tag><Additional template information can be found below.>"
        },
        {
          // Array of components. 
          // Will be a selectable option within compatible widgets or microservices in the studio.
        }
      ],
      "styleData": 
      [
        {
          "classification": "Tab name",
          "section": "Section name",
          "helpText": "Help text for the property. Use Markdown to add additional formatting to the help text",
          "name": "Property name which will be used to reference this property",
          "label": "Property label",
          "type": "Property type --see property page",
          "default": "Default value",
          "label": "Display label",
          "options": {}
        },
        {
          // Array of component set properties. 
          // These properties will apply to all components.
          // Will be shown within the component set designer page in the studio.
        }
      ]  
     }
 
 Templates are the HTML code that is implemented when the component is used. Each component within the component set requires its own template. 
 
 To call the properties that the studio user sets, use the templating syntax, ``{componentData.propertyName}``, where ``propertyName`` is the name of the property whose value you want to use. Components can only call properties that are under their component section or under the styleData section. 

 .. note::
    The template section supports jinja.
 
 The current tags available are:
 	- ``body`` adds GUI that the end user will interact with and the studio user can place anywhere on the page. Normally you can add multiple of the same component.
 	- ``model`` adds elements that appear in a specific spot on the page. Normally you would only add one of the same components.
 	- ``logic`` adds logic code that takes specific actions when certain criteria are met. Normally you would only add one of the same components.
 	- ``footer`` adds a footer.
 	- ``header`` adds a header.
 	- ``STRING`` can create a custom tag by adding a string value that is not listed above to the tag array. Be aware that a widget or microservice will need to be designed that calls the new dynamic component before the component can be used in the studio.  
