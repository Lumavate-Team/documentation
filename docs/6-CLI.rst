
.. _CLI:

============
CLI
============

The Lumavate Commandline Line Interface (CLI) can be used to streamline many administrative tasks.

.. The CLI uses the native REST APIs available via the Platform. To learn more about Lumavate's REST APIs, please go here: <link to come>.

.. If you would like to know more about the CLI, it is available via open-source here: <link to come>.

The following documentation will explain:

* :ref:`Requirements`
* :ref:`Installation`
* :ref:`Provisioning Credentials`
* :ref:`CLI Syntax`

_______________________________________________________________________________________________________________________________________

.. _Requirements:

Requirements
-------------

You will need to install `Python 3.1.1 or higher <https://www.python.org/downloads/>`_ in order to use the CLI. 

 .. figure:: ../images/pythoninstall.PNG
    :align: center
    :width: 400px
    :alt: Image of a Python downloader with the "Add Python To Path" checkbox highlighted.
      
    Remember to click the “Add Python To Path” checkbox when installing Python.  

It is recommended that you install `Gitbash <https://git-scm.com/downloads>`_ as the CLI is written for and tested in a BASH shell. 

.. note::
   Luma supports `ZSH <https://sourceforge.net/projects/zsh/files/>`_. 

_______________________________________________________________________________________________________________________________________

.. _Installation:

Installation
------------
The CLI can be installed two different ways:

 #. :ref:`From Pip<Installation Pip>` (install without downloading files)
 #. :ref:`From Source<Installation Source>` (install by downloading files)

.. _Installation Pip:

From Pip
^^^^^^^^

 On Mac and Linx:
  
   .. code-block:: bash
     
      $ sudo pip3 install luma

 On Windows:
  
   .. code-block:: bash
     
      $ pip3 install luma

 The CLI should now be installed. Continue on to :ref:`Provisioning Credentials`. 

.. _Installation Source:

From Source
^^^^^^^^^^^

 Installing the CLI as a Non-admin:

  #. Clone the `CLI repo <https://github.com/LabelNexus/lumavate-cli>`_.
  
  #. Unzip the file you just downloaded.
  
  #. CD into the CLI directory.
  
     .. Code-block:: bash
     
        $ cd C:/User/DownloadLocation/lumavate-cli-master/cli
        
  #. Run:
  
     .. code-block:: bash
        
        On Windows:
        
        $ pip3 install luma --user
        
        On Mac and Linx:
        
        $ sudo pip3 install luma --user
 
  #. Add the returned path URL to your system environment variables. 
   
     Example Response: 
   
     .. code-block:: bash
       
        The script luma.exe is installed in 'C:\ComputerName\UserName\AppData\Roaming\Python\Python37\Scripts' which is not on PATH. 
        Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
  
  #. The CLI should now be installed. Continue on to :ref:`Provisioning Credentials`. 
 
 Installing the CLI as an Admin:

  #. Clone the `CLI repo <https://github.com/LabelNexus/lumavate-cli>`_.
  
  #. Unzip the file you just downloaded.
  
  #. CD into the CLI directory.
  
     .. Code-block:: bash
     
        $ cd C:/User/DownloadLocation/lumavate-cli-master/cli
        
  #. Run:
   
     .. code-block:: bash
     
        On Windows:
        
        $ pip3 install luma
        
        On Mac and Linx:
       
        $ sudo pip3 install luma

  #. The CLI should now be installed. Continue on to :ref:`Provisioning Credentials`. 
_______________________________________________________________________________________________________________________________________

.. _Provisioning Credentials:

Provisioning Credentials
-------------------------

The CLI requares two variables to be configured in order to talk to the platform: :ref:`configuring environments<Provisioning Environments>` and :ref:`configuring profiles<Provisioning Profiles>`.
    
    * **Environments** know how to get and refresh tokens so the user stays authorized with the platform. They also set what command centers or studios the user has access to.
    * **Profiles** give the user a company context in a specific environment which is required by most of the platform API. They set what studio or command center the user is modifying.  

.. _Provisioning Environments:

Setting-Up Environments:
^^^^^^^^^^^^^^^^^^^^^^^

 You can use either the :ref:`Lumavate pre-configured<enviroment preset configuration>` environment or you can :ref:`setup your own environment configuration<enviroment your own configuration>`.

.. _enviroment preset configuration:

 Using the preset configuration:

  #. Log into the command center you want to modify with the CLI.
  
     .. figure:: ../images/enviromentselect.PNG
         :align: center
         :width: 400px
         :alt: Image of the Lumavate Organization Select Page.
      
         The Organization Select page allows users to select the command center or studio he/she wishes to edit. Command centers are shown with a gear Settings icon. Studios are shown with a paint palette Color_Lens icon.
  
  #. Go to the CLI tab located in the side menu bar.
  
     .. figure:: ../images/sidebarforcli.PNG
         :align: center
         :width: 800px
         :alt: Image of the sidebar with the CLI option highlighted.
      
         The CLI tab in the sidebar allows Admin users to create a CLI accounts.
  
  #. Copy the information from the Configure An Environment field. It should look like this:
   
     .. code-block:: bash
       
         $ luma env config --env-name prod --app https://not-a-real-realm.place.lumavate-type.com --audience https://place.lumavate-type.com/notarealapp --token place-lumavate-type.notarealtoken.com --client-id NotARealId1234j2eIxKILomCdA --client-secret NotARealClientSecretEqeKWD5JgUtzsRkhNNXMPQM6auPhTTjVK
      
  #. Paste the command into your Bash window and click enter. 
  #. The CLI should return the following showing that the new enviroment Prod has been created. Continue on to :ref:`Setting up Profiles <Provisioning Profiles>`. 
     
     .. code-block:: bash
     
         envName app                                                  audience                                 token
         prod    https://not-a-real-realm.place.lumavate-type.com     https://place.lumavate-type.com/notanapp place-lumavate-type.notarealtoken.com

     .. warning::
        If there are two environments with the same name, the newer version will overwrite the older version.
 
 .. _enviroment your own configuration:
 
 Using your own configuration:

  #. Log into the command center you want to modify with the CLI.
     
     .. figure:: ../images/enviromentselect.PNG
         :align: center
         :width: 400px
         :alt: Image of the Lumavate Organization Select Page.
      
         The Organization Select page allows users to select the command center or studio he/she wishes to edit. Command centers are shown with a gear Settings icon. Studios are shown with a paint palette Color_Lens icon.
 
  #. Go to the CLI tab located in the side menu bar.
  
      .. figure:: ../images/sidebarforcli.PNG
          :align: center
          :width: 800px
          :alt: Image of the sidebar with the CLI option highlighted.
      
          The CLI tab in the sidebar allows Admin users to create a CLI accounts.
       
  #. Take note of the app, audience, token, client-id, and client-secret information from the Configure An Environment field.
  
  #. In your Bash window, run:
   
     .. code-block:: bash
       
         $ luma env config

  #. Fill out the prompts as they appear on the screen with the appropriate information. It should look like this:
   
     .. code-block:: bash
       
         $ Env Name: <<name of environment in CLI>>
           App: <<enviroment Url>>
           Token: <<enviroment token>>
           Audience: <<envitoment audience>>
           Client id: <<user clientId>>
           Client secret: <<user clientSecret>>
          
  #. The CLI should return the following with the env name you specified listed with the other enviroments showing that the new enviroment has been created. Continue on to :ref:`Setting up Profiles <Provisioning Profiles>`. 
  
     .. code-block:: bash
     
         envName app                                                    audience                                    token
         Fantasy https://not-a-real-realm2.fantasy.lumavate-type.com    https://fantasy.lumavate-type.com/notanapp2 fantasy-lumavate-type.notarealtoken2.com

  .. note:: 
     The CLI uses Client ID and Client Secret to associate a user context to a machine. From this point forward, user will refer to the Client ID and Client Secret information used to setup the environment in the CLI. 

