.. _platform
Platform
========
.. _command center:

Command Center
--------------
A command center is a central location in the platform where :ref:`tools <tools>` are managed and created. The center cannot use :ref: 'tools <tools>', as it cannot create :ref:`experiences <experiences>`. The center can only manage, create, and distribute :ref:`tools <tools>`. A :ref:`studio <studio>` is needed to use :ref:`tools <tools>`.   

What it does
^^^^^^^^^^^^
Command center users can:

* Upload tool containers
* Create different versions of tools
* Define whether versions are deprecated, complete, or in-development
* Share tools with associated studios and command centers
* :ref:`Create CLI accounts <CLI>`

Why you should care
^^^^^^^^^^^^^^^^^^^
The command center will be the main access point for developers. The functions it provides will allow command center users to create, manage, and distribute the various tools he/she wishes to make.

.. _tools:

Tools
-----
Tools are the basic pieces of an :ref:`experience <experiences>`. There are three types: :ref:`widgets <widgets>`, :ref:`microservices <microservices>`, & :ref:`component-sets <component-sets>`.

What it does
^^^^^^^^^^^^
Tools can provide:

* Basic functionality that experiences use
* Reusable pieces that can be moved from experience to experience
* Data-collection that can dynamically alter or produce content for the user

Why you should care
^^^^^^^^^^^^^^^^^^^
Tools will be the main way developers interact with the platform. It will allow developers to create specific functionality for their or other people's use within an :ref:`experience <experiences>`. To get started developing tools, consult :ref:`Developing Tools`.

.. _studio:

Studio
------
A studio is a WYSIWYG designer application within the platform that allows users to assemble :ref:`experiences <experiences>` using a reusable set of tools. These :ref:`experiences <experiences>` can then be published to create the users own unique PWA. 

There are two types of studios: production and development.

* Production studios are the main studio where final published experiences are created for the public.

* Development studios are testing studios that allow developers to try out their tools within an experience. 

What it does
^^^^^^^^^^^^
Studios allow users to:

* Create and publish an experience
* Set custom activation codes, numbers, etc.
* Establish databases for data-collection and distribution

Why you should care
^^^^^^^^^^^^^^^^^^^
Studio users will be the audience for any tool a developer creates. Therefore, a firm grasp of what a studio looks like and how it functions will greatly increase the quality of any tool. In addition, studios will be the main area where tools are tested making them an essential part in any tool development.

.. _experiences:

Experiences
-----------
An Experience is a complete web application that delivers a full user experience for a specific need. An experience can be designed exclusively for mobile, tablets, desktops, or any combination thereof. Any Experience from the platform is automatically published as an encapsulated `Progressive Web Application <https://developers.google.com/web/progressive-web-apps/>`_.

What it does
^^^^^^^^^^^^
Experiences allow a user to:

* Use tools from a library to create applications 
* Publish PWAs 
* Create pre-set activations for a PWA

Why you should care
^^^^^^^^^^^^^^^^^^^
Experiences are where various :ref:`widgets <widgets>`, :ref:`microservices <microservices>`, and :ref:`component-sets <component-sets>` meet-up, and should always be kept in mind when developing an individual tool. At the end of the day, it is much more common that users will be fusing together a wide variety of tools to make one unified experience rather than using a single tool in isolation. 

.. _activations:

Activations
-----------
Activations refer to the method by which an :ref:`experience <experiences>` is started. Activation methods can include URL link, QR code, NFC tag, or SMS messages. The Lumavate :ref:`studio <studio>` automatically generates activation methods for each :ref:`experience <experiences>`, but the user also has the option to set-up their own activation codes. 

What it does
^^^^^^^^^^^^
Activations:

* Provides several pre-set activations (URL link, QA code, NFC tag, SMS message)
* Allows studio users to create custom activations
* Collects contextual data for developers and studio users
* Allows developers and studio users to create specific, contextualized experiences to the end user

Why you should care
^^^^^^^^^^^^^^^^^^^
Activation methods are how the end user connects with the :ref:`experience <experiences>`. However, activation methods can optionally pass additional contextual data during the activation of the :ref:`experience <experiences>`. This information can then be used by developers and :ref:`studio <studio>` users to create contextualized and directed :ref:`experiences <experiences>` for the end user. Developers have access to this activation data in the standard payload that is passed to each :ref:`tool <tools>` while :ref:`studio <studio>` users can look up the information in their databases. 

However, a developer has to specifically design their tool to allow for contextual changes based on the data collected to take full advantage of the activation’s potential. 

.. _databases:

Databases
---------
Any :ref:`microservice <microservices>` registered within Lumavate will get its own database context to be used at the developer's discretion. In addition, :ref:`studio <studio>` users can create their own databased within Lumavate in order to manage and distribute collected data.

What it does
^^^^^^^^^^^^
Databased allow the user to:

* Collect specified data from the end user or studio user
* Communicate that data to other tools
* Create individual environments for each studio

Why you should care
^^^^^^^^^^^^^^^^^^^
Anyone who is developing :ref:`microservices <microservices>` will need to understand how the databases work and what information they want to collect and distribute. However, people developing other :ref:`tools <tools>` should keep in mind what these databases offer them in terms of customizability and dynamic configuration as only compatible :ref:`microservices <microservices>` and :ref:`component-sets <component-sets>` will be able to use the :ref:`microservices <microservices>` database.  
