.. _component-sets:

Component-Sets
--------------

Component-sets are bundled web components that are registered to be used by :ref:`widgets <widgets>` and :ref:`microserivces <microservices>`. Any web component upon upload, regardless of framework, can be used by any widget via supplementing the distributable with a metadata file and proper tags. Component-sets can also compile and redistribute microservice information when properly configured. 

.. _metadata:

Metadata
^^^^^^^^

A Component-set's metadata can be defined via the component-sets JSON file which adheres to the following JSON structure:

.. code-block:: javascript

   'label': 'Component Label',
   'icon': 'Relative path within the Distributable to an SVG icon for use in the Studio',
   'tags': ['Array of Tags which can be used within a Widget to denote where a Component can be used'],
   'type': 'Unique Label per Component',
   'properties':
   [  // Array of Properties to be shown within the studio
     {
       'classification': 'Tab name',
       'section': 'Section name',
       'help': 'Help text for the property.  Use Markdown to provide additional help to the studio user',
       'name': 'Property name which will be used to reference this property',
       'label': 'Property label',
       'type': 'Property type - see below'
       'default': 'Default value',
       'label': 'Display label',
       'options': {},
     }
   ],
   'template': '<component-tag property1='{{componentData.property1}}'></component-tag>'

The teamplate defines the HTML that is output upon use. The properties exposed can be substituted within the template using the templating syntax. For instance, the template defined above will set the `property1` attribute to the value set within the platform.

.. code-block:: javascript

   {{ componentData.propertyName }}

The component-sets JSON file must be included within the root folder of the distributable that is uploaded to Lumavate.
