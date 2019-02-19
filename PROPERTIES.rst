.. _Properties:

Properties
----------

The Discover endpoint enables the developer to expose configurable settings through the Lumavate :ref:`studio <studio>`, by returning an array of properties via JSON.

A property is defined by denoting the tab name, section name, help text, property name, property label, default value, and property type using the following JSON structure:

.. code-block:: javascript

  var property = {
    'classification': 'Tab name',
    'section': 'Section name',
    'help': 'Help text for the property. Use Markdown to provide additional formatting.',
    'name': 'Property name. Use this when referencing the property.',
    'label': 'Property label. The name of the field shown in the studio.',
    'default': 'Default value'
    'type': 'Property type. For a complete list of supported properties, see below.'
  }

The following list of types can be implemented by including the appropriate JSON in the Discover endpoint.

Properties Index:
 #. :ref:`Translatable Text`
 #. :ref:`Text`
 #. :ref:`Color`
 #. :ref:`Image`
 #. :ref:`Checkbox`
 #. :ref:`Toggle`
 #. :ref:`Dropdown`
 #. :ref:`Numeric`
 #. :ref:`Multiple Selection`
 #. :ref:`Page Link`

________________________________________________________________________________________________________________________________________

.. _Translatable Text:

Translatable Text
^^^^^^^^^^^^^^^^^

 Translatable Text allows :ref:`studio <studio>` users to set a language specific text value. The application will then render the proper text based on the end user's language settings.

 .. code-block:: javascript

    type: 'translatable-text'

________________________________________________________________________________________________________________________________________

.. _Text:

Text
^^^^

 Text allows :ref:`studio <studio>` users to set a text value.

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

 Color allows :ref:`studio <studio>` users to set a color value via a color picker.

 .. code-block:: javascript

    type: 'color'

________________________________________________________________________________________________________________________________________

.. _Image:

Image
^^^^^

 Image allows :ref:`studio <studio>` users to upload an image.

 .. code-block:: javascript

    type: 'image-upload'

________________________________________________________________________________________________________________________________________

.. _Checkbox:

Checkbox
^^^^^^^^

 Checkbox allows :ref:`studio <studio>` users to set a boolean value by checking a checkbox.

 .. code-block:: javascript

    type: 'checkbox'

________________________________________________________________________________________________________________________________________

.. _Toggle:

Toggle
^^^^^^

 Toggle allows :ref:`studio <studio>` users to set a boolean value by toggling a toggle on or off.

 .. code-block:: javascript

    type: 'toggle'

________________________________________________________________________________________________________________________________________

.. _Dropdown:

Dropdown
^^^^^^^^

 Dropdown allows :ref:`studio <studio>` users to select a **single** value from a list of options.

 .. code-block:: javascript

   type: 'dropdown',
   options: {
     'value1': 'Option One',
     'value2': 'Option Two'
   }

________________________________________________________________________________________________________________________________________

.. _Numeric:

Numeric
^^^^^^^

 Numeric allows :ref:`studio <studio>` users to enter a numeric value. Numeric accepts decimals as input. A min and max range can be set.

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

 Multiple selection allows :ref:`studio <studio>` users to select **multiple** values from a list of options.

 .. code-block:: python

    type: 'multi-select'
    options: {
     'value1': 'Option One',
     'value2': 'Option Two'
   }

________________________________________________________________________________________________________________________________________

.. _Page Link:

Page Link
^^^^^^^^^

 Page Link allows :ref:`studio <studio>` users to link to another URL by either selecting a :ref:`widget <widgets>` from the current :ref:`experience <experiences>` or by typing in a URL.

 .. code-block:: python

    type: 'page-link' 
