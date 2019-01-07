Component Sets
--------------

Component Sets are bundled webcomponents that are registered to be used by Widgets.  Any current web component, regardless of framework, can be registered for
used by Widgets via supplementing the distributable with a metadata file.

A Component Set metadata can be defined via the components.json file which adheres to the following JSON structure:

.. code-block:: javascript

  'label': 'Component Label',
  'icon': 'Relative path within the Distributable to an SVG icon for use in the Studio',
  'tags': ['Array of Tags which can be used within a Widget to denote where a Component can be used'],
  'type': 'Unique Label per Component',
  'properties':
  [  // Array of Properties to be shown within the Studio
    {
      'classification': 'Tab Name for which this property resides',
      'default': 'Default Value',
      'helpText': 'Help Text',
      'label': 'Display Label',
      'name': 'property1' //Property Name used in the Component',
      'options': {},
      'section': null,
      'type': 'Property Type: Text, Toggle, Image, Color, etc.'
    }
  ],
  'template': '<component-tag property1='{{componentData.property1}}'></component-tag>'

The components.json file should be included within the root folder of the dsitrubtable taht is uploaded to Lumavate.
