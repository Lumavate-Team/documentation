Platform
========

Studio
------

The Lumavate Studio refers to the WYSIWYG designer application within the Lumavate Platform that allows Studio users to assemble Experiences using a reusable set of Tools (Components, Microservices, & Widgets).

Command Center
--------------

In the Lumavate Platform, a Command Center is a central location where Tools, used
within the Experiences, are managed. Tools are made up of Widgets, Microservices, and Component Sets. The Command Center is used to share those Tools with associated Studios. The Command Center can be thought of as “the gatekeeper of Studio Tools,” because Studios must be given access to Tools by a command center in order to use them.

Activations
-----------

Activations refer to the method by which an Experience is started. Activation methods can include such things as URL link, QR Code, NFC tag, or text back reply. The Lumavate Studio automatically generates activation methods for each Experience. Each activation method can optionally pass additional “contextual data” during the activation to the widget.  What data is passed during activation can be setup and configured in the Lumavate Studio. The developer has access to this activation data in the standard payload that is passed to each widget.

Experiences
-----------

An Experience is a complete web application that delivers a full user experience for a specific need. An experience can be designed exclusively for mobile, for tablets, for desktops, or any combination thereof. Within Lumavate, every Experience is automatically published from that platform as an encapsulated Progressive Web Application.

Databases
---------

Each Microservice registered within Lumavate will get it's own database context to be used at the developer's discretion.

Tools
-----

Widgets, Microservices, & Component Sets used within the Platform

API Reference
-------------

Current API documentation can be found at https://api.developer.lumavate.com

