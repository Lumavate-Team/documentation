Platform
========

Command Center
--------------
A command center is a central location in the platform where tools are managed and created. The center cannot use tools. It can only manage, create, and distribute them.  

What it does
^^^^^^^^^^^^
Command center users can:

* Upload tool containers
* Create different versions of tools
* Define whether versions are deprecated, complete, or in-development
* Share tools with associated :ref: 'studios' and command centers
* Create :ref: 'CLI' accounts

Why you should care
^^^^^^^^^^^^^^^^^^^
The command center will be the main access point for developers. The functions it provides will allow command center users to create, manage, and distribute the various tools he/she wishes to make.


Tools
-----
Tools are the basic pieces of an :ref: 'experience'. There are three types: :ref: 'widgets', :ref: 'microservices', & :ref: component-sets.

What it does
^^^^^^^^^^^^
Tools can provide:

* Basic functionality that experiences use
* Reusable pieces that can be moved from :ref: ‘experience’ to :ref: ‘experience’
* Data-collection that can dynamically alter or produce content for the user

Why you should care
^^^^^^^^^^^^^^^^^^^
Tools will be the main way developers interact with the platform. It will allow developers to create specific functionality for their or other people's use within an :ref: 'experience'. To get started developing tools, consult :ref: 'Developing Tools'


Studio
------
A studio is a WYSIWYG designer application within the platform that allows users to assemble :ref: 'experiences' using a reusable set of tools. These :ref: ‘experiences’ can then be published to create the users own unique PWA. 

There are two types of studios: production and development.

Production studios are the main studio where final published experiences are created for the public.

Development studios are testing studios that allow developers to try out their tools within an ref: ‘experience’. 

What it does
^^^^^^^^^^^^
Studios allow users to:
* Create and publish an experience
* Set custom activation codes, numbers, etc.
* Establish databases for data-collection and distribution

Why you should care
^^^^^^^^^^^^^^^^^^^
Studio users will be the audience for any tool a developer creates. Therefore, a firm grasp of what a studio looks like and how it functions will greatly increase the quality of any tool. In addition, studios will be the main area where tools are tested making them an essential part in any tool development.


Experiences
-----------
An Experience is a complete web application that delivers a full user experience for a specific need. An experience can be designed exclusively for mobile, tablets, desktops, or any combination thereof. Every Experience from the platform is automatically published as an encapsulated 'Progressive Web Application <https://developers.google.com/web/progressive-web-apps/>'.

What it does
^^^^^^^^^^^^
Experiences allow a user to
* 
* 
* 

Why you should care
^^^^^^^^^^^^^^^^^^^
Experiences are the collective whole of the tools that developers create. It is where various widgets, microservices, and component-sets meet-up, and should always be kept in mind when developing an individual tool. At the end of the day, it is much more common that users will be fusing together a wide variety of tools to make one unified experience rather than using a single tool in isolation. 


Activations
-----------
Activations refer to the method by which an :ref: 'experience' is started. Activation methods can include URL link, QR code, NFC tag, or SMS messages. The Lumavate studio automatically generates activation methods for each :ref: 'experience', but the user also has the option to set-up their own activation codes. 

What it does
^^^^^^^^^^^^
Activations:
* Provides several pre-set activations (URL link, QA code, NFC tag, SMS message)
* Allows the studio user to create custom activations
* Collects contextual data for developers and studio users
* Allows developers and studio users to create specific, contextualized experiences to the end user

Why you should care
^^^^^^^^^^^^^^^^^^^
Activation methods are how the end user connects with the experience. However, activation methods can optionally pass additional contextual data during the activation of the :ref: ‘experience’. This information can then be used by developers and studio users to create contextualized and directed experiences for the end user. Developers have access to this activation data in the standard payload that is passed to each tool while studio users can look up the information in their databases. 

However, a developer has to specifically design their tool to allow for contextual changes based on the data collected to take full advantage of the activation’s potential. 


Databases
---------
Any :ref: 'microservice' registered within Lumavate will get its own database context to be used at the developer's discretion. In addition, studio users can create their own databased within Lumavate in order to manage and distribute collected data.

What it does
^^^^^^^^^^^^
Databased allow the user to:
* Collect specified data from the end user or studio user
* Communicate that data to other tools
* Create individual environments for each studio

Why you should care
^^^^^^^^^^^^^^^^^^^
Anyone who is developing :ref: 'microservices' will need to understand how the databases work and what information they want to collect and distribute. However, people developing other tools should keep in mind what these databases offer them in terms of customizability and dynamic configuration as only compatible :ref: 'microservices' and :ref: 'component-sets' will be able to use the :ref: 'microservices' database.  


API Reference
-------------

Current API documentation can be found at https://api.developer.lumavate.com
