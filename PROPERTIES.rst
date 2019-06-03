.. _Properties:

Properties
----------

The Discover endpoint enables the developer to expose configurable settings through the Lumavate studio, by returning an array of properties via JSON.


A property can have a tab name, section name, help text, property name, property label, default value, and property type all defined using the following JSON structure:

.. code-block:: javascript

  var property = {
    'classification': 'Tab name. The name of the tab the property field is under in the studio.',
    'section': 'Section name. The name of the section the property field is located in the studio.',
    'helpText': 'Help text for the property. Use Markdown to provide additional formatting.',
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
 #. :ref:`Theme Color`
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

 Translatable text allows studio users to set a language specific text value. The application will then render the proper text based on the end user's language settings.

 .. code-block:: javascript

    "classification": "Classification",
    "name": "Name",
    "type": "translated-text"
 
 .. figure:: ../images/translatedtextfield.PNG
       :align: center
       :width: 400px
       :alt: Image of a translatable text field.
      
       ..
       
 Required Fields:
  * ``"classification": "STRING"`` (only available for widgets and microservices)
  * ``"name": "STRING"``
  * ``"type": "translated-text"``
  
 Optional Fields:
  * ``"section": "STRING"``
  * ``"helpText": "STRING with Markdown"``
  * ``"label": "STRING"``
  * ``"default": "STRING"`` (does not have a default)
  * ``"options": {OPTIONS}`` 
   * ``"readonly": true || false`` (defaults to false)
   * ``"rows": INTEGER`` (the studio displays the number of rows specified, defaults to 1)
    
________________________________________________________________________________________________________________________________________

.. _Text:

Text
^^^^

 Text allows studio users to set a text value.

 .. code-block:: javascript

      "classification": "Classification",
      "name": "Name",
      "type": "text"

 .. figure:: ../images/textfield.PNG
       :align: center
       :width: 700px
       :alt: Image of a text field.
      
       ..
       
Required Fields:
  * ``"classification": "STRING"`` (only available for widgets and microservices)
  * ``"name": "STRING"``
  * ``"type": "text"``
  
 Optional Fields:
  * ``"section": "STRING"``
  * ``"helpText": "STRING with Markdown"``
  * ``"label": "STRING"``
  * ``"default": "STRING"`` (does not have a default)
  * ``"options": {OPTIONS}``
   * ``"readonly": true || false`` (defaults to false)
   * ``"rows": INTEGER`` (the studio displays the number of rows specified, defaults to 1)

_______________________________________________________________________________________________________________________________________

.. _Color:

Color
^^^^^

 Color allows studio users to set a color value via a color picker.

 .. code-block:: javascript

    "classification": "Classification",
    "name": "Name",
    "type": "color"
  
 .. figure:: ../images/colorfield.PNG
       :align: center
       :width: 600px
       :alt: Image of a color field.
      
       ..
       
 Required Fields:
  * ``"classification": "STRING"`` (only available for widgets and microservices)
  * ``"name": "STRING"``
  * ``"type": "color"``
  
 Optional Fields:
  * ``"section": "STRING"``
  * ``"helpText": "STRING with Markdown"``
  * ``"label": "STRING"``
  * ``"default": "STRING"`` (defaults to #fff/white)
  
 .. warning::
    The tool will error when used in the studio if the default field contains an invalid value.
    
_______________________________________________________________________________________________________________________________________

.. _Theme Color:

Theme Color
^^^^^^^^^^^

 Color allows studio users to set a color value via a theme color picker.  The theme color picker will use all the color properties defined within a Component
 Set, including a gradient scale of any properties that are identified as color families.

 .. code-block:: javascript

    "classification": "Classification",
    "name": "Name",
    "type": "theme-color"
  
 .. figure:: ../images/colorfield.PNG
       :align: center
       :width: 600px
       :alt: Image of a color field.
      
       ..
       
 Required Fields:
  * ``"classification": "STRING"`` (only avaliable for widgets and microservices)
  * ``"name": "STRING"``
  * ``"type": "theme-color"``
  
 Optional Fields:
  * ``"section": "STRING"``
  * ``"helpText": "STRING with Markdown"``
  * ``"label": "STRING"``
  * ``"deafult": "STRING"`` (defaults to #fff/white)
  
 .. warning::
    The tool will error when used in the studio if the default field contains an invalid value.
    
________________________________________________________________________________________________________________________________________

.. _Image:

Image
^^^^^

 Image allows studio users to upload an image.

 .. code-block:: javascript

    "classification": "Classification",
    "name": "Name",
    "type": "image-upload"
 
 .. figure:: ../images/imagefield.PNG
       :align: center
       :width: 600px
       :alt: Image of a image upload field.
      
       ..
       
 Required Fields:
  * ``"classification": "STRING"`` (only available for widgets and microservices)
  * ``"name": "STRING"``
  * ``"type": "image-upload"``
  
 Optional Fields:
  * ``"section": "STRING"``
  * ``"helpText": "STRING with Markdown"``
  * ``"label": "STRING"``
  
 .. note::
        The platform will set the default image to a No Image PNG file. At the current moment, there is no way to change this default image.
    _______________________________________________________________________________________________________________________________________

.. _Checkbox:

Checkbox
^^^^^^^^

 Checkbox allows studio users to set a boolean value by checking a checkbox.

 .. code-block:: javascript

    "classification": "Classification",
    "name": "Name",
    "type": "checkbox"
 
 .. figure:: ../images/checkboxfield.PNG
       :align: center
       :width: 700px
       :alt: Image of a checkbox field.
      
       ..
       
 Required Fields:
  * ``"classification": "STRING"`` (only available for widgets and microservices)
  * ``"name": "STRING"``
  * ``"type": "checkbox"``
  
 Optional Fields:
  * ``"section": "STRING"``
  * ``"helpText": "STRING with Markdown"``
  * ``"label": "STRING"``
  * ``"default": true || false`` (defaults to false)
  
________________________________________________________________________________________________________________________________________

.. _Toggle:

Toggle
^^^^^^

 Toggle allows studio users to set a boolean value by toggling a toggle on or off. Toggle is the default property type if an invalid type is used.

 .. code-block:: javascript

    "classification": "Classification",
    "name": "Name",
    "type": "toggle"
 
 .. figure:: ../images/togglefield.PNG
       :align: center
       :width: 600px
       :alt: Image of a toggle field.
      
       ..
       
 Required Fields:
  * ``"classification": "STRING"`` (only available for widgets and microservices)
  * ``"name": "STRING"``
  * ``"type": "toggle"``
  
 Optional Fields:
  * ``"section": "STRING"``
  * ``"helpText": "STRING with Markdown"``
  * ``"label": "STRING"``
  * ``"default": true || false`` (defaults to false)
  
________________________________________________________________________________________________________________________________________

.. _Dropdown:

Dropdown
^^^^^^^^

 Dropdown allows studio users to select a **single** value from a list of options.

 .. code-block:: javascript

   
    "classification": "Classification",
    "name": "Name",
    "options":{
         "option1 name":"label",
         "option2 name":"label"
    },
    "type": "dropdown"
 
 .. figure:: ../images/dropdownfield.PNG
       :align: center
       :width: 600px
       :alt: Image of a dropdown field.
      
       .. 
       
 Required Fields:
  * ``"classification": "STRING"`` (only available for widgets and microservices)
  * ``"name": "STRING"``
  * ``"options": {OPTIONS}`` (at least one option must be added to the options field)
  
   * ``"NAME STRING":"LABEL STRING"`` (name is used to reference the option, label is what studio users see in the dropdown field)
   
  * ``"type": "dropdown"``
  
 Optional Fields:
  * ``"section": "STRING"``
  * ``"helpText": "STRING with Markdown"``
  * ``"label": "STRING"``
  * ``"default": "Option Name"`` (does not have a default)

________________________________________________________________________________________________________________________________________

.. _Numeric:

Numeric
^^^^^^^

 Numeric allows studio users to enter a numeric value. Numeric accepts decimals as input.

 .. code-block:: javascript

    "classification": "Classification",
    "default": 34,
    "name": "Name",
    "options": {},
    "type": "numeric"
 
 .. figure:: ../images/numricfield.PNG
       :align: center
       :width: 700px
       :alt: Image of a numeric field.
      
       ..
       
 Required Fields:
  * ``"classification": "STRING"`` (only available for widgets and microservices)
  * ``"default": INTEGER`` (does not have a default)
  * ``"name": "STRING"``
  * ``"options": {OPTIONS}`` (send an empty options field to use the default options)
  
   * ``"min": INTEGER`` (defaults to none)
   * ``"max": INTEGER`` (defaults to none)
   
  * ``"type": "numeric"``
  
 Optional Fields:
  * ``"section": "STRING"``
  * ``"helpText": "STRING with Markdown"``
  * ``"label": "STRING"``
  
________________________________________________________________________________________________________________________________________

.. _Multiple Selection:

Multiple Selection
^^^^^^^^^^^^^^^^^^

 Multiple selection allows studio users to select **multiple** values from a list of options.

 .. code-block:: javascript

    "classification": "Classification",
    "name": "Name",
    "options": [
       {"value":"Name","displayValue":"Label"},
       {"value":"Name","displayValue":"Label"}
    ],
    "type": "multiselect"
 
 .. figure:: ../images/multiselectfield.PNG
       :align: center
       :width: 700px
       :alt: Image of a multiselect field.
      
       ..
       
 Required Fields:
  * ``"classification": "STRING"`` (only available for widgets and microservices)
  * ``"name": "STRING"``
  * ``"options": {OPTIONS}`` (at least one option must be added to the options field)
  
   * ``{"value":"STRING","displayValue":"STRING"}`` (defaults to none)
   
  * ``"type": "multiselect"``
  
 Optional Fields:
  * ``"section": "STRING"``
  * ``"helpText": "STRING with Markdown"``
  * ``"label": "STRING"``

________________________________________________________________________________________________________________________________________

.. _Page Link:

Page Link
^^^^^^^^^

 Page link allows studio users to link to another URL by either selecting a widget from the current experience or by typing in a URL.

 .. code-block:: javascript

    "classification": "Classification",
    "name": "Name",
    "type": "page-link"
 
 .. figure:: ../images/pagelinkfield.PNG
       :align: center
       :width: 400px
       :alt: Image of a page-link field.
      
       ..
       
 Required Fields:
  * ``"classification": "STRING"`` (only available for widgets and microservices)
  * ``"name": "STRING"``
  * ``"type": "page-link"``
  
 Optional Fields:
  * ``"section": "STRING"``
  * ``"helpText": "STRING with Markdown"``
  * ``"label": "STRING"``
