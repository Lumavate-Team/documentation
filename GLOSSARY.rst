Glossary
--------

.. Activations
.. ^^^^^^^^^^^

.. Activations refer to the method by which an experience is started. Activation methods can include such things as URL link, QR Code, NFC tag, or text back reply. The Lumavate studio automatically generates activation methods for each experience. Each activation method can optionally pass additional “contextual data” during the activation to the widget.  What data is passed during activation can be setup and configured in the Lumavate studio. The developer has access to this activation data in the standard payload that is passed to each widget.

.. Command Center
.. ^^^^^^^^^^^^^^

.. In the Lumavate platform, a command center is a central location where tools, used within the experiences, are managed. Tools are made up of widgets, microservices, and component-sets. The command center is used to share those tools with associated studios. The command center can be thought of as “the gatekeeper of Studio Tools,” because studios must be given access to tools by a command center in order to use them.

.. Component Sets
.. ^^^^^^^^^^^^^^

.. A component-set is a group of custom Web Components that can be used within experiences, similar to widgets. Web Components are based on existing web standards and are an industry standard with the intent to bring component-based engineering to the World Wide Web.

Environment Variables
^^^^^^^^^^^^^^^^^^^^^

 Environment variables refer to runtime field/value pairs that can be set inside a widget Docker container to affect runtime behavior. These variables can optionally be exposed to studio users inside the Lumavate studio to allow central configuration of a widget outside of properties. These are often used for **one-time configuration data** for a specific Lumavate studio instance that does not need to change for every experience within that instance. They may also be used so you can easily change some internal widget variables without hard coding them into the widget. Such internal widget variables do not need to be exposed to the studio users (see SECRET for creating secure internal variables).
 
 For example, if you need a specific URL designation for a third-party system that would remain the same for every experience within the Lumavate studio instance, you could set that as an environment variable instead of using a property and requiring it to be set in every experience. If the widget was shared across multiple Lumavate studio instances (two different companies or two different user groups within a company), the environment variable could be set differently. 

.. Experience
.. ^^^^^^^^^^

.. An Experience is a complete web application that delivers a full user experience for a specific need. An experience can be designed exclusively for mobile, for tablets, for desktops, or any combination thereof. Within Lumavate, every Experience is automatically published from that platform as an encapsulated Progressive Web Application.

.. Lumavate Studio
.. ^^^^^^^^^^^^^^^

.. The Lumavate Studio refers to the WYSIWYG designer application within the Lumavate platform that allows studio users to assemble Experiences using reusable Widgets.

.. Microservice
.. ^^^^^^^^^^^^

.. Similar to Widgets, Microservices are container-based applications used within Experiences. A Microservice is intended to be a behind-the-scenes addition to an Experience, providing additional business logic and/or data access to an Experience.

Progressive Web Application
^^^^^^^^^^^^^^^^^^^^^^^^^^^

 A Progressive Web Application (PWA) is a cloud-based web application that complies with the PWA standards started by Google in 2015 and adopted by Google, Microsoft, and Apple. The PWA specification establishes technical standards for such things as offline use, push notifications, save to desktop, and other native type capabilities previously unavailable to cloud-based applications. 
 
 `Visit Google’s PWA Compliance Checklist to learn more <https://developers.google.com/web/progressive-web-apps/checklist>`_.

.. Property
.. ^^^^^^^^

.. A property allows a studio user through the Lumavate studio to configure a widget for their specific experience. As a developer, you determine which properties should be exposed for your specific widget and what type of control should be used to capture the property. Properties can be set by the user using a variety of controls through the platform. Examples of control types for properties include text, numeric, image upload, color selector, dropdown, multi-select, multilingual text, page link/URL link, checkbox, and toggle.

.. Publish
.. ^^^^^^^

.. Publish or Publishing refers to the action a studio user takes to promote their designed experience into production with the Lumavate studio. As part of this process, Lumavate automatically assembles the required elements to publish the experience as a fully compliant PWA. It also automatically securely routes all the traffic to the various widgets used within the Experience.

Secret
^^^^^^

 Environment variables that are encrypted and not exposed to other users.

.. Studio Users
.. ^^^^^^^^^^^^

.. Users of the Lumavate studio product. Often these users do not have a development background. The Lumavate studio is designed so users without a development background can assemble and publish experiences using reusable widgets.

.. Tools
.. ^^^^^

.. Widgets, microservices, & component-sets used within the platform

.. Widget
.. ^^^^^^

.. A widget is a reusable web application component that can consist of one to many pages. It is a reusable web component that can be utilized across multiple Lumavate experiences. For example, a Locator is a standard widget. It provides location services and can be used in multiple experiences.
