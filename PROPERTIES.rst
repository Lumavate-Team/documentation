Properties
^^^^^^^^^^

The Discover endpoint enables the ability to expose properties through the Lumavate Studio, by returning an array of properties via JSON.
Each property is defined by denoting the tab, section, name, & label using the following JSON structure:

.. code-block:: javascript

  var property = {
  'classification': 'Tab Name',
  'section': 'Section Name',
  'help': 'Help text for the property.  Use Markup to provide additional help to the Studio User',
  'name': 'Property Name which will be used to reference this property',
  'label': 'Property Label',
  'type': 'Property Type - see below'
  }

The following list of properties are available & can be implemented by including the appropriate JSON in the Discover endpoint.

* Translatable Text
* Text
* Color
* Image
* Checkbox
* Toggle
* Dropdown
* Numeric
* Multiple Selection
* Page Link

**Translatable Text**

This property will allow the Studio user to set a property value which might be language specific.  This allows the application to render the proper text
based on the end user's language settings.

.. code-block:: javascript

  type: 'translatable-text'

**Text**

A simple text property, which is not typically end-user visible (othreiwse translatable text is recomended).

.. code-block:: javascript

  type: 'text',
  options: {
    'readonly': true || false - defaults to true,
    'rows': 0 - Modify the text box to a text area
  }

**Color**

Rather than setting a HEX or RGB color, use this property to enable the Stuiod user to use a color picker when setting a color, like background, text, or
header styles.

.. code-block:: javascript

  type: 'color'

**Image**

The ability to store an image as a property of a Tool.  This is useful when doing image recognition, branding, and/or personalization.

.. code-block:: javascript

  type: 'image-upload'

**Checkbox**

Present the Studio user with a checkbox option, which is useful when the value of the property is pre-defined & only selectable by the Studio user.

.. code-block:: javascript

  type: 'checkbox'

**Toggle**

A boolean property type useful when detemrining if a property should be "on" or "off".

.. code-block:: javascript

  type: 'toggle'

**Dropdown**

A list of options from which a Studio user can choose a single value.

.. code-block:: javascript

  type: 'dropdown',
  options: {
    'value1': 'Display Value',
    'value2': 'Display Value Too'
  }

**Numeric**

Numeric properties can be represented as a decimal, however also give the option to set a min & max range.

.. code-block:: javascript

  type: 'numeric',
  options: {
    'min': 0,
    'max': 99999
  }

**Multiple Selection**

Multiple selection will allow the studio user to select from a list of options, which will be returned as an array for use later.

.. code-block:: python

  type: 'multi-select'

**Page Link**

Used to provide a link to another Tool included in the Experience, useful for navigation between Widgets.

.. code-block:: python

  type: 'page-link'