.. _Provisioning Profiles:
  
Setting up Profiles:
^^^^^^^^^^^^^^^^^^^

 Profiles can be setup using the :ref:`Lumavate pre-set command<profile preset configuration>` or using :ref:`your own configuration<profile your own configuraiton>`. 

 You will need to have :ref:`configured an environment<Provisioning Environments>` on your machine through the CLI to configure a profile.  

.. _profile preset configuration:

 Using a preset configuration:

  #. Log into a Lumavate command center.
  
     .. figure:: ../images/enviromentselect.PNG
         :align: center
         :width: 400px
         :alt: Image of the Lumavate Organization Select Page.
      
         The Organization Select page allows users to select the command center or studio he/she wishes to edit. Command centers are shown with a gear Settings icon. Studios are shown with a paint palette Color_Lens icon.
         
  #. Navigate to the CLI tab located in the side menu bar.
     
     .. figure:: ../images/sidebarforcli.PNG
         :align: center
         :width: 800px
         :alt: Image of the sidebar with the CLI option highlighted.
      
         The CLI tab in the sidebar allows Admin users to create a CLI accounts.
         
  #. Copy the information from the Add A Profile field. It should look like this:
   
     .. code-block:: bash
       
         $ luma profile add --env prod

  #. Paste the command into your Bash window and click enter.
  
  #. You will be prompted to name the profile. It should look like this:
   
     .. code-block:: bash
       
         Profile Name: <<profile name: used to reference an organization>>

     .. warning::
        If there are two profiles with the same name, the newer version will overwrite the older version. Profiles in different environments can have the same name without overwriting each other.  
    
  #. You will then be presented with a list of organizations associated with the preset Lumavate enviroment. Pick the one you want to edit with this profile, and enter its ID number. It should look like this:
   
     .. code-block:: bash
       
          id Org Name                  Org Type Test Org
          35 Sample Command Center     dev      None
          49 Sample Studio             studio   False

          Org ID you want to associate with this profile: <<org id>>
  
  #. The CLI should return the following with the profile name you specified listed with the other profiles showing that the new profile has been created. Continue on to the :ref:`CLI Syntax<CLI Syntax>` for more help.
  
    .. code-block:: bash
    
        Environment Org Name              Org ID
        prod        Sample Command Center 35

.. _profile your own configuraiton:

 Using your own configuration:

  #. In your Bash window, run:
   
     .. code-block:: bash
       
         $ luma profile add

  #. You will be prompted to name your profile. It should look like this:
   
     .. code-block:: bash
       
         Profile Name: <<profile’s name in the CLI>>
     
     .. warning::
        If there are two profiles with the same name, the newer version will overwrite the older version. Profiles in different environments can have the same name without overwriting each other.  

  #. A list of environments will appear. Select which environment you wish to associate with the profile, and enter its Name:
   
     .. code-block:: bash
       
         Env Name App                                              Audience                                    Token
         Fantasy  https://not-a-realm2.fantasy.lumavate-type.com   https://fantasy.lumavate-type.com/notanapp2 fantasy-lumavate-type.notarealtoken2.com
         prod     https://not-a-realm.place.lumavate-type.com      https://place.lumavate-type.com/notanapp    place-lumavate-type.notarealtoken.com

          Env: <<Env Name>>

  #. A list of organizations will appear. Pick the one you want to edit with this profile, and enter its ID number. It should look like this:
   
     .. code-block:: bash
       
         id  Org Name                  Org Type Test Org
         99  Dragon Command Center     dev      None
         999 Child Command Center      dev      None
         9   Dragon Studio             studio   False

          Org ID you want to associate with this profile: <<org id>>
         
  #. The CLI should return the following with the profile name you specified listed with the other profiles showing that the new profile has been created. Continue on to the :ref:`CLI Syntax<CLI Syntax>` for more help.
  
    .. code-block:: bash
    
        Environment Org Name              Org ID
        Fantasy     Dragon Command Center 9 

 .. note::
    While running the profile command, you will have the option to associate the new profile to any organization the user has access to regardless of the command center you are currently in.

_______________________________________________________________________________________________________________________________________

.. _CLI Syntax:

CLI Syntax
----------

The CLI will allow users to interact with the Lumavate platform from a terminal. For setup instructions, look at the `Github readme <https://github.com/Lumavate-Team/documentation/blob/master/CLI.rst>`_ or the :ref:`CLI setup documentation <CLI>`. All the main commands are listed in the Command Index below. Each of the main commands has their subcommands listed in their section. 

Use the ``--help`` flag with the command for more information on how to use them and how to use their subcommands.

All commands will start with ``luma``.

Command Index:
 #. :ref:`API`
 #. :ref:`Component-set`
 #. :ref:`Component-set-version`
 #. :ref:`Env`
 #. :ref:`Experience`
 #. :ref:`Experience-collection`
 #. :ref:`Microservice`
 #. :ref:`Microservice-version`
 #. :ref:`Org`
 #. :ref:`Profile`
 #. :ref:`Version`
 #. :ref:`Widget`
 #. :ref:`Widget-version`
 #. :ref:`Ls Filters`
 #. :ref:`Version Commands`
 #. :ref:`Additional Info`
_______________________________________________________________________________________________________________________________________

.. _API:

API
^^^

Commands that directly query the API.

.. _API Delete:

Delete
++++++

 Calls a delete command in order to remove a tool through the API. 

 Example:
 
 .. code-block:: bash
    
     $ luma api delete /iot/v1/containers/999?expand=all
       Profile: dragon
 
 Response:
 
 .. code-block:: bash
    
     {"payload": {"data": {"createdAt": "2019-02-22T16:17:30.165138+00:00", "createdBy": 99, "expand": {"experiences": 0, "grantees": [], "publisher": {"id": 9, "instanceType": "cc", "isTest": null, "name": "Dragon Command Center"}}, 
     "id": 9999, "image": null, "integrationCloudId": 1, "isOwner": true, "lastModifiedAt": "2019-02-22T16:17:30.165109+00:00", "lastModifiedBy": 99, "name": "Fire Breathing", "premium": false, "type": "widget", "urlRef": "fire", 
     "versionInfo": {"latest": {"createdAt": null, "createdBy": null, "id": null, "label": null, "lastModifiedAt": null, "lastModifiedBy": null, "manageUrl": null, "versionNumber": null}}}}}

 Options:
  * ``-p, --profile "STRING"``
  * ``--help``
 
 .. note::
    API paths cannot include sort criteria.

.. _API Get:

