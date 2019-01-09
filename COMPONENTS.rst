Component-Sets
--------------

Component-sets are bundled web components that are registered to be used by widgets.  Any web component, regardless of framework, upon upload can be
used by any widget via supplementing the distributable with a metadata file & proper tags.

Metadata
^^^^^^^^

A Component-set metadata can be defined via the components.json file which adheres to the following JSON structure:

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

The components.json file should be included within the root folder of the distributable that is uploaded to Lumavate.

.. include:: ../PROPERTIES.rst

