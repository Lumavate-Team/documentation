.. _properties:

Properties
----------

The Discover endpoint enables the ability to expose configurable settings through the Lumavate studio, by returning an array of properties via JSON.

A property is defined by denoting the tab, section, help text, name, label, & type using the following JSON structure:

.. code-block:: javascript

  var property = {
    'classification': 'Tab name',
    'section': 'Section name',
    'help': 'Help text for the property.  Use Markdown to provide additional help to the studio user',
    'name': 'Property name which will be used to reference this property',
    'label': 'Property label',
    'default': 'Default value'
    'type': 'Property type - see below'
  }

The following list of types are available & can be implemented by including the appropriate JSON in the Discover endpoint.

* :ref:`Translatable Text`
* :ref:`Text`
* :ref:`Color`
* :ref:`Image`
* :ref:`Checkbox`
* :ref:`Toggle`
* :ref:`Dropdown`
* :ref:`Numeric`
* :ref:`Multiple Selection`
* :ref:`Page Link`

________________________________________________________________________________________________________________________________________

.. _Translatable Text:

Translatable Text
^^^^^^^^^^^^^^^^^

 Translatable Text allows the studio user to set a lanugage specific property value.  The application will then render the proper text
based on the end user's language settings.

 .. code-block:: javascript

    type: 'translatable-text'

________________________________________________________________________________________________________________________________________

.. _Text:

Text
^^^^

 Text allows studio users to set a text-only value.

 .. code-block:: javascript

   type: 'text',
   options: {
     'readonly': true || false - defaults to true,
     'rows': 0 - Modify the text box to a text area
   }

________________________________________________________________________________________________________________________________________

.. _Color:

Color
^^^^^

 Color allows studio users to set a color via a color picker rather than setting a HEX or RGB color value.

 .. code-block:: javascript

    type: 'color'

________________________________________________________________________________________________________________________________________

.. _Image:

Image
^^^^^

 Image allows a studio user to upload an image.

 .. code-block:: javascript

    type: 'image-upload'

________________________________________________________________________________________________________________________________________

.. _Checkbox:

Checkbox
^^^^^^^^

 Checkbox allows studio users to set a boolean value by checking a checkbox

 .. code-block:: javascript

    type: 'checkbox'

________________________________________________________________________________________________________________________________________

.. _Toggle:

Toggle
^^^^^^

 Toggle allows studio users to set a boolean value between "on" and "off".

 .. code-block:: javascript

    type: 'toggle'

________________________________________________________________________________________________________________________________________

.. _Dropdown:

Dropdown
^^^^^^^^

 Dropdown presents studio users with a list of options. The user is able to select a single value.

 .. code-block:: javascript

   type: 'dropdown',
   options: {
     'value1': 'Display Value',
     'value2': 'Display Value Two'
   }

________________________________________________________________________________________________________________________________________

.. _Numeric:

Numeric
^^^^^^^

 Numeric allows studio user to enter numeric values.  Numeric properties can be represented as a decimal and a min and max range can be set.

 .. code-block:: javascript

   type: 'numeric',
   options: {
     'min': 0,
     'max': 99999
   }

________________________________________________________________________________________________________________________________________

.. _Multiple Selection:

Multiple Selection
^^^^^^^^^^^^^^^^^^

 Multiple selection presents studio users with a list of options. The user is able to select multiple options.

 .. code-block:: python

    type: 'multi-select'

________________________________________________________________________________________________________________________________________

.. _Page Link:

Page Link
^^^^^^^^^

 Page Link allows studio users to link to another URL by either selecting a Widget from the current Experience or typing in an external URL.

 .. code-block:: python

    type: 'page-link'