Get
+++

 Calls a get command in order to return information from the API.

 Example:

 .. code-block:: bash
   
     $ luma api get /iot/v1/containers?expand=all
       Profile: dragon

 Response:
  
 .. code-block:: bash
  
      {"payload": {"currentItemCount": 2, "data": [{"createdAt": "2019-02-22T16:17:19.878312+00:00", "createdBy": 30, "expand": {"experiences": 0, "grantees": [], "publisher": {"id": 9, "instanceType": "cc",
      "isTest": null, "name": "Dragon Command Center"}}, "id": 9999, "image": {"key": "containers/dragon/icons/78130f31", "preview":
      "https://s3.amazonaws.com/from.through.to.com/containers/dragon/icons/78130f31?AWSAccessKeyId=NotAnAccessKeyId5Q&Signature=nota
      Signaturev8xyp8cnhE%3D&Expires=999993222"}, "integrationCloudId": 1, "isOwner": true, "lastModifiedAt": "2019-02-22T16:17:19.878294+00:00", "lastModifiedBy": 99, "name": "Dragon", "premium": false,
      "type": "widget", "urlRef": "dragon", "versionInfo": {"latest": {"createdAt": "2019-02-22T16:23:05.318677+00:00", "createdBy": 99, "id": 9999, "label": "prod", "lastModifiedAt": "2019-02-22T16:23:05.318646+00:00",
      "lastModifiedBy": 99, "manageUrl": null, "versionNumber": "9.9.9"}, "recommended": {"createdAt": "2019-02-22T16:23:05.318677+00:00", "createdBy": 30, "id": 9999, "label": "prod", 
      "lastModifiedAt": "2019-02-22T16:23:05.318646+00:00", "lastModifiedBy": 99, "manageUrl": null, "versionNumber": "9.9.9"}}}, {"createdAt": "2019-02-22T16:17:30.165138+00:00", "createdBy": 99, "expand": 
      {"experiences": 0, "grantees": [], "publisher": {"id": 9, "instanceType": "cc", "isTest": null, "name": "Dragon Command Center"}}, "id": 9999, "image": null, "integrationCloudId": 1, "isOwner": true,
      "lastModifiedAt": "2019-02-22T16:17:30.165109+00:00", "lastModifiedBy": 99, "name": "Fire Breathing", "premium": false, "type": "widget", "urlRef": "fire", "versionInfo": {"latest": {"createdAt": null, "createdBy": null,
      "id": null, "label": null, "lastModifiedAt": null, "lastModifiedBy": null, "manageUrl": null, "versionNumber": null}}}], "nextPage": null, "page": 1, "pageSize": 100, "prevPage": null, "totalItems": 2, "totalPages": 1}}

 Options: 
  * ``-p, --profile "STRING"``
  * ``--help``

 .. note::
    API paths cannot include sort criteria.

.. _API Post:

Post
++++

 Calls a post command in order to add a tool through the API. 

 Example:

 .. code-block:: bash
   
     $ luma api post /iot/v1/containers?expand=all -d '{"id":0,"type":"widget","name":"Dragon","urlRef":"dragon"}'
       Profile: dragon
 
 Response:
 
 .. code-block:: bash
    
     {"payload": {"data": {"createdAt": "2019-02-22T15:56:21.722668", "createdBy": 99, "expand": {"experiences": 0, "grantees": [], "publisher": {"id": 9, "instanceType": "cc", "isTest": null,
     "name": "Dragon Command Center"}}, "id": 9, "image": {"key": "containers/dragon/icons/af7ef4a6", "integrationCloudId": 1, "isOwner": true, "lastModifiedAt": "2019-02-22T15:56:21.722632",
     "lastModifiedBy": 99, "name": "Dragon", "premium": false, "type": "widget", "urlRef": "dragon", "versionInfo": {"latest": {"createdAt": null, "createdBy": null, "id": null, "label": null,
     "lastModifiedAt": null, "lastModifiedBy": null, "manageUrl": null, "versionNumber": null}}}}}

 Options: 
  * ``-p, --profile "STRING"``
  * ``-d, --data "{JSON}, {JSON}"``
  * ``--help``

 .. note::
    API paths cannot include sort criteria.

.. _API Put:

Put
+++

 Calls a put command in order to change a tool through the API.

 Example:

 .. code-block:: bash
   
     $ luma api post /iot/v1/containers?expand=all -d '{"id":9,"type":"widget","name":"Fire Breathing","urlRef":"fireball"}'
       Profile: dragon
  
 Response:
 
 .. code-block:: bash
 
     {"payload": {"data": {"createdAt": "2019-02-22T16:03:22.950331", "createdBy": 99, "expand": {"experiences": 0, "grantees": [], "publisher": {"id": 9, "instanceType": "cc", "isTest": null, 
     "name": "Dragon Command Center"}}, "id": 1675, "image": null, "integrationCloudId": 1, "isOwner": true, "lastModifiedAt": "2019-02-22T16:03:22.950312", "lastModifiedBy": 99, "name": "Fire Breathing",
     "premium": false, "type": "widget", "urlRef": "fireball", "versionInfo": {"latest": {"createdAt": null, "createdBy": null, "id": null, "label": null, "lastModifiedAt": null, "lastModifiedBy": null,
     "manageUrl": null, "versionNumber": null}}}}}

 Options: 
  * ``-p, --profile “STRING”``
  * ``-d, --data "{JSON}, {JSON}"``
  * ``--help``

 .. note::
    API paths cannot include sort criteria.
_______________________________________________________________________________________________________________________________________

.. _Component-set:

Component-set
^^^^^^^^^^^^^

Commands that create, modify, share, and delete component-set containers.

.. _Component-set Access:

Access
++++++

 Shares and unshares component-set containers with child organizations.

 Example:

 .. code-block:: bash
   
     $ luma component-set access --add 9
       Profile: dragon
       Component set: 999

 Response:
 
 .. code-block:: bash
 
     failed sharedWith          unsharedFrom resultingGrantees
     []     [{'granteeId': 9}]  []           ['Dragon Studio']

 Options: 
  * ``-p, --profile “STRING”``
  * ``-cs, --component-set ID``
  * ``--add ID || Name``
  * ``--rm ID || Name``
  * ``--absolute ID || Name``
  * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Component-set Add:

Add
+++

 Adds a component-set container. 

 Example:

 .. code-block:: bash
   
     $ luma component-set add
       Profile: dragon
       Name: Fire Breath
       Url Ref: firebreath

 Response:

 .. code-block:: bash
   
     id  name        urlRef      createdAt
     999 Fire Breath firebreath  02/22/19 16:36:09

 Options: 
  * ``-p, --profile “STRING”``
  * ``--name “STRING”``
  * ``--url-ref “LOWERCASE STRING”``
  * ``-path, --icon-file “FILE PATH”``
  * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
  * ``--json`` 
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Component-set Ls:

Ls
++

 Lists all component-set containers in the command center associated with the specified profile. 

 Example:

 .. code-block:: bash
   
     $ luma component-set ls
       Profile: dragon
 
 Response:
 
 .. code-block:: bash
 
     id  name          urlRef       createdAt
     999 Fire Breath   firebreath   02/22/19 16:36:09
     99  Frosty Breath frostybreath 02/22/19 16:36:09

 Options:
  * ``-p, --profile “STRING”``
  * ``-f, --format “{JSON VALUE}, {JSON VALUE}”`` 
  * ``--filter “{JSON VALUE=SPECIFIC VALUE}”``
  * ``--page INTAGER`` 
  * ``--pagesize INTAGER``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Component-set Rm:

Rm
++

 Deletes a component-set container. This can only be done after all versions in the container have been deleted.

 Example:

 .. code-block:: bash
   
     $ luma component-set rm
       Profile: dragon
       Component set: 999
 
 Response:
 
 .. code-block:: bash
 
     id  name        urlRef      createdAt
     999 Fire Breath firebreath  02/22/19 16:36:09

 Options: 
  * ``-p, --profile “STRING”``
  * ``-cs, --component-set ID``
  * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
  * ``--json``
  * ``--table``
  * ``--help`` 

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Component-set Update:

Update
++++++

 Updates the name or image of a component-set container. 

 Example:

 .. code-block:: bash
   
     $ luma component-set update --name "Frosty Breath"
       Profile: dragon
       Component set: 999
 
 Response:
 
 .. code-block:: bash
 
    id  name          urlRef      createdAt
    999 Frosty Breath firebreath  02/22/19 16:36:09

 Options: 
  * ``-p, --profile “STRING”``
  * ``-cs, --component-set ID``
  * ``--name “STRING”``
  * ``-path, --icon-file “FILE PATH”``
  * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated. 
    Use ``--format`` to see JSON values organized in table format.
_______________________________________________________________________________________________________________________________________

.. _Component-set-version:

Component-set-version
^^^^^^^^^^^^^^^^^^^^^

Commands that create, modify, and delete component-set versions.

.. _Component-set-version Add:

Add
+++

 Adds a version to a component-set container.  

 Example:

 .. code-block:: bash
   
     $ luma component-set-version add 
       Profile: dragon
       Component set: 999
       Component set file: “C:\fantasy\creatures\dragons\firebreather.zip”
       Label: prod
       Version: 9.9.9
 
 Response:
 
 .. code-block:: bash
    
     Image Size: 6.91 KB
     Uploading Component Set Version to Lumavate
     id  versionNumber directIncludes directCssIncludes label createdAt
     999 9.9.9         0              0                 prod  02/22/19 16:54:00

 Options: 
  * ``-p, --profile “STRING”``
  * ``-cs, --component-set ID``
  * ``-path, --component-set-file-path “FILE PATH”``
  * ``-fv, --from-version (*.*.*)``
  * ``-v, --version INTAGER (*.*.*)``
  * ``--patch INTAGER``
  * ``--minor INTAGER``
  * ``--major INTAGER``
  * ``--css-includes “STRING”``
  * ``--direct-includes “STRING”``
  * ``-l, --label “[prod, dev, old]”``
  * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated. 
    Use ``--format`` to see JSON values organized in table format.

 .. warning::
    File paths with spaces in them may need to be specified in the main command using the ``-path`` option so as to preserve the spaces.

.. _Component-set-version Components:

Components
++++++++++

 Returns the JSON of a component-set version. 

 Example:

 .. code-block:: bash
   
     $ luma component-set-version components
       Profile: dragon
       Component set: 999
       Version: 9.9.9
      
 Response:
 
 .. code-block:: bash
 
     {"payload": {"data": {"componentSetId": 999, "createdAt": "2019-02-22T16:54:00.511074+00:00", "createdBy": 30, "directCssIncludes": [], "directIncludes": [], "distribution": "/iot/v1/dynamic-component-sets/firebreath/9.9.9", "expand": {"components": [{"icon": "/iot/v1/dynamic-component-sets/firebreath/9.9.9/icons/material.svg", "label": "No Template", "properties": [{"label": "No Template", "name": "selectOptions", "options": {"readonly": null}, "type": "text"}], "section": "Fire Breath (v9.9.9)", "tags": ["material", "body"], "template": "<div class=\"mdc-select\"><i class=\"mdc-select__dropdown-icon\"></i><select id=\"{{ componentData.Id }}\" class=\"mdc-select__native-control\"></div>", "type": "material-input-select"}]}, "id": 999, "label": "prod", "lastModifiedAt": "2019-02-22T16:54:00.511040+00:00", "lastModifiedBy": 30, "major": 9, "minor": 9, "patch": 9, "state": "available", "versionNumber": "9.9.9"}}}

 Options: 
  * ``-p, --profile “STRING”``
  * ``-cs, --component-set ID``
  * ``-v, --version INTAGER (*.*.*)``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` and ``--json`` are deprecated.
    The CLI will return the JSON file by default. The file cannot be organized by the CLI.

.. _Component-set-version Ls:

Ls
++

 Lists all versions in a component-set container.

 Example:

 .. code-block:: bash
   
     $ luma component-set-version ls
       Profile: dragon
       Component-set: 999
 
 Response:
 
 .. code-block:: bash
 
     id  versionNumber # Inc # Css Inc label # Exp createdAt
     999 9.9.9         0     0         prod  0     02/22/19 16:54:00
     99  9.9.99        1     1         old   0     02/22/19 16:54:00

 Options: 
  * ``-p, --profile “STRING”``
  * ``-cs, --component-set ID``
  * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
  * ``--filter “{JSON VALUE=SPECIFIC VALUE}”``
  * ``--page INTAGER``
  * ``--pagesize INTAGER``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

 .. note::
    Version number is filtered as “major=*&minor=*&patch=*”.

.. _Component-set-version Rm:

Rm
++

 Deletes a version from a component-set container.

 Example:

 .. code-block:: bash
   
     $ luma component-set-version rm
       Profile: dragon
       Component set: 999
       Version number: 9.9.9
 
 Response:
 
 .. code-block:: bash
 
     id  versionNumber directIncludes directCssIncludes label createdAt
     999 9.9.9         0              0                 prod  02/22/19 16:54:00
 
 Options: 
  * ``-p, --profile “STRING”``
  * ``-cs, --component-set ID``
  * ``-vm, --version-mask INTAGER (*.*.*)``
  * ``-v, --version INTAGER (*.*.*)``
  * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Component-set-version Update:

Update
++++++

 Updates the label of a component-set version.

 Example:

 .. code-block:: bash
   
     $ luma component-set-version update -l dev 
       Profile: dragon
       Component set: 999 
       Version number: 9.9.9
 
 Response:
 
 .. code-block:: bash
    
     id  versionNumber directIncludes directCssIncludes label createdAt
     999 9.9.9         0              0                 dev   02/22/19 16:54:00

    
 Options: 

  * ``-p, --profile "STRING"``
  * ``-cs, --component-set ID``
  * ``-v, --version INTAGER (*.*.*)``
  * ``-l, --label "[prod, dev, old]"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

_______________________________________________________________________________________________________________________________________

.. _Env:

Env
^^^

Commands that create, modify, and delete environments.

.. _Env Config:

Config
++++++

 Creates an environment. 

 Example:

 .. code-block:: bash
   
     $ luma env config
       Env name: Fantasy
       App: https://example-realm.fantasy.lumavate-type.com
       Token: fantasy-lumavate-type.not-a-real-token.com
       Audience: https://fantasy.lumavate-type.com/notarealaudience
       Client secret: NotARealClientSecretEqeKWD5JgUtzsRkhNNXMPQM6auPhTTjVK
       Client id: NotARealId1234j2eIxKILomCdA
 
 Response:
 
 .. code-block:: bash
 
     envName app                                                    audience                                    token
     Fantasy https://not-a-real-realm2.fantasy.lumavate-type.com    https://fantasy.lumavate-type.com/notanapp2 fantasy-lumavate-type.notarealtoken2.com
     
 Options: 
  * ``--env-name "STRING"``
  * ``--app "LINK"``
  * ``--token "LINK"``
  * ``--audience "LINK"``
  * ``--client-id "ID"``
  * ``--client-secret "SECRET"``
  * ``--json``
  * ``--help``

.. _Env Ls:

Ls
++

 Lists all the environments the user has access to.

 Example:

 .. code-block:: bash
   
     $ luma env ls
 
 Response:
 
 .. code-block:: bash
 
     envName  app                                           audience                                   token       
     Fantasy  https://not-a-realm.fantasy.lumavate-type.com https://fantasy.lumavate-type.com/notanapp fantasy-lumavate-type.NotAToken.com
     prod     https://not-a-realm.place.lumavate-type.com   https://place.lumavate-type.com/notanapp   place-lumavate-type.notatoken.com

    
 Options: 
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--help``

.. _Env Rm:

Rm
++

 Removes an environment. 

 Example:

 .. code-block:: bash
   
     $ luma env rm
       Name: Fantasy
 
 Response: 
 
 .. code-block:: bash
 
     {"app": "https://not-a-realm.fantasy.lumavate-type.com", "audience": "https://fantasy.lumavate-type.com/notanapp", "clientId": "NotAClientIdELhuj2eIxKILomCdA", "clientSecret": "NotAClientSecretCbhNEgmEqeKWD5JgUtzsRkhNNXMPQM6auPhTTjVK", "envName": "Fantasy", "token": "fantasy-lumavate-type.notatoken.com"}

 Options: 

  * ``--env-name "STRING"``
  * ``--help``

_______________________________________________________________________________________________________________________________________

.. _Experience:

Experience
^^^^^^^^^^

Commands that move and list experiences.

.. _Experience Export:

Export
++++++

 Exports an experience as a JSON file from a studio.

 Example:

 .. code-block:: bash
   
     $ luma experience export
       Profile: dragon
       Export file: “C:\fantasy\creatures\dragon\egg.json”
       Label: Creatures
 
 Response:
 
 .. code-block:: bash
 
     Saved to C:\fantasy\creatures\dragons\egg.json
 
 Options:
  * ``-p, --profile "STRING"``
  * ``-l, --label "STRING"``
  * ``-n, --name "STRING"``
  * ``-path, --export-file "FILE PATH"``
  * ``--json``
  * ``--help``

 .. warning::
    File paths with spaces in them may need to be specified in the main command using the ``-path`` option so as to preserve the spaces.
    
.. _Experience Import:

Import
++++++

 Imports an experience JSON file to a studio.

 Example:

 .. code-block:: bash
   
    $ luma experience import
      Profile: dragon
      Label: Dragon Hatchling
      Activation code: hatch
      Import file: "C:\fantasy\creatures\dragons\egg.json"
      Collection Name: Creatures
 
 Response:
 
 .. code-block:: bash
 
     Uploading file...
     File uploaded.

     Successfully imported experience.
     
 Options:
  * ``-p, --profile "STRING"``
  * ``-l, --label "STRING"``
  * ``-d, --description "STRING"``
  * ``-ci, --collection-id ID``
  * ``--device "[mobile, tablet, web]"``
  * ``-cn, --collection-name "STRING"``
  * ``-ac, --activation-code "STRING"``
  * ``-t, --template``
  * ``-ru, --redirect-url "URL"``
  * ``-path, --import-file "FILE PATH"``
  * ``--json``
  * ``--help``
 
  .. warning::
    File paths with spaces in them may need to be specified in the main command using the ``-path`` option so as to preserve the spaces.
    
.. _Experience Ls:

Ls
++

 Lists all the experiences in the studio associated with the specified profile.

 Example:

 .. code-block:: bash
   
     $ luma experience ls
       Profile: dragon
 
 Response:
 
 .. code-block:: bash
 
     id  label            name createdAt
     99  Dragons          drag 08/27/18 15:57:16
     999 Dragon Hatchling drha 09/12/18 17:22:11

 Options:
  * ``-p, --profile "STRING"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--filter "{JSON VALUE=SPECIFIC VALUE}"``
  * ``--page INTEGER``
  * ``--pagesize INTEGER``
  * ``--json``
  * ``--help``

_______________________________________________________________________________________________________________________________________

.. _Experience-collection:

Experience-collection
^^^^^^^^^^^^^^^^^^^^^

List experience collections in the studio associated with the specified profile.

Example:

.. code-block:: bash

     $ luma experience-collection ls
       Profile: dragon

Response:

.. code-block:: bash

    id  name      createdAt
    99  Creatures 02/27/18 20:08:10
   
Options: 
 * ``--help``

_______________________________________________________________________________________________________________________________________

.. _Microservice:

Microservice
^^^^^^^^^^^^

Commands that create, modify, share, and delete microservice containers.

.. _Microservice Access:

Access
++++++

 Shares and unshares a microservice container with child organizations. 

 Example:

 .. code-block:: bash
   
     $ luma microservice access --add 99
       Profile: dragon
       Microservice: 999
 
 Response:
 
 .. code-block:: bash
 
     failed sharedWith          unsharedFrom resultingGrantees
     []     [{'granteeId': 99}] []           ['Dragon Studio']
     
 Options: 
  * ``-p, --profile "STRING"``
  * ``-ms, --microservice ID``
  * ``--add ID``
  * ``--rm ID``
  * ``--absolute ID``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table`` 
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Microservice Add:

Add
+++

 Adds a microservice container to a command center.

 Example:

 .. code-block:: bash
   
     $ luma microservice add 
       Profile: dragon
       Name: Dragon Fact Sheet
       Url Ref: factsheet
 
 Response:
 
 .. code-block:: bash
 
     id  name              urlRef    createdAt
     999 Dragon Fact Sheet factsheet 02/22/19 19:21:49

 Options: 
  * ``-p, --profile "STRING"``
  * ``--name "STRING"``
  * ``--url-ref "STRING"``
  * ``-path, --icon-file "FILE PATH"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Microservice Ls:

Ls
++

 Lists all microservices containers in the command center associated with the specified profile.

 Example:

 .. code-block:: bash
   
     $ luma microservice ls 
       Profile: dragon
 
 Response:
 
 .. code-block:: bash
 
     id  name              urlRef    createdAt
     99  World Building    world     10/12/18 20:05:40
     999 Dragon Fact Sheet factsheet 02/22/19 19:21:49

 Options: 
  * ``-p, --profile "STRING"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--filter "{JSON VALUE=SPECIFIC VALUE}"``
  * ``--page INTAGER``
  * ``--pagesize INTAGER``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Microservice Rm:

Rm
++

 Removes a microservice container. 

 Example:

 .. code-block:: bash
   
     $ luma microservice rm 
       Profile: dragon 
       Microservice: 999
 
 Response:
 
 .. code-block:: bash
 
     id  name              urlRef    createdAt
     999 Dragon Fact Sheet factsheet 02/22/19 19:21:49
     
 Options: 
  * ``-p, --profile "STRING"``
  * ``-ms, --microservice ID``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Microservice Update:

Update
+++++++

 Updates the name or image of a microservice container.

 Example:

 .. code-block:: bash
   
     $ luma microservice update --name "World Building" 
       Profile: dragon 
       Microservice: 999 
 
 Response:
 
 .. code-block:: bash
 
     id  name           urlRef    createdAt
     999 World Building factsheet 02/22/19 19:31:05

 Options: 
  * ``-p, --profile "STRING"``
  * ``-ms, --microservice ID``
  * ``--name "STRING"``
  * ``-path, --icon-file "FILE PATH"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

_______________________________________________________________________________________________________________________________________

.. _Microservice-version:

Microservice-version
^^^^^^^^^^^^^^^^^^^^

Commands that add, modify, and delete microservice versions.

.. _Microservice-version Add:

Add
+++

 Adds a version to a microservice container.

 Example:

 .. code-block:: bash
   
     $ luma microservice-version add 
       Profile: dragon 
       Microservice: 999
       Label: prod
       Version: 9.9.9 
       Port: 5000
       Microservice-file-path: "C:\fantasy\creatures\dragons\DragonFactSheet.gz"
 
 Response:
 
 .. code-block:: bash
 
     Uploading image to Lumavate:
     Image Size: 59.43 MB
     id  actualState versionNumber label createdAt
     999 created     9.9.9         prod  02/22/19 19:40:59

     
 Options: 
  * ``-p, --profile "STRING"``
  * ``-ms, --microservice ID``
  * ``--port INTAGER``
  * ``-image, --docker-image "FILE PATH"``
  * ``-path, --microservice-file-path "FILE PATH"``
  * ``-fv, --from-version INTAGER (*.*.*)``
  * ``-v, --version INTAGER (*.*.*)``
  * ``--patch INTAGER``
  * ``--minor INTAGER``
  * ``--major INTAGER``
  * ``--env-var "{"STRING":"KEY"}"``
  * ``-l, --label "[dev, old, prod]"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated. 
    Use ``--format`` to see JSON values organized in table format.

.. _Microservice-version Exec:

Exec
++++

 Sends commands directly to Docker. For more information on Docker commands, consult the `Docker documentation <https://docs.docker.com/engine/reference/commandline/docker/>`_.

 Example:

 .. code-block:: bash
   
     $ luma microservice-version exec '<<Docker command>>' 
       Profile: dragon 
       Mirocservice: 999 
       Version Number: 9.9.9

 Options: 
  * ``-p, --profile "STRING"``
  * ``-ms, --microservice ID``
  * ``-v, --version INTAGER (*.*.*)``
  * ``--target [one, all]`` 
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Microservice-version Logs:

Logs
++++

 Returns the logs for a microservice version.

 Example:

 .. code-block:: bash
   
     $ luma microservice-version logs 
       Profile: dragon 
       Microservice: 999
       Version Number: 9.9.9

 Response:
 
 .. code-block:: bash
 
     [2019-02-22 19:58:00 +0000] [1] [INFO] Starting gunicorn 19.9.0
     [2019-02-22 19:58:00 +0000] [1] [INFO] Listening at: http://0.0.0.0:5000 (1)
     [2019-02-22 19:58:00 +0000] [1] [INFO] Using worker: eventlet
     [2019-02-22 19:58:00 +0000] [7] [INFO] Booting worker with pid: 7
     [2019-02-22 19:58:00 +0000] [9] [INFO] Booting worker with pid: 9
     [2019-02-22 19:58:00 +0000] [11] [INFO] Booting worker with pid: 11
     [2019-02-22 19:58:00 +0000] [13] [INFO] Booting worker with pid: 13
    
 Options: 
  * ``-p, --profile "STRING"``
  * ``-ms, --microservice ID``
  * ``-v, --version INTAGER (*.*.*)``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Microservice-version Ls:

Ls
++

 Lists all versions of a microservice container.

 Example:

 .. code-block:: bash
   
     $ luma microservice-version ls 
       Profile: dragon
       Microservice: 999
 
 Response:
 
 .. code-block:: bash
 
     id  actualState versionNumber label createdAt
     999 stopped     9.9.9         prod  02/22/19 19:57:16

 Options: 
  * ``-p, --profile "STRING"``
  * ``-ms, --microservice ID``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--filter "{JSON VALUE=SPECIFIC VALUE}"``
  * ``--page INTAGER``
  * ``--pagesize INTAGER``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

 .. note::
    Version number is filtered as ``"major=*&minor=*&patch=*"``.

.. _Microservice-version Rm:

Rm
++

 Removes a version from a microservice container.

 Example:

 .. code-block:: bash
   
     $ luma microservice-version rm
       Profile: dragon
       Microservice: 999
       Version: 9.9.9
 
 Response:
 
 .. code-block:: bash
 
     id  versionNumber label  createdAt
     999 9.9.9         prod   02/22/19 19:57:16
     
 Options: 
  * ``-p, --profile "STRING"``
  * ``-ms, --microservice ID``
  * ``-vm, --version-mask INTAGER (*.*.*)``
  * ``-v, --version INTAGER (*.*.*)``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Microservice-version Start:

Start
+++++

 Starts a microservice version.

 Example:

 .. code-block:: bash
   
     $ luma microservice-version start
       Profile: dragon
       Microservice: 999
       Version: 9.9.9
 
 Response:
 
 .. code-block:: bash
 
     id  Current State Version # Created At
     999 running       9.9.9     02/22/19 19:57:16

 Options: 
  * ``-p, --profile "STRING"``
  * ``-ms, --microservice ID``
  * ``-v, --version INTAGER (*.*.*)``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated. 
    Use ``--format`` to the JSON values organized in table format.

.. _Microservice-version Stop:

Stop
++++

 Stops a microservice version. A microservice version cannot be stopped if it is being used in an experience.

 Example:

 .. code-block:: bash
   
     $ luma microservice-version stop
       Profile: dragon
       Microservice: 999
       Version: 9.9.9
 
 Response:
 
 .. code-block:: bash
 
     id  Current State Version # Created At
     999 stopped       9.9.9     02/22/19 19:57:16

 Options: 
  * ``-p, --profile "STRING"``
  * ``-ms, -- microservice ID``
  * ``-v, --version INTAGER (*.*.*)``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Microservice-version Update:

Update
++++++

 Updates the label of a microservice version.

 Example:

 .. code-block:: bash
   
    $ luma microservice-version update --label dev
      Profile: dragon
      Microservice: 999
      Version: 9.9.9

 Response:
 
 .. code-block:: bash
 
     id  versionNumber label createdAt
     999 9.9.9         dev   02/22/19 19:57:16
     
 Options: 
  * ``-p, --profile "STRING"``
  * ``-ms, -- microservice ID``
  * ``-v, --version INTAGER (*.*.*)``
  * ``-l, --label "[dev, old, prod]"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

_______________________________________________________________________________________________________________________________________

.. _Org:

Org
^^^

Commands that list the organizations associated with an environment or organization.

.. _Org Child-orgs:

Child-orgs
++++++++++

 Lists the child organizations that a profile’s associated organization can share with.

 Example:

 .. code-block:: bash
   
     $ luma org child-orgs
       Profile: dragon

 Response:
 
 .. code-block:: bash
 
     id  name                   instanceType isTest
     999 Child Command Center   dev          None
     9   Dragon Studio          studio       False
     
 Options: 
  * ``-p, --profile "STRING"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--filter "{JSON VALUE=SPECIFIC VALUE}"``
  * ``--json``
  * ``--help``

.. _Org Ls:

Ls
++

 Lists the organizations inside an environment.

 Example:

 .. code-block:: bash
   
     $ luma org ls
       Env: Fantasy

 Response:
 
 .. code-block:: bash
 
     id  name                  instanceType isTest
     999 Child Command Center  dev          None
     99  Dragon Command Center dev          None
     9   Dragon Studio         studio       False
     
 Options: 
  * ``--env "STRING"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--filter "{JSON VALUE=SPECIFIC VALUE}"``
  * ``--json``
  * ``--help``

_______________________________________________________________________________________________________________________________________

.. _Profile:

Profile
^^^^^^^

Commands that add, modify, or delete profiles.

.. _Profile Add:

Add
+++

 Adds a profile to an environment and associates the profile to a specific organization.

 Example:

 .. code-block:: bash
   
     $ luma profile add
       Profile name: dragon
       
         Env Name App                                              Audience                                    Token
         Fantasy  https://not-a-realm2.fantasy.lumavate-type.com   https://fantasy.lumavate-type.com/notanapp2 fantasy-lumavate-type.notarealtoken2.com
         prod     https://not-a-realm.place.lumavate-type.com      https://place.lumavate-type.com/notanapp    place-lumavate-type.notarealtoken.com
       
       Name of Env you want to use with this profile: Fantasy
       
       id  name                  Org Type Test Org
       999 Child Command Center  dev      None
       99  Dragon Command Center dev      None
       9   Dragon Studio         studio   False
       
       Org ID you want to associate with this profile: 99

 Response:
 
 .. code-block:: bash
 
     Environment Org Name              Org ID
     Fantasy     Dragon Command Center 99
     
 Options: 
  * ``--profile-name "STRING"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--help``

.. _Profile Ls:

Ls
++

 Lists all profiles associated with the Client ID and Secret.

 Example:

 .. code-block:: bash
   
     $ luma profile ls
 
 Response:
 
 .. code-block:: bash
 
     profileName       env     orgName                      orgId
     dragon            Fantasy Dragon Command Center        99
     dragon-two        Fantasy Dragon Studio                9
     profile           prod    Sample Command Center        35

 Options: 
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--help``

.. _Profile Rm:

Rm
++

 Deletes a profile.

 Example:

 .. code-block:: bash
   
     $ luma profile rm
       Profile: dragon

 Response:
 
 .. code-block:: bash
 
     {"accessToken": "NotAccessTokenOiJSUzI1NiIsImtpZCI6Ik5VSXhSVFpHTmpORU9FVkdNVVZHTlRGQk9FWXdRMNotAccessToken1RnME1FTTBOdyJ9.eyJodHRwczovL2x1bWF2YXRlLmNvbS91dWlkIjoiOGZjMGM1NTgtZmJkNS00MWRlLWFhOTUtN2FkMmJmNDAyOGM3IiwiaXNzIjoiaHR0cHM6Ly9kcmFnb25mbHktbHVtYXZhdGUtZGV2LmF1dGgwLmNvbS8iLCJzdWIiOiJreW8yZkQwMXgwd1JVM3RFTGh1ajJlSXhLSUxvbUNkQUBjbNotAccessTokenkcmFnb25mbHkubHVtYXZhdGUtZGV2LmNvbS9hcHAiLCJpYXQiOjE1NDg3MTA1MzUsImV4cCI6MTU0ODc5NjkzNSwiYXpwIjoia3lvMmZEMDF4MHdSVTN0RUxodWoyZUl4S0lMb21DZEEiLCJndHkiOiJjbGllbnQtY3JlZGVudGlhbHMifQ.oOWd0sd05uvMVnZZJDTpXA9pqbAsVsq2Je97nS3J7wy8c-o7LUuN_kNYeCyxZWZ2FEBhVl2galmUB_dvUxdnYOzRMNhiiIqxZhQHeNotAccessTokenjCHDqCmuQQvPg-yqZxlQL6xfHqcmh2-syTeCyHf5y_gCWdxsUhuMSj28vtH5_v76NotAccessTokenSyb5XktrdUobFuSdvy4fw-GU5eUAEFRgzlYbnRzq8ygB4SXONZvbcKqVqpBDFdbdcmo4jIWk4a2gK5-v51a49Sh798dSBxiNotAccessTokennCxD7f7VcCWuUW0wNX87YtIjHsAw", "env": "Fantasy", "orgId": 99, "orgName": "Dragon Command Center"}

 Options: 
  * ``-p, --profile "STRING"``
  * ``--help``

_______________________________________________________________________________________________________________________________________

.. _Version:

Version
^^^^^^^

Lists the luma version that the current machine is on.

Example:

.. code-block:: bash
   
    $ luma version

Response:

.. code-block:: bash

    Lumavate CLI Version: 0.8.9

Options: 
 * ``--help``

_______________________________________________________________________________________________________________________________________

.. _Widget:

Widget
^^^^^^

Commands that add, modify, share, and delete widget containers.

.. _Widget Access:

Access
++++++

 Shares and unshares a widget container with child organizations.

 Example:

 .. code-block:: bash
   
     $ luma widget access --add 99
       Profile: dragon
       Widget: 999
 
 Response:
 
 .. code-block:: bash
 
     failed sharedWith          unsharedFrom resultingGrantees
     []     [{'granteeId': 99}] []           ['Dragon Command Center']
     
 Options: 
  * ``-p, --profile "STRING"``
  * ``-w, --widget ID``
  * ``--add ID``
  * ``--rm ID``
  * ``--absolute ID``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Widget Add:

Add
+++

 Adds a widget container.

 Example:

 .. code-block:: bash
   
     $ luma widget add
       Profile: dragon
       Name: Hydra
       Url Ref: hydra
 
 Response:
 
 .. code-block:: bash
 
     id  name  urlRef createdAt
     999 Hydra hydra  02/22/19 20:28:17
     
 Options: 
  * ``-p, --profile "STRING"``
  * ``--name "STRING"``
  * ``--url-ref "LOWERCASE STRING"``
  * ``-path, --icon-file "FILE PATH"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"`` 
  * ``--json`` 
  * ``--table`` 
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Widget Ls:

Ls
++

 Lists all the widget containers in an organization associated with the specified profile. 

 Example:

 .. code-block:: bash
   
     $ luma widget ls
       Profile: dragon
 
 Response:
 
 .. code-block:: bash
 
     id  name  urlRef    createdAt
     999 Hydra hydra     02/22/19 20:28:17
     99  European Dragon 02/22/19 20:28:17

 Options: 
  * ``-p, --profile "STRING"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"`` 
  * ``--filter "{JSON VALUE=SPECIFIC VALUE}"`` 
  * ``--page INTAGER``
  * ``--pagesize INTAGER``
  * ``--json`` 
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Widget Rm:

Rm
++

 Removes a widget container.

 Example:

 .. code-block:: bash
   
     $ luma widget rm
       Profile: dragon
       Widget: 999
 
 Response:
 
 .. code-block:: bash
 
     id  name  urlRef createdAt
     999 Hydra hydra  02/22/19 20:38:07

 Options: 
  * ``-p, --profile "STRING"``
  * ``-w, --widget ID``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table`` 
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Widget Update:

Update
++++++

 Updates a widget container’s name or image.

 Example:

 .. code-block:: bash
   
     $ luma widget update --name "European Dragon"
       Profile: dragon
       Widget: 999
 
 Response:
 
 .. code-block:: bash
 
     id  name            urlRef createdAt
     999 European Dragon hydra  02/22/19 20:38:07

 Options: 
  * ``-p, --profile "STRING"``
  * ``-w, --widget ID``
  * ``--name "STRING"``
  * ``-path, --icon-file "FILE PATH"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``  
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

_______________________________________________________________________________________________________________________________________

.. _Widget-version:

Widget-version
^^^^^^^^^^^^^^

Commands that add, modify, and delete widget versions.

.. _Widget Add:

Add
+++

 Adds a version to a widget container.

 Example:

 .. code-block:: bash
   
     $ luma widget-version add
       Profile: dragon
       Widget: 999
       Label: prod 
       Version Number: 9.9.9
       Widget File Path: "C:\fantasy\creatures\dragons\hydra.gz"
       Port: 8080 
 
 Response:
 
 .. code-block:: bash
 
     Uploading image to Lumavate
     Image Size: 179.87 MB
     id  actualState versionNumber label createdAt
     999 created     9.9.9         prod  02/22/19 20:46:08
     
 Options: 
  * ``-p, --profile "STRING"``
  * ``--port INTAGER``
  * ``-w, --widget ID``
  * ``-path, --widget-file-path "FILE PATH"``
  * ``-image, --docker-image "FILE PATH"``
  * ``-fv, --from-version INTAGER (*.*.*)``
  * ``-v, --version INTAGER (*.*.*)``
  * ``--patch INTAGER``
  * ``--minor INTAGER``
  * ``--major INTAGER``
  * ``--env-var "{"STRING":"KEY"}"``
  * ``-l, --label "[dev, old, prod]"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Widget-version Exec:

Exec
++++

 Sends commands directly to Docker. For more information about Docker commands, consult the `Docker documentation <https://docs.docker.com/engine/reference/commandline/docker/>`_.

 Example:

 .. code-block:: bash
   
     $ luma widget-version exec '<<Docker Command>>'
       Profile: dragon
       Widget: 999
       Version Number: 9.9.9

 Options: 
  *	``-p, --profile "STRING"``
  *	``-w, --widget ID``
  *	``-v, --version INTAGER (*.*.*)``
  *	``--target [one, all]``
  *	``--json``
  *	``--table``
  *	``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Widget-version Logs:

Logs
++++

 Returns the logs for a widget version.

 Example:

 .. code-block:: bash
   
     $ luma widget-version logs
       Profile: dragon
       Widget: 999
       Version Number: 9.9.9
 
 Response:
 
 .. code-block:: bash
 
     | ___ \
     | |_/ / ___ ___
     | ___ \ / _ \ / _ \
     | |_/ /| __/| __/
     \____/ \___| \___| v1.10.0
     [21m[0m2019/02/22 20:48:24 [34m[1mINFO [21m[0m ▶ 0001 Using 'widget' as 'appname'
     2019/02/22 20:48:24 [34m[1mINFO [21m[0m ▶ 0002 Initializing watcher...
     github.com/Place/Repository/File
     widget/models
     widget/controllers
     widget/routers
     widget
     2019/02/22 20:48:26 [32m[1mSUCCESS [21m[0m ▶ 0003 Built Successfully!
     2019/02/22 20:48:26 [34m[1mINFO [21m[0m ▶ 0004 Restarting 'widget'...
     2019/02/22 20:48:26 [32m[1mSUCCESS [21m[0m ▶ 0005 './widget' is running...
     2019/02/22 20:48:26.774 [1;34m[I] [asm_amd64.s:2197] http server Running on http://:8080[0m
     2019/02/22 20:48:30.578 [1;44m[D] [server.go:2568] | 54.164.117.6|[42m 200 [0m| 127.084µs| match|[44m GET [0m /ic/hydra/discover/health r:/:ic/:url_ref/discover/health[0m
     
 Options: 

  * ``-p, --profile "STRING"``
  * ``-w, --widget ID``
  * ``-v, --version INTAGER (*.*.*)``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Widget-version Ls:

Ls
++

 Lists all the version for a widget container.

 Example:

 .. code-block:: bash
   
     $ luma widget-version ls
       Profile: dragon
       Widget: 999

 Response:
 
 .. code-block:: bash
 
     id  actualState versionNumber label createdAt
     999 running     9.9.9         prod  02/22/19 20:46:08
     99  running     9.9.99        old   02/22/19 20:46:08
     
 Options: 
  * ``-p, --profile "STRING"``
  * ``-w, --widget ID``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--filter "{JSON VALUE=SPECIFIC VALUE}"``
  * ``--page INTAGER``
  * ``--pagesize INTAGER``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

 .. note::
    Version number is filtered as ``"major=*&minor=*&patch=*"``.

.. _Widget-version Rm:

Rm
++

 Deletes a widget version. This cannot be done if a widget version is being used in an experience.

 Example:

 .. code-block:: bash
   
     $ luma widget-version rm
       Profile: dragon
       Widget: 999
       Version Number: 9.9.9

 Response:
 
 .. code-block:: bash
 
     id  versionNumber label createdAt
     999 9.9.9         prod  02/22/19 20:46:08
     
 Options: 
  * ``-p, --profile "STRING"``
  * ``-w, --widget ID``
  * ``-vm, --version-mask INTAGER (*.*.*)``
  * ``-v, --version INTAGER (*.*.*)``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table`` 
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Widget-version Start:

Start
+++++

 Starts a widget version.

 Example:

 .. code-block:: bash
   
     $ luma widget-version start
       Profile: dragon
       Widget: 999
       Version Number: 9.9.9

 Response:
 
 .. code-block:: bash
 
     id  Current State Version # Created At
     999 running       9.9.9     02/22/19 20:46:08

 Options: 
  * ``-p, --profile "STRING"``
  * ``-w, --widget ID``
  * ``-v, --version INTAGER (*.*.*)``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Widget-version Stop:

Stop
++++

 Stops a widget version. This cannot be done if a widget version is being used in an experience.

 Example:

 .. code-block:: bash
   
     $ luma widget-version stop
       Profile: dragon
       Widget: 999
       Version Number: 9.9.9

 Response:
 
 .. code-block:: bash
 
     id  Current State Version # Created At
     999 stopped       9.9.9     02/22/19 20:46:08
     
 Options: 
  * ``-p, --profile "STRING"``
  * ``-w, --widget ID``
  * ``-v, --version INTAGER (*.*.*)``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table``
  * ``--help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Widget-version Update:

Update
++++++

 Updates a widget version’s label.

 Example:

 .. code-block:: bash
   
     $ luma widget-version update -l dev
       Profile: dragon
       Widget: 999
       Version Number: 9.9.9

 Response:
 
 .. code-block:: bash
 
     id  versionNumber label createdAt
     999 9.9.9         dev   02/22/19 20:46:08
  
 Options: 
  * ``-p, --profile "STRING"``
  * ``-w, --widget ID``
  * ``-v, --version INTAGER (*.*.*)``
  * ``-l, --label "[dev, old, prod]"``
  * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
  * ``--json``
  * ``--table``
  * ``–help``

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

_______________________________________________________________________________________________________________________________________

.. _Ls Filters:

Ls Filters
^^^^^^^^^^^

Limits Ls search results by:

 * :ref:`Greater Than <Ls Commands gt>`
 * :ref:`Less Than <Ls Commands lt>`
 * :ref:`Greater Than or Equal To <Ls Commands gte>`
 * :ref:`Less Than or Equal To <Ls Commands lte>`
 * :ref:`Containing <Ls Commands ct>`

.. _Ls Commands gt:

Greater Than (gt)
+++++++++++++++++

 Looks for anything that contains more than the specified value. 

 example:

 .. code-block:: bash
   
    $ luma profile ls --filter “name=gt:dragon”
    
 Response:
 
 .. code-block:: bash
 
    profileName env     orgName       orgId
    dragon-two  Fantasy Dragon Studio 9

.. _Ls Commands lt:

Less Than (lt)
++++++++++++++

 Looks for anything that contains less than the specified value.

 example:

 .. code-block:: bash
   
    $ luma profile ls --filter “name=lt:dragon”
    
 Response:
 
 .. code-block:: bash
 
    profileName env     orgName       orgId
    drag        prod    Other Studio  3

.. _Ls Commands gte:

Greater Than Or Equal To (gte)
++++++++++++++++++++++++++++++

 Looks for anything that contains either the specified value or more than the specified value.

 example:

 .. code-block:: bash
   
    $ luma profile ls --filter “name=gte:dragon”
    
 Response:
 
 .. code-block:: bash
 
    profileName env     orgName                orgId
    dragon      Fantasy Dragon Command Center  99
    dragon-two  Fantasy Dragon Studio          9

.. _Ls Commands lte:

Less Than Or Equal To (lte)
+++++++++++++++++++++++++++

 Looks for anything that contains either the specified value or less than the specified value.

 example:

 .. code-block:: bash
   
    $ luma profile ls --filter “name=lte:dragon”

 Response:
 
 .. code-block:: bash
 
    profileName env     orgName                orgId
    dragon      Fantasy Dragon Command Center  99
    drag        prod    Other Studio           3
    
.. _Ls Commands ct:

Containing (ct)
+++++++++++++++

 Looks for anything that contains the specified value.

 example:

 .. code-block:: bash
   
    $ luma profile ls --filter “name=ct:dragon”
    
 Response:
 
 .. code-block:: bash
 
    profileName env     orgName                orgId
    dragon      Fantasy Dragon Command Center  99
    dragon-two  Fantasy Dragon Studio          9

_______________________________________________________________________________________________________________________________________

.. _Version Commands:

Version Commands
^^^^^^^^^^^^^^^^

Commands that modify the CLI or luma version.

.. _Version Commands Install:

Install
+++++++

 Installs luma.

 example: 

 .. code-block:: bash
   
    $ pip3 install luma

.. _Version Commands Upgrade:

Upgrade
+++++++

 Updates the version of luma on the current machine. 

 example:

 .. code-block:: bash
   
    $ pip3 install luma --upgrade

.. _Version Commands Help:

Help
++++

 Describes and lists the possible subcommands for any command. This can be done by running any command without passing in any options or by passing in the ``--help`` flag.

 example:

 .. code-block:: bash
    
     $ luma
     
     OR 
     
     $ luma <<Command>>
     
     OR
     
     $ luma <<Command>> --help 
     
     OR
     
     $ luma <<Command>> <<Sub-Command>> --help

_______________________________________________________________________________________________________________________________________

.. _Additional Info:

Additional Info
^^^^^^^^^^^^^^^

* Dates must be in the format: year-month-day
* Must include "" around all arguments
* Must include "&" between arguments when using multiple arguments
