.. _Platform terms:

==============
Platform Terms
==============

The following is a list of terms commonly used in the Lumavate platform. They are organized by location in the platform:

* :ref:`Command Center`

  * :ref:`Tools`
   
* :ref:`Studio`

  * :ref:`Activations`
   
  * :ref:`Databases`
   
  * :ref:`Experiences`
________________________________________________________________________________________________________________________________________

.. _command center:

Command Center
--------------

A command center is a central location in the platform where :ref:`tools <tools>` are managed and created. The center cannot use tools, as it cannot create :ref:`experiences <experiences>`. The center can only manage, create, and distribute tools. A :ref:`studio <studio>` is needed to use tools.   

What it does
^^^^^^^^^^^^

 Command center users can:

  * Upload tool containers
  * Create different versions of tools
  * Define whether versions are deprecated, in-development, or ready for production
  * Share tools with associated studios and command centers
  * :ref:`Create CLI accounts <CLI>`

Why it matters
^^^^^^^^^^^^^^

 The command center will be the main access point for developers. The functions it provides will allow command center users to create, manage, and distribute the various tools they wish to make.

________________________________________________________________________________________________________________________________________

.. _tools:

Tools
-----

Tools are the basic parts of an :ref:`experience <experiences>`. There are three types: :ref:`widgets <widgets>`, :ref:`microservices <microservices>`, and :ref:`component sets <component-sets>`.

What it does
^^^^^^^^^^^^

 Tools can provide:

  * Basic functionality for experiences
  * Reusable pieces that can be moved from experience to experience or from tool to tool
  * Data-collection that can dynamically alter or produce content for the end user

Why it matters
^^^^^^^^^^^^^^

 Tools are the main way developers interact with the platform. They allow developers to create specific functionality for their or other users' use within an experience. To get started developing tools, consult :ref:`Developing Tools`.

________________________________________________________________________________________________________________________________________

.. _studio:

Studio
------

A studio is a WYSIWYG designer application within the platform that allows users to assemble :ref:`experiences <experiences>` using a reusable set of :ref:`tools <tools>`. These experiences can then be published creating a unique `Progressive Web Application <https://developers.google.com/web/progressive-web-apps/>`_ (PWA). 

There are two types of studios:

* Production studios: are the main studio where experiences are created for the public.

* Development studios: are testing studios that allow developers to try out their tools within an experience. 

What it does
^^^^^^^^^^^^

 Studios allow users to:

  * Create and publish an experience
  * Set custom activation codes, numbers, etc.
  * Establish databases for data-collection and distribution

Why it matters
^^^^^^^^^^^^^^

 Studio users will be the audience for any tool a developer creates. Therefore, a firm grasp of what a studio looks like and how it functions will greatly increase the quality of any tool. In addition, studios will be the main area where tools are tested making them an essential part in any tool's development.


________________________________________________________________________________________________________________________________________

.. _activations:

Activations
-----------

Activations refer to the method by which an :ref:`experience <experiences>` is started. Activation methods can include URL links, QR codes, NFC tags, or SMS messages. The Lumavate :ref:`studio <studio>` automatically generates activation methods for each experience. The studio user also has the option to set up their own activation codes. 

What it does
^^^^^^^^^^^^

 Activations:

  * Provide several pre-set activations (URL link, QA code, NFC tag, SMS message)
  * Allow studio users to create custom activations
  * Collect contextual data for developers and studio users
  * Allow developers and studio users to create specific, contextualized experiences for the end user

Why it matters
^^^^^^^^^^^^^^

 Activation methods are how the end user connects with the experience. However, activation methods can optionally pass additional contextual data during the activation of the experience. This information can then be used by developers and studio users to create contextualized and directed experiences for the end user. Developers have access to this activation data in the standard payload that is passed to each :ref:`tool <tools>` while studio users can look up the information in their databases. 
 
  .. note:
   A developer has to specifically design their tool to allow for contextual changes based on the data collected to take full advantage of the activation’s potential. 

________________________________________________________________________________________________________________________________________

.. _databases:

Databases
---------

Any :ref:`microservice <microservices>` registered within Lumavate will get its own database context to be used at the developer's discretion. In addition, :ref:`studio <studio>` users can create their own databases within Lumavate in order to manage and distribute collected data.

What it does
^^^^^^^^^^^^

 Databases allow users to:

  * Collect specified data from the end user or studio user
  * Communicate that data to other tools
  * Create individual environments for each studio

Why it matters
^^^^^^^^^^^^^^

 Anyone who is developing microservices will need to understand how databases work in order to collect and distribute information. However, people developing other :ref:`tools <tools>` should keep in mind what these databases offer them in terms of customizability and dynamic configuration as only compatible tools will be able to use the microservice's database.  

________________________________________________________________________________________________________________________________________

.. _experiences:

Experiences
-----------

An experience is a complete web application that delivers a full user experience. An experience can be designed exclusively for mobile, tablets, desktops, or any combination thereof. All experiences are automatically published as an encapsulated `Progressive Web Application <https://developers.google.com/web/progressive-web-apps/>`_ (PWA).

What it does
^^^^^^^^^^^^

 Experiences allow a user to:

  * Use tools shared with them to create applications 
  * Publish PWAs 
  * Create pre-set activations for a PWA

Why it matters
^^^^^^^^^^^^^^

 Experiences are where various :ref:`widgets <widgets>`, :ref:`microservices <microservices>`, and :ref:`component sets <component-sets>` meet-up, and should always be kept in mind when developing an individual :ref:`tool <tools>`. At the end of the day, it is much more common for users to fuse together a wide variety of tools to make one unified experience than for them to use a single tool in isolation. 
