
.. _CLI:

============
CLI
============

The Lumavate Command-line Interface (CLI) can be used to streamline many administrative tasks.

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

You will need to install `Python 3.1.1 or higher <https://www.python.org/downloads/>`_ in order to use the CLI. If you are on Windows, remember to click the “Add Python To Path” checkbox when installing Python.  

It is recommended that you install `Gitbash <https://git-scm.com/downloads>`_ as the CLI is written for and tested in a BASH shell. 

.. note::
   The CLI supports `ZSH <https://sourceforge.net/projects/zsh/files/>`_. 

_______________________________________________________________________________________________________________________________________

.. _Installation:

Installation
------------
The CLI can be installed two different ways:

 #. :ref:`From Pip<Installation Pip>` (install ready-to-start)
 #. :ref:`From Source<Installation Source>` (install by manually downloading and configuring source files)

.. _Installation Pip:

From Pip
^^^^^^^^

 On Mac and Linux:
   
   Run the following command in a Bash or command prompt.
   
   .. code-block:: bash
     
      $ sudo pip3 install luma

 On Windows:
 
   Run the following command in a Bash or command prompt.
  
   .. code-block:: bash
     
      $ pip3 install luma

 The CLI should now be installed. Continue on to :ref:`Provisioning Credentials`. 

.. _Installation Source:

From Source
^^^^^^^^^^^

 Installing the CLI as a Non-admin:

  #. Clone the `CLI repo <https://pypi.org/project/luma/>`_.
  
  #. Unzip the file you just downloaded.
  
  #. Open a Bash or command prompt.
  
  #. CD into the CLI directory.
  
     .. Code-block:: bash
     
        $ cd C:/User/DownloadLocation/lumavate-cli-master/cli
        
  #. Run:
  
     .. code-block:: bash
        
        On Windows:
        
         $ pip3 install luma --user
        
        On Mac and Linux:
        
         $ sudo pip3 install luma --user
 
  #. Add the returned path URL to your system environment variables. 
   
     Example Response: 
   
     .. code-block:: bash
       
        The script luma.exe is installed in 'C:\ComputerName\UserName\AppData\Roaming\Python\Python37\Scripts' which is not on PATH. 
        Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
  
  #. The CLI should now be installed. Continue on to :ref:`Provisioning Credentials`. 
 
 Installing the CLI as an Admin:

  #. Clone the `CLI repo <https://pypi.org/project/luma/>`_.
  
  #. Unzip the file you just downloaded.
  
  #. Open a Bash or command prompt.
  
  #. CD into the CLI directory.
  
     .. Code-block:: bash
     
        $ cd C:/User/DownloadLocation/lumavate-cli-master/cli
        
  #. Run:
   
     .. code-block:: bash
     
        On Windows:
        
         $ pip3 install luma
        
        On Mac and Linux:
       
         $ sudo pip3 install luma

  #. The CLI should now be installed. Continue on to :ref:`Provisioning Credentials`. 
_______________________________________________________________________________________________________________________________________

.. _Provisioning Credentials:

Provisioning Credentials
-------------------------

The CLI requires two variables be configured in order to talk to the platform: :ref:`configuring environments<Provisioning Environments>` and :ref:`configuring profiles<Provisioning Profiles>`.
    
    * **Environments** know how to get and refresh tokens so the user stays authorized within the platform. They also set what command centers or studios the user has access to.
    * **Profiles** give the user a company context in a specific environment which is required by most of the platform API. They set what studio or command center the user is modifying.  

.. _Provisioning Environments:

Setting-Up Environments
^^^^^^^^^^^^^^^^^^^^^^^

 You can use either the :ref:`Lumavate pre-configured<environment preset configuration>` environment or you can :ref:`setup your own environment configuration<environment your own configuration>`.

.. _environment preset configuration:

 Using the preset configuration:

  #. Log into the command center you want to modify with the CLI.
  
     .. figure:: ../images/environmentselect.PNG
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
  #. The CLI should return the following showing that the new environment Prod has been created. Continue on to :ref:`Setting up Profiles <Provisioning Profiles>`. 
     
     .. code-block:: bash
     
         envName app                                                  audience                                 token
         prod    https://not-a-real-realm.place.lumavate-type.com     https://place.lumavate-type.com/notanapp place-lumavate-type.notarealtoken.com

     .. warning::
        If there are two environments with the same name, the newer version will overwrite the older version.
 
 .. _environment your own configuration:
 
 Using your own configuration:

  #. Log into the command center you want to modify with the CLI.
     
     .. figure:: ../images/environmentselect.PNG
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
       
         $ Env Name: <<What you want to name the environment>>
           App: <<environment Url>>
           Token: <<environment token>>
           Audience: <<envitoment audience>>
           Client id: <<user clientId>>
           Client secret: <<user clientSecret>>
          
  #. The CLI should return the following with the env name you specified listed with any other environments you have setup. Continue on to :ref:`Setting up Profiles <Provisioning Profiles>`. 
  
     .. code-block:: bash
     
         envName app                                                    audience                                    token
         Fantasy https://not-a-real-realm2.fantasy.lumavate-type.com    https://fantasy.lumavate-type.com/notanapp2 fantasy-lumavate-type.notarealtoken2.com

  .. note:: 
     The CLI uses Client ID and Client Secret to associate a user context to a machine. From this point forward, user will refer to the Client ID and Client Secret information used to setup the environment in the CLI. 

.. _Provisioning Profiles:
  
Setting up Profiles
^^^^^^^^^^^^^^^^^^^

 Profiles allow users to send commands to a specific organization. Most commands in the CLI require a profile. Profiles can be setup using the :ref:`Lumavate pre-set command<profile preset configuration>` or using :ref:`your own configuration<profile your own configuration>`. 

 You will need to have :ref:`configured an environment<Provisioning Environments>` on your machine through the CLI to configure a profile.  

.. _profile preset configuration:

 Using a preset configuration:

  #. Log into a Lumavate command center.
  
     .. figure:: ../images/environmentselect.PNG
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
  
  #. You will be prompted to name the profile. Profiles will be used to reference a command center or studio. The prompt should look like this:
   
     .. code-block:: bash
       
         Profile Name: <<What you want to call the profile. Cannot include spaces or special characters.>>

     .. warning::
        If there are two profiles with the same name, the newer version will overwrite the older version. Profiles in different environments can have the same name without overwriting each other.  
    
  #. You will then be presented with a list of organizations associated with the preset Lumavate environment. Pick the one you want to associate with this profile, and enter its ID number. The prompt should look like this:
   
     .. code-block:: bash
       
          id Org Name                  Org Type Test Org
          35 Sample Command Center     dev      None
          49 Sample Studio             studio   False

          Org ID you want to associate with this profile: <<org id>>
  
  #. The CLI should return the following with the environment, org name, and org id you associated the profile with. Continue on to the :ref:`CLI Syntax<CLI Syntax>` for more help.
  
    .. code-block:: bash
    
        Environment Org Name              Org ID
        prod        Sample Command Center 35

.. _profile your own configuration:

 Using your own configuration:

  #. In your Bash window, run:
   
     .. code-block:: bash
       
         $ luma profile add

  #. You will be prompted to name your profile. Profiles will be used to reference a command center or studio. The prompt should look like this:
   
     .. code-block:: bash
       
         Profile Name: <<What you want to call the profile. Cannot include spaces or special characters.>>
     
     .. warning::
        If there are two profiles with the same name, the newer version will overwrite the older version. Profiles in different environments can have the same name without overwriting each other.  

  #. A list of environments will appear. Select which environment you wish to associate with the profile, and enter its name. The prompt should look like this:
   
     .. code-block:: bash
       
         Env Name App                                              Audience                                    Token
         Fantasy  https://not-a-realm2.fantasy.lumavate-type.com   https://fantasy.lumavate-type.com/notanapp2 fantasy-lumavate-type.notarealtoken2.com
         prod     https://not-a-realm.place.lumavate-type.com      https://place.lumavate-type.com/notanapp    place-lumavate-type.notarealtoken.com

          Env: <<Env Name>>

  #. A list of organizations will appear. Pick the one you want to edit with this profile, and enter its ID. The prompt should look like this:
   
     .. code-block:: bash
       
         id  Org Name                  Org Type Test Org
         99  Dragon Command Center     dev      None
         999 Child Command Center      dev      None
         9   Dragon Studio             studio   False

          Org ID you want to associate with this profile: <<org id>>
         
  #. The CLI should return the following with the environment, org name, and org id you associated the profile with. Continue on to the :ref:`CLI Syntax<CLI Syntax>` for more help.
  
    .. code-block:: bash
    
        Environment Org Name              Org ID
        Fantasy     Dragon Command Center 9 

 .. note::
    While running the profile command, you will have the option to associate the new profile to any organization the user has access to regardless of the command center you are currently in.

_______________________________________________________________________________________________________________________________________

.. _CLI Syntax:

CLI Syntax
----------

The CLI allows users to interact with the Lumavate platform from a terminal. For setup instructions, look at the `Github readme <https://github.com/Lumavate-Team/documentation/blob/master/CLI.rst>`_ or the :ref:`CLI setup documentation <CLI>`. All the main commands are listed in the Command Index below. Each of the main commands has their subcommands listed in their section. 

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
    
     {"payload": {"data": {"createdAt": "2019-02-22T16:17:30.165138+00:00", "createdBy": 99, "expand": {"experiences": 0, "grantees": [], "publisher": {"id": 9, "instanceType": "cc", "isTest": null, "name": "Dragon Command Center"}}, "id": 9999, "image": null, "integrationCloudId": 1, "isOwner": true, "lastModifiedAt": "2019-02-22T16:17:30.165109+00:00", "lastModifiedBy": 99, "name": "Fire Breathing", "premium": false, "type": "widget", "urlRef": "fire", "versionInfo": {"latest": {"createdAt": null, "createdBy": null, "id": null, "label": null, "lastModifiedAt": null, "lastModifiedBy": null, "manageUrl": null, "versionNumber": null}}}}}

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do. 
 
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
  
      {"payload": {"currentItemCount": 2, "data": [{"createdAt": "2019-02-22T16:17:19.878312+00:00", "createdBy": 90, "expand": {"experiences": 0, "grantees": [], "publisher": {"id": 9, "instanceType": "cc", "isTest": null, "name": "Dragon Command Center"}}, "id": 9999, "image": {"key": "containers/dragon/icons/78130f31", "preview": "https://s3.amazonaws.com/from.through.to.com/containers/dragon/icons/78130f31?AWSAccessKeyId=NotAnAccessKeyId5Q&Signature=nota Signaturev8xyp8cnhE%3D&Expires=999993222"}, "integrationCloudId": 1, "isOwner": true, "lastModifiedAt": "2019-02-22T16:17:19.878294+00:00", "lastModifiedBy": 99, "name": "Dragon", "premium": false, "type": "widget", "urlRef": "dragon", "versionInfo": {"latest": {"createdAt": "2019-02-22T16:23:05.318677+00:00", "createdBy": 99, "id": 9999, "label": "prod", "lastModifiedAt": "2019-02-22T16:23:05.318646+00:00", "lastModifiedBy": 99, "manageUrl": null, "versionNumber": "9.9.9"}, "recommended": {"createdAt": "2019-02-22T16:23:05.318677+00:00", "createdBy": 90, "id": 9999, "label": "prod", "lastModifiedAt": "2019-02-22T16:23:05.318646+00:00", "lastModifiedBy": 99, "manageUrl": null, "versionNumber": "9.9.9"}}}, {"createdAt": "2019-02-22T16:17:30.165138+00:00", "createdBy": 99, "expand": {"experiences": 0, "grantees": [], "publisher": {"id": 9, "instanceType": "cc", "isTest": null, "name": "Dragon Command Center"}}, "id": 9999, "image": null, "integrationCloudId": 1, "isOwner": true, "lastModifiedAt": "2019-02-22T16:17:30.165109+00:00", "lastModifiedBy": 99, "name": "Fire Breathing", "premium": false, "type": "widget", "urlRef": "fire", "versionInfo": {"latest": {"createdAt": null, "createdBy": null, "id": null, "label": null, "lastModifiedAt": null, "lastModifiedBy": null, "manageUrl": null, "versionNumber": null}}}], "nextPage": null, "page": 1, "pageSize": 100, "prevPage": null, "totalItems": 2, "totalPages": 1}}

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
    
     {"payload": {"data": {"createdAt": "2019-02-22T15:56:21.722668", "createdBy": 99, "expand": {"experiences": 0, "grantees": [], "publisher": {"id": 9, "instanceType": "cc", "isTest": null, "name": "Dragon Command Center"}}, "id": 9, "image": {"key": "containers/dragon/icons/af7ef4a6", "integrationCloudId": 1, "isOwner": true, "lastModifiedAt": "2019-02-22T15:56:21.722632", "lastModifiedBy": 99, "name": "Dragon", "premium": false, "type": "widget", "urlRef": "dragon", "versionInfo": {"latest": {"createdAt": null, "createdBy": null, "id": null, "label": null, "lastModifiedAt": null, "lastModifiedBy": null, "manageUrl": null, "versionNumber": null}}}}}

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * -  ``-d, --data "{JSON}, {JSON}"``
       - The JSON payload/body of the call.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
 
     {"payload": {"data": {"createdAt": "2019-02-22T16:03:22.950331", "createdBy": 99, "expand": {"experiences": 0, "grantees": [], "publisher": {"id": 9, "instanceType": "cc", "isTest": null, "name": "Dragon Command Center"}}, "id": 1675, "image": null, "integrationCloudId": 1, "isOwner": true, "lastModifiedAt": "2019-02-22T16:03:22.950312", "lastModifiedBy": 99, "name": "Fire Breathing", "premium": false, "type": "widget", "urlRef": "fireball", "versionInfo": {"latest": {"createdAt": null, "createdBy": null, "id": null, "label": null, "lastModifiedAt": null, "lastModifiedBy": null, "manageUrl": null, "versionNumber": null}}}}}

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * -  ``-d, --data "{JSON}, {JSON}"``
       - The JSON payload/body of the call.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. note::
    API paths cannot include sort criteria.
_______________________________________________________________________________________________________________________________________

.. _Component-set:

Component-set
^^^^^^^^^^^^^

Commands that create, modify, share, and delete component set containers.

.. _Component-set Access:

Access
++++++

 Shares and unshares component set containers with child organizations.

 Example:

 .. code-block:: bash
   
     $ luma component-set access --add 9
       Profile: dragon
       Component set: 999

 Response:
 
 .. code-block:: bash
 
     failed sharedWith          unsharedFrom resultingGrantees
     []     [{'granteeId': 9}]  []           ['Dragon Studio']

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-cs, --component-set ID``
       - The component set container you want to edit. You can pass either the ID or UrlRef.
     * - ``--add ID``
       - The studio or command center you want to **share** with. You can pass either the ID or Name.
     * - ``--rm ID``
       - The studio or command center you want to **unshare** with. You can pass either the ID or Name.
     * - ``--absolute ID``
       - Unshares the tool with all organizations and then shares the tool with the specified organizations. *Ignores* ``--add`` *and* ``--rm`` *commands*. You can pass either the ID or Name.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{failed} {unsharedFrom}"`` 
     * - ``--json``
       - Returns the raw JSON payload.
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Component-set Add:

Add
+++

 Adds a component set container. 

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

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``--name "STRING"``
       - What you want to call the component set container. The name will appear in the command center and studio.
     * - ``--url-ref "STRING"``
       - What the tool will be referenced by in URLs. For example: urlToExperience.com/url-ref or ic/url-ref. It can contain only lowercase letters, numbers, and dashes.
     * - ``-path, --icon-file "FILE PATH"``
       - The absolute path where the icon SVG file is located. For example: ``-path "C:/Users/User/Desktop/Folder/icon.SVG"``.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``
     * - ``--json``
       - Returns the raw JSON payload.
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Component-set Ls:

Ls
++

 Lists all component set containers in the command center associated with the specified profile. 

 Example:

 .. code-block:: bash
   
     $ luma component-set ls
       Profile: dragon
 
 Response:
 
 .. code-block:: bash
 
     id  name          urlRef       createdAt
     999 Fire Breath   firebreath   02/22/19 16:36:09
     99  Frosty Breath frostybreath 02/22/19 16:36:09

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{createdBy} {id}"``
     * - ``--filter "JSON VALUE=SPECIFIC VALUE"``
       - Returns results that match the filter criteria. For example: ``--filter "urlRef=firebreath"``. Additional filter options are available in the :ref:`Ls Filters` section.
     * - ``--page INTEGER`` 
       - The results page you want to view.
     * - ``--pagesize INTEGER``
       - The number of results you want to show per page.
     * - ``--json``
       - Returns the raw JSON payload.
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Component-set Rm:

Rm
++

 Deletes a component set container. This can only be done after all versions in the container have been deleted.

 Example:

 .. code-block:: bash
   
     $ luma component-set rm
       Profile: dragon
       Component set: 999
 
 Response:
 
 .. code-block:: bash
 
     id  name        urlRef      createdAt
     999 Fire Breath firebreath  02/22/19 16:36:09

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-cs, --component-set ID``
       - The component set container you want to edit. You can pass either the ID or UrlRef.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{createdBy} {urlRef}"`` 
     * - ``--json``
       - Returns the raw JSON payload.
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Component-set Update:

Update
++++++

 Updates the name or image of a component set container. 

 Example:

 .. code-block:: bash
   
     $ luma component-set update --name "Frosty Breath"
       Profile: dragon
       Component set: 999
 
 Response:
 
 .. code-block:: bash
 
    id  name          urlRef      createdAt
    999 Frosty Breath firebreath  02/22/19 16:36:09

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-cs, --component-set ID``
       - The component-set container you want to edit. You can pass either the ID or UrlRef.
     * - ``--name "STRING"``
       - The new name for the component set container. The name will appear in the command center and studio. 
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{createdBy} {id}"``
     * - ``--json``
       - Returns the raw JSON payload.
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` is deprecated. 
    Use ``--format`` to see JSON values organized in table format.
_______________________________________________________________________________________________________________________________________

.. _Component-set-version:

Component-set-version
^^^^^^^^^^^^^^^^^^^^^

Commands that create, modify, and delete component set versions.

.. _Component-set-version Add:

Add
+++

 Adds a version to a component set container.  

 Example:

 .. code-block:: bash
   
     $ luma component-set-version add 
       Profile: dragon
       Component set: 999
       Component set file: C:\fantasy\creatures\dragons\firebreather.zip
       Label: prod
       Version: 9.9.9
 
 Response:
 
 .. code-block:: bash
    
     Image Size: 6.91 KB
     Uploading Component Set Version to Lumavate
     id  versionNumber directIncludes directCssIncludes label createdAt
     999 9.9.9         0              0                 prod  02/22/19 16:54:00

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-cs, --component-set ID``
       - The component set container you want to edit. You can pass either the ID or UrlRef.
     * - ``-path, --component-set-file-path "FILE PATH"``
       - The absolute path where the component set zip file is located. For example: ``-path "C:/Users/User/Desktop/Folder/file.zip"``. 
     * - ``-fv, --from-version INTEGER "*.*.*"``
       - The version you want to use as a base for the current version. This will use the specified version’s port, label, variables, and image unless otherwise specified. Use a * to indicate the most recent version. For example, ``--from-version "9.9.*"`` will take the most recent version that has a major and minor value of 9. ``--from-version "*.*.*"`` will take the most recent version. 
     * - ``-v, --version INTEGER "*.*.*"``
       - What you want the component set version number to be. For example, ``--version "9.9.9"``.
     * - ``--patch``
       - Sets the version number by increasing the from-version’s number patch value by one. For example, ``--from-version "1.1.1" --patch`` sets the version number to 1.1.2.
     * - ``--minor``
       - Sets the version number by increasing the from-version’s number minor value by one. For example, ``--from-version "1.1.1" --minor`` sets the version number to 1.2.0.
     * - ``--major``
       - Sets the version number by increasing the from-version number’s major value by one. For example, ``--from-version "1.1.1" --major`` sets the version number to 2.0.0.
     * - ``--css-includes "STRING"``
       - CSS includes for the version.
     * - ``--direct-includes "STRING"``
       - Direct includes for the version. 
     * - ``-l, --label "[prod|dev|old]"``
       - The status of the version as either ready-for-production, in-development, or deprecated respectively.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {CreatedBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload.
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` is deprecated. 
    Use ``--format`` to see JSON values organized in table format.

 .. warning::
    File paths with spaces in them may need to be specified in the main command using the ``-path`` option so as to preserve the spaces.

.. _Component-set-version Components:

Components
++++++++++

 Returns the JSON of a component set version. 

 Example:

 .. code-block:: bash
   
     $ luma component-set-version components
       Profile: dragon
       Component set: 999
       Version: 9.9.9
      
 Response:
 
 .. code-block:: bash
 
     {"payload": {"data": {"componentSetId": 999, "createdAt": "2019-02-22T16:54:00.511074+00:00", "createdBy": 99, "directCssIncludes": [], "directIncludes": [], "distribution": "/iot/v1/dynamic-component-sets/firebreath/9.9.9", "expand": {"components": [{"icon": "/iot/v1/dynamic-component-sets/firebreath/9.9.9/icons/material.svg", "label": "Fire Breath Properties", "properties": [{"label": "Color", "name": "firecolor", "type": "color"}], "section": "Power Properties", "tags": ["body"], "template": "<div class=\"firepower\"><svg class=\"fire-image\" color=\"{{ componentData.firecolor }}></svg></div>", "type": "material-input-select"}]}, "id": 999, "label": "prod", "lastModifiedAt": "2019-02-22T16:54:00.511040+00:00", "lastModifiedBy": 99, "major": 9, "minor": 9, "patch": 9, "state": "available", "versionNumber": "9.9.9"}}}

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-cs, --component-set ID``
       - The component set container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the component set you want to view. For example, ``--version "9.9.9"``.
     * - ``--json``
       - Returns the raw JSON payload.
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` and ``--json`` are deprecated.
    The CLI will return the JSON file by default. The file cannot be organized by the CLI.

.. _Component-set-version Ls:

Ls
++

 Lists all versions in a component set container.

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

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-cs, --component-set ID``
       - The component set container you want to edit. You can pass either the ID or UrlRef.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {CreatedBy}"``. 
     * - ``--filter "JSON VALUE=SPECIFIC VALUE"``
       - Returns results that match the filter criteria. For example: ``--filter "label=prod"``. Additional filter options are available in the :ref:`Ls Filters` section.
     * - ``--page INTEGER``
       - The results page you want to view.
     * - ``--pagesize INTEGER``
       - The number of results you want to show per page.
     * - ``--json``
       - Returns the raw JSON payload.
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

 .. note::
    Version number is filtered as "major=*&minor=*&patch=*".

.. _Component-set-version Rm:

Rm
++

 Deletes a version from a component set container.

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
 
 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-cs, --component-set ID``
       - The component set container you want to edit. You can pass either the ID or UrlRef.
     * - ``-vm, --version-mask INTEGER "*.*.*"``
       - Removes all version with that major, minor, or path. Use a * to indicate all. For example, ``--version-mask "9.*.*"`` will delete all versions that have a major value of 9. ``--version-mask "*.*.*"`` will delete all version.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the component set you want to remove. For example, ``--version "9.9.9"``.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {CreatedBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload.
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Component-set-version Update:

Update
++++++

 Updates the label of a component set version.

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
    
 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-cs, --component-set ID``
       - The component set container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the component set you want to edit. For example, ``--version "9.9.9"``.
     * - ``-l, --label "[prod|dev|old]"```
       - The new status of the version. It can either be ready-for-production, in-development, or deprecated respectively.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {CreatedBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload.
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
     
 .. list-table:: Options 
     :widths: 10 20

     * - ``--env-name "STRING"``
       - What you want to call the environment. The name will only appear in the CLI.
     * - ``--app "LINK"``
       - The domain where the studio and command centers you want to work with are located.
     * - ``--token "LINK"``
       - A value the platform produces to authenticate the environment. 
     * - ``--audience "LINK"``
       - Auth value used to identify the environment provided by the platform. 
     * - ``--client-id "ID"``
       - The user’s ID provided by the platform. The environment will have access to the same studios and command centers as the user whose ID was used. This must match the client secret for the environment to be created. 
     * - ``--client-secret "SECRET"``
       - The user’s secret provided by the platform. It must match the client ID for the environment to be created. 
     * - ``--json``
       - Returns the raw JSON payload.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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

    
 .. list-table:: Options 
     :widths: 10 20

     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{app} {audience}"``. 
     * - ``--json``
       - Returns the raw JSON payload.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

.. _Env Rm:

Rm
++

Removes an environment. The user will be asked if they want to delete the profiles associated with the environment. If the user sends yes, the environment and associated profiles will be deleted. If the user sends no, the environment will be deleted, but the associated profiles will be retained. Any response that is not understood defaults to no.  

 Example:

 .. code-block:: bash
   
     $ luma env rm Fantasy
       The following profiles are using this environment. Would you like to delete these profiles?
       ['dragon', 'dragon-two']

       Yes/No: Yes

 
 Response: 
 
 .. code-block:: bash
     
    Deleted Environment: Fantasy

    Deleted Profiles: ['dragon', 'dragon-two']

 .. list-table:: Options 
     :widths: 10 20

     * - ``--force``
       - Skips the confirmation when deleting environments with profiles. 
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
       Export file: C:\fantasy\creatures\dragon\egg.json
       Label: Creatures
 
 Response:
 
 .. code-block:: bash
 
     Saved to C:\fantasy\creatures\dragons\egg.json
 
 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-l, --label "STRING"``
       - The experience's name in the studio. 
     * - ``-n, --name "STRING"``
       - The experience's referenced name in the studio designer URL.
     * - ``-path, --export-file "FILE PATH"``
       - The absolute path where the experience JSON file will be saved. For example: ``-path "C:/Users/User/Desktop/experience.json"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
      Import file: C:\fantasy\creatures\dragons\egg.json
      Collection Name: Creatures
 
 Response:
 
 .. code-block:: bash
 
     Uploading file...
     File uploaded.

     Successfully imported experience.
     
 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-l, --label "STRING"``
       - What the experience's name will be in the studio. 
     * - ``-d, --description "STRING"``
       - What description will accompany the experience. This will appear when studio users hover over an experience. 
     * - ``-ci, --collection-id ID``
       - The collection where you want to add the experience. The collection must exist before importing the experience.
     * - ``--device "[mobile|tablet|web]"``
       - What device the experience will be previewed on.
     * - ``-cn, --collection-name "STRING"``
       - The name of the collection where you want to add the experience. The collection must exist before importing the experience.  
     * - ``-ac, --activation-code "STRING"``
       - What the activation code will be for the experience. It can contain only lowercase alphanomics with no special characters or spaces. There is a max length of 20.
     * - ``-t, --template``
       - Makes the experience a template.
     * - ``-ru, --redirect-url "URL"``
       - Adds a redirect URL to the experience. The experience will be redirected to the URL when the experience is rendered.
     * - ``-path, --import-file "FILE PATH"``
       - The absolute path where the experience file is located. For example: ``-path "C:/Users/User/Desktop/Folder/experience.json"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.
 
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

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--filter "JSON VALUE=SPECIFIC VALUE"``
       - Returns results that match the filter criteria. For example: ``--filter "name=Dragons"``. Additional filter options are available in the :ref:`Ls Filters` section.
     * - ``--page INTEGER``
       - The results page you want to view.
     * - ``--pagesize INTEGER``
       - The number of results you want to show per page.
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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

.. list-table:: Options 
    :widths: 10 20
     
    * - ``-p, --profile "STRING"``
      - The profile associated with the studio or command center you want to edit.
    * - ``-f, --format "{JSON VALUE}"``
      - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
    * - ``--filter "JSON VALUE=SPECIFIC VALUE"``
      - Returns results that match the filter criteria. For example: ``--filter "name=Creatures"``. Additional filter options are available in the :ref:`Ls Filters` section.
    * - ``--page INTEGER``
      - The results page you want to view.
    * - ``--pagesize INTEGER``
      - The number of results you want to show per page.
    * - ``--json``
      - Returns the raw JSON payload. 
    * - ``--help``
      - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

_______________________________________________________________________________________________________________________________________

.. _Microservice:

Microservice
^^^^^^^^^^^^

Commands that create, modify, share, and delete microservice containers.

.. _Microservice Access:

Access
++++++

 Shares or unshares a microservice container with child organizations. 

 Example:

 .. code-block:: bash
   
     $ luma microservice access --add 99
       Profile: dragon
       Container: 999
 
 Response:
 
 .. code-block:: bash
 
     failed sharedWith          unsharedFrom resultingGrantees
     []     [{'granteeId': 99}] []           ['Dragon Studio']
     
 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The microservice container you want to share or unshare. You can pass either the ID or UrlRef.
     * - ``--add ID``
       - The studio or command center with whom you want to **share**. You can pass either the ID or Name.
     * - ``--rm ID``
       - The studio or command center with whom you want to **unshare**. You can pass either the ID or Name.
     * - ``--absolute ID``
       - Unshares the tool with all organizations and then shares the tool with the specified organizations. *Ignores* ``--add`` *and* ``--rm`` *commands*. You can pass either the ID or Name.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{sharedWith} {failed}"``.
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table`` 
       - Returns a table with several basic JSON values.
     * - ``--current``
       - Lists the organizations the specified tool is shared with.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``--name "STRING"``
       - What you want to call the microservice container. The name will appear in the command center and studio. 
     * - ``--url-ref "STRING"``
       - What the microservice will be referenced by in URLs. For example: https://urlToExperience.com/url-ref or ic/url-ref.
     * - ``-path, --icon-file "FILE PATH"``
       - The absolute path where the icon SVG file is located. For example: ``-path "C:/Users/User/Desktop/Folder/icon.SVG"``. 
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``.
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table`` 
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit. 
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``.
     * - ``--filter "JSON VALUE=SPECIFIC VALUE"``
       - Returns results that match the filter criteria. For example: ``--filter "urlRef=world"``. Additional filter options are available in the :ref:`Ls Filters` section.
     * - ``--page INTEGER``
       - The results page you want to view.
     * - ``--pagesize INTEGER``
       - The number of results you want to show per page.
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table`` 
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
       Container: 999
 
 Response:
 
 .. code-block:: bash
 
     id  name              urlRef    createdAt
     999 Dragon Fact Sheet factsheet 02/22/19 19:21:49
     
 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The microservice container you want to remove. You can pass either the ID or UrlRef.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``.
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table`` 
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
       Container: 999 
 
 Response:
 
 .. code-block:: bash
 
     id  name           urlRef    createdAt
     999 World Building factsheet 02/22/19 19:31:05

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The microservice container you want to remove. You can pass either the ID or UrlRef.
     * - ``--name "STRING"``
       - The new name for the microservice container. The name will appear in the command center and studio. 
     * - ``-path, --icon-file "FILE PATH"``
       - The absolute path where the new icon SVG file is located. For example: ``-path "C:/Users/User/Desktop/Folder/icon.SVG"``. 
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``.
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table`` 
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
       Container: 999
       Label: prod
       Version: 9.9.9 
       Port: 5000
       Container-file-path: C:\fantasy\creatures\dragons\DragonFactSheet.gz
 
 Response:
 
 .. code-block:: bash
 
     Uploading image to Lumavate:
     Image Size: 59.43 MB
     id  actualState versionNumber label createdAt
     999 created     9.9.9         prod  02/22/19 19:40:59

     
 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The microservice container you want to edit. You can pass either the ID or UrlRef.
     * - ``--port INTEGER``
       - The port that the version will run on. This will either be set in your code or be your programming language’s default port.
     * - ``--editor-port INTEGER``
       - The editor port checked by the Visual Studio Code Luma extension. 
     * - ``--is-editable``
       - Marks the microservice version as editable. Editable versions can be edited through the Visual Studio Code Luma extension.
     * - ``-image, --docker-image "STRING"``
       - The name and tag of a microservice Docker container from the Docker daemon. Docker must be installed locally to use this option. For more information about installing Docker, please see :ref:`Docker set-up<Installing Locally>`. 
     * - ``-path, --container-file-path "FILE PATH"``
       - The absolute path where the microservice tar file is located. For example: ``-path "C:/Users/User/Desktop/Folder/microservice.tar"``. 
     * - ``-fv, --from-version INTEGER "*.*.*"``
       - The version you want to use as a base for the current version. This will use the specified version’s port, label, variables, and image unless otherwise specified. Use a * to indicate the most recent version. For example, ``--from-version "9.9.*"`` will take the most recent version that has a major and minor value of 9. ``--from-version "*.*.*"`` will take the most recent version.
     * - ``-v, --version INTEGER "*.*.*"``
       - What you want the microservice's version number to be. For example, ``--version "9.9.9"``.
     * - ``--patch INTEGER``
       - Sets the version number by increasing the from-version’s number patch value by one. For example, ``--from-version "1.1.1" --patch`` sets the version number to 1.1.2.
     * - ``--minor INTEGER``
       - Sets the version number by increasing the from-version’s number minor value by one. For example, ``--from-version "1.1.1" --minor`` sets the version number to 1.2.0.
     * - ``--major INTEGER``
       - Sets the version number by increasing the from-version number’s major value by one. For example, ``--from-version "1.1.1" --major`` sets the version number to 2.0.0.
     * - ``--env-var "{"STRING":"KEY"}"``
       - The name of the environmental variable followed by the key value. For more information, see the :ref:`environmental variables definition<Enviroment Variables>`. 
     * - ``-l, --label "[prod|dev|old]"``
       - The status of the version as either ready-for-production, in-development, or deprecated. respectively.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``.
     * - ``--json``
       - Returns the raw JSON payload.
     * - ``--table`` 
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` is deprecated. 
    Use ``--format`` to see JSON values organized in table format.

.. _Microservice-version Download:

Download
++++++++

 Downloads a zip file of an editable microservice version's Image.
 
 Example:
 
 .. code-block:: bash
 
     $ luma microservice-version download
       Profile: dragon
       Container: 999
       Version: 9.9.9
 
 Response:
 
 .. code-block:: bash
      
      % Total    % Received % Xferd  Average Speed    Time     Time      Time  Current
                                      Dload  Upload   Total    Spent     Left  Speed
    100 42275  100    42275 0     0    42275     0  0:00:01  0:00:01 --:--:--    42275
    
    File Location: C:\Users\User\Desktop\application.999999.zip  
 
 .. list-table:: Options
     :widths: 10 20
     
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The microservice container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the microservice you want to edit. For example, ``--version "9.9.9"``.
     * - ``--path "FILE PATH"``
       - The absolute path or the relative path from the Desktop where the microservice zip file will be saved. For example, ``--path "C:/Users/User/Desktop/Folder/microservice.zip"`` or ``--path "/Folder/microservice.zip"`` Defaults to the Desktop if no path is specified.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

.. _Microservice-version Exec:

Exec
++++

 Sends commands directly to Docker. For more information on Docker commands, consult the `Docker documentation <https://docs.docker.com/engine/reference/commandline/docker/>`_.

 Example:

 .. code-block:: bash
   
     $ luma microservice-version exec '<<Docker command>>' 
       Profile: dragon 
       Container: 999 
       Version Number: 9.9.9

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The microservice container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the microservice you want to edit. For example, ``--version "9.9.9"``.
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table`` 
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Microservice-version Logs:

Logs
++++

 Returns the logs for a microservice version. If the microservice version is editable, the editor logs will be followed. If the microservice version is read-only or is not editable, the production logs will be tailed. 

 Example:

 .. code-block:: bash
   
     $ luma microservice-version logs 
       Profile: dragon 
       Container: 999
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
    
 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The microservice container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the microservice whose logs you want to see. For example, ``--version "9.9.9"``.
     * - ``-n, --tail-number INTEGER``
       - The number of log lines you want to display.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
       Container: 999
 
 Response:
 
 .. code-block:: bash
 
     id  actualState versionNumber label createdAt
     999 stopped     9.9.9         prod  02/22/19 19:57:16

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The microservice container you want to edit. You can pass either the ID or UrlRef.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--filter "JSON VALUE=SPECIFIC VALUE"``
       - Returns results that match the filter criteria. For example: ``--filter "id=999"``. Additional filter options are available in the :ref:`Ls Filters` section.
     * - ``--page INTEGER``
       - The results page you want to view.
     * - ``--pagesize INTEGER``
       - The number of results you want to show per page.
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table`` 
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

 .. note::
    Version number is filtered as ``"major=*&minor=*&patch=*"``.

.. _Microservice-version Restart:

Restart
+++++++

 Restarts the microservice version's editor application without discarding code changes.
 
 Example:

 .. code-block:: bash
   
     $ luma microservice-version restart 
       Profile: dragon 
       Container: 999
       Version Number: 9.9.9

 Response:
 
 .. code-block:: bash
 
     {'payload': {'data': {'actualState': 'running', 'actualStateChangedAt': '2019-06-18T19:06:37.832178+00:00', 'containerId': 9999, 'createdAt': '2019-06-18T14:55:30.243397+00:00', 'createdBy': 99, 'desiredState': 'running', 'desiredStateChangedAt': '2019-06-18T16:24:06.846847+00:00', 'editorPort': None, 'enforceRoutes': True, 'env': {}, 'expand': {}, 'id': 9999, 'instanceCount': 1, 'isEditable': False, 'label': 'prod', 'lastActualStatePayload': {'childHasError': False, 'children': [{'childHasError': False, 'children': [], 'errorMessage': None, 'id': '9d999999', 'overallPercent': 100.0, 'percent': 100, 'summary': {'beginState': 'running', 'eventName': 'do_validate', 'message': 'Container Version 9.9.9 (ID:9999) started successfully'}}, {'childHasError': False, 'children': [], 'errorMessage': None, 'id': '9d99r99a', 'overallPercent': 100.0, 'percent': 100, 'summary': {'beginState': 'validating', 'eventName': 'validated'}}], 'errorMessage': None, 'id': '9d9rag9o', 'overallPercent': 100.0, 'percent': 100, 'summary': {'stateLog': ['running', 'validating', 'running']}}, 'lastModifiedAt': '2019-06-18T19:11:10.410143', 'lastModifiedBy': 99, 'major': 9, 'minor': 0, 'notes': None, 'patch': 9, 'platformVersion': 'v2', 'port': 9999, 'repositoryName': 'registry.realm.lumavate-type.com/factsheet', 'rewriteUrl': False, 'stateChangedAt': '2019-06-18T14:55:30.235871+00:00', 'tag': 'd9r9', 'versionNumber': '9.9.9'}}}

    
 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The microservice container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the microservice you want to restart. For example, ``--version "9.9.9"``.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

.. _Microservice-version Rm:

Rm
+++

 Removes a version from a microservice container.

 Example:

 .. code-block:: bash
   
     $ luma microservice-version rm
       Profile: dragon
       Container: 999
       Version: 9.9.9
 
 Response:
 
 .. code-block:: bash
 
     id  versionNumber label  createdAt
     999 9.9.9         prod   02/22/19 19:57:16
     
 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The microservice container you want to edit. You can pass either the ID or UrlRef.
     * - ``-vm, --version-mask INTEGER "*.*.*"``
       - Removes all versions with that major, minor, or patch. Use a * to indicate all. For example, ``--version-mask "9.*.*"`` will delete all versions with a major value of 9. "--version-mask *.*.*" will delete all versions.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the microservice you want to remove. For example, ``--version "9.9.9"``.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table`` 
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
       Container: 999
       Version: 9.9.9
 
 Response:
 
 .. code-block:: bash
 
     id  Current State Version # Created At
     999 running       9.9.9     02/22/19 19:57:16

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The microservice container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the microservice you want to start. For example, ``--version "9.9.9"``.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table`` 
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
       Container: 999
       Version: 9.9.9
 
 Response:
 
 .. code-block:: bash
 
     id  Current State Version # Created At
     999 stopped       9.9.9     02/22/19 19:57:16

 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The microservice container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the microservice you want to stop. For example, ``--version "9.9.9"``.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table`` 
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
      Container: 999
      Version: 9.9.9

 Response:
 
 .. code-block:: bash
 
     id  versionNumber label createdAt
     999 9.9.9         dev   02/22/19 19:57:16
     
.. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The microservice container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the microservice you want to update. For example, ``--version "9.9.9"``.
     * - ``-l, --label "[prod|dev|old]"``
       - The new status of the version. It can be ready-for-production, in-development, or deprecated respectively.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table`` 
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
     
 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--filter "JSON VALUE=SPECIFIC VALUE"``
       - Returns results that match the filter criteria. For example: ``--filter "instanceType=studio"``. Additional filter options are available in the :ref:`Ls Filters` section.
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
     
 .. list-table:: Options 
     :widths: 10 20

     * - ``--env "STRING"``
       - The name of the environment whose organizations you want listed.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {isTest}"``. 
     * - ``--filter "JSON VALUE=SPECIFIC VALUE"``
       - Returns results that match the filter criteria. For example: ``--filter "isTest=None"``. Additional filter options are available in the :ref:`Ls Filters` section.
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
     
 .. list-table:: Options 
     :widths: 10 20

     * - ``--profile-name "STRING"``
       - What you want to call the profile in the CLI. The profile will be associated with a studio or command center of your choosing, so keep that in mind when naming the profile.  
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. The only options are ``--format "{env} {orgName} {orgId}"``. 
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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

 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{env} {orgName}"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

.. _Profile Refresh-Token:

Refresh-token 
+++++++++++++

 Refreshes the profiles cached token used by the Visual Studio Code Luma extension. 
 
 Example:

 .. code-block:: bash
   
     $ luma profile refresh-token
       Profile: dragon

 Response:
 
 .. code-block:: bash
 
     Refreshed 'dragon' access token.

 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The name of the profile whose token is to be refreshed.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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

 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The name of the profile you want to remove.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

_______________________________________________________________________________________________________________________________________

.. _Widget:

Widget
^^^^^^

Commands that add, modify, share, and delete widget containers.

.. _Widget Access:

Access
++++++

 Shares or unshares a widget container with child organizations.

 Example:

 .. code-block:: bash
   
     $ luma widget access --add 99
       Profile: dragon
       Container: 999
 
 Response:
 
 .. code-block:: bash
 
     failed sharedWith          unsharedFrom resultingGrantees
     []     [{'granteeId': 99}] []           ['Dragon Command Center']
     
 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The widget container you want to edit. You can pass either the ID or UrlRef.
     * - ``--add ID``
       - The studio or command center whom with you want to **share**. You can pass either the ID or Name.
     * - ``--rm ID``
       - The studio or command center whom with you want to **unshare**. You can pass either the ID or Name.
     * - ``--absolute ID``
       - Unshares the tool with all organizations and then shares the tool with the specified organizations. *Ignores* ``--add`` *and* ``--rm`` *commands*. You can pass either the ID or Name.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{failed} {resultingGrantees}"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--current``
       - Lists the organizations the specified tool is shared with.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
     
 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``--name "STRING"``
       - What you want to call the widget container. The name will appear in the command center and studio. 
     * - ``--url-ref "STRING"``
       - url-ref: What the widget will be referenced by in URLs. For example: https://urlToExperience.com/url-ref or ic/url-ref. It can contain only lowercase letters, numbers, or dashes. 
     * - ``-path, --icon-file "FILE PATH"``
       - The absolute path where the icon SVG file is located. For example: ``-path "C:/Users/User/Desktop/Folder/icon.SVG"``. 
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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

 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--filter "JSON VALUE=SPECIFIC VALUE"`` 
       - Returns results that match the filter criteria. For example: ``--filter "name=Hydra"``. Additional filter options are available in the :ref:`Ls Filters` section.
     * - ``--page INTEGER``
       - The results page you want to view.
     * - ``--pagesize INTEGER``
       - The number of results you want to show per page.
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
       Container: 999
 
 Response:
 
 .. code-block:: bash
 
     id  name  urlRef createdAt
     999 Hydra hydra  02/22/19 20:38:07

 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The widget container you want to edit. You can pass either the ID or UrlRef.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
       Container: 999
 
 Response:
 
 .. code-block:: bash
 
     id  name            urlRef createdAt
     999 European Dragon hydra  02/22/19 20:38:07

 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The widget container you want to edit. You can pass either the ID or UrlRef.
     * - ``--name "STRING"``
       - The new name for the widget container. The name will appear in the command center and studio. 
     * - ``-path, --icon-file "FILE PATH"``
       - The absolute path where the new icon SVG file is located. For example: ``-path "C:/Users/User/Desktop/Folder/icon.SVG"``. 
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
       Container: 999
       Label: prod 
       Version Number: 9.9.9
       Container File Path: C:\fantasy\creatures\dragons\hydra.gz
       Port: 8080 
 
 Response:
 
 .. code-block:: bash
 
     Uploading image to Lumavate
     Image Size: 179.87 MB
     id  actualState versionNumber label createdAt
     999 created     9.9.9         prod  02/22/19 20:46:08
     
 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``--port INTEGER``
       - The port that the version will run on. This will either be set in your code or be your programming language’s default port.
     * - ``--editor-port INTEGER``
       - The editor port checked by the Visual Studio Code Luma extension. 
     * - ``--is-editable``
       - Marks the widget version as editable. Editable versions can be edited through the Visual Studio Code Luma extension.
     * - ``-c, --container ID``
       - The widget container you want to edit. You can pass either the ID or UrlRef.
     * - ``-path, --container-file-path "FILE PATH"``
       - The absolute path where the widget tar file is located. For example: ``-path "C:/Users/User/Desktop/Folder/widget.tar"``. 
     * - ``-image, --docker-image "STRING"``
       - The name and tag of a microservice Docker container from the Docker daemon. Docker must be installed locally to use this option. For more information about installing Docker, please see :ref:`Docker set-up<Installing Locally>`. 
     * - ``-fv, --from-version INTEGER "*.*.*"``
       - The version you want to use as a base for the current version. This will use the specified version’s port, label, variables, and image unless otherwise specified. Use a * to indicate the most recent version. For example, ``--from-version "9.9.*"`` will take the most recent version that has a major and minor value of 9. ``--version-mask "*.*.*"`` will take the most recent version. 
     * - ``-v, --version INTEGER "*.*.*"``
       - What you want the widget’s version number to be. For example, ``--version "9.9.9"``.
     * - ``--patch``
       - Sets the version number by increasing the from-version’s number patch value by one. For example, ``--from-version "1.1.1" --patch`` sets the version number to 1.1.2.
     * - ``--minor``
       - Sets the version number by increasing the from-version’s number minor value by one. For example, ``--from-version "1.1.1" --minor`` sets the version number to 1.2.0.
     * - ``--major``
       - Sets the version number by increasing the from-version number’s major value by one. For example, ``--from-version "1.1.1" --major`` sets the version number to 2.0.0.
     * - ``--env-var "{"STRING":"KEY"}"``
       - The name of the environmental variable followed by the key value. For more information, see the :ref:`environmental variables definition<Enviroment Variables>`.
     * - ``-l, --label "[prod|dev|old]"``
       - The status of the version as ready-for-production, in-development, or deprecated respectively.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Widget-version Download:

Download
++++++++

 Downloads a zip file of an editable widget version's Image.
 
 Example:
 
 .. code-block:: bash
 
     $ luma widget-version download
       Profile: dragon
       Container: 999
       Version: 9.9.9
       
 Response:
 
 .. code-block:: bash
 
      % Total    % Received % Xferd  Average Speed    Time     Time      Time  Current
                                      Dload  Upload   Total    Spent     Left  Speed
    100 42275  100    42275 0     0    42275     0  0:00:01  0:00:01 --:--:--    42275
    
    File Location: C:\Users\User\Desktop\application.999999.zip    
       
 .. list-table:: Options
     :widths: 10 20
     
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The widget container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the widget you want to edit. For example, ``--version "9.9.9"``.
     * - ``--path "FILE PATH"``
       - The absolute path where the widget zip file will be saved. For example: ``--path "C:/Users/User/Desktop/Folder/widget.zip"``. Defaults to the desktop if no path is specified.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

.. _Widget-version Exec:

Exec
++++

 Sends commands directly to Docker. For more information about Docker commands, consult the `Docker documentation <https://docs.docker.com/engine/reference/commandline/docker/>`_.

 Example:

 .. code-block:: bash
   
     $ luma widget-version exec '<<Docker Command>>'
       Profile: dragon
       Container: 999
       Version Number: 9.9.9

 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The widget container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the widget you want to edit. For example, ``--version "9.9.9"``.
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.
       
 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Widget-version Logs:

Logs
++++

 Returns the logs for a widget version. If the widget version is editable, the editor logs will be followed. If the widget version is read-only or is not editable, the production logs will be tailed. 

 Example:

 .. code-block:: bash
   
     $ luma widget-version logs
       Profile: dragon
       Container: 999
       Version Number: 9.9.9
 
 Response:
 
 .. code-block:: bash
 
     | ___ \
     | |_/ / ___ ___
     | ___ \ / _ \ / _ \
     | |_/ /| __/| __/
     \____/ \___| \___| v1.10.0
      [21m [0m2019/02/22 20:48:24  [34m [1mINFO  [21m [0m ▶ 0001 Using 'widget' as 'appname'
     2019/02/22 20:48:24  [34m [1mINFO  [21m [0m ▶ 0002 Initializing watcher...
     github.com/Place/Repository/File
     widget/models
     widget/controllers
     widget/routers
     widget
     2019/02/22 20:48:26  [32m [1mSUCCESS  [21m [0m ▶ 0003 Built Successfully!
     2019/02/22 20:48:26  [34m [1mINFO  [21m [0m ▶ 0004 Restarting 'widget'...
     2019/02/22 20:48:26  [32m [1mSUCCESS  [21m [0m ▶ 0005 './widget' is running...
     2019/02/22 20:48:26.774  [1;34m[I] [asm_amd64.s:2197] http server Running on http://:8080 [0m
     2019/02/22 20:48:30.578  [1;44m[D] [server.go:2568] | 54.164.117.6| [42m 200  [0m| 127.084µs| match| [44m GET  [0m /ic/hydra/discover/health r:/:ic/:url_ref/discover/health [0m
     
 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The widget container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the widget whose logs you want to see. For example, ``--version "9.9.9"``.
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

.. _Widget-version Ls:

Ls
++

 Lists all the versions for a widget container.

 Example:

 .. code-block:: bash
   
     $ luma widget-version ls
       Profile: dragon
       Container: 999

 Response:
 
 .. code-block:: bash
 
     id  actualState versionNumber label createdAt
     999 running     9.9.9         prod  02/22/19 20:46:08
     99  running     9.9.99        old   02/22/19 20:46:08
     
 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The widget container whose version you want to see. You can pass either the ID or UrlRef.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--filter "JSON VALUE=SPECIFIC VALUE"``
       - Returns results that match the filter criteria. For example: ``--filter "actualState=running"``. Additional filter options are available in the :ref:`Ls Filters` section.
     * - ``--page INTEGER``
       - The results page you want to view.
     * - ``--pagesize INTEGER``
       - The number of results you want to show per page.
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

 .. warning:: 
    ``--table`` is deprecated.
    Use ``--format`` to see JSON values organized in table format.

 .. note::
    Version number is filtered as ``"major=*&minor=*&patch=*"``.

.. _Microservice-version Restart:

Restart
+++++++

 Restarts the widget version's editor application without discarding code changes.
 
 Example:

 .. code-block:: bash
   
     $ luma widget-version restart 
       Profile: dragon 
       Container: 999
       Version Number: 9.9.9

 Response:
 
 .. code-block:: bash
 
      {'payload': {'data': {'actualState': 'running', 'actualStateChangedAt': '2019-06-18T19:06:37.832178+00:00', 'containerId': 9999, 'createdAt': '2019-06-18T14:55:30.243397+00:00', 'createdBy': 99, 'desiredState': 'running', 'desiredStateChangedAt': '2019-06-18T16:24:06.846847+00:00', 'editorPort': None, 'enforceRoutes': True, 'env': {}, 'expand': {}, 'id': 9999, 'instanceCount': 1, 'isEditable': False, 'label': 'prod', 'lastActualStatePayload': {'childHasError': False, 'children': [{'childHasError': False, 'children': [], 'errorMessage': None, 'id': '9d999999', 'overallPercent': 100.0, 'percent': 100, 'summary': {'beginState': 'running', 'eventName': 'do_validate', 'message': 'Container Version 9.9.9 (ID:9999) started successfully'}}, {'childHasError': False, 'children': [], 'errorMessage': None, 'id': '9d99r99a', 'overallPercent': 100.0, 'percent': 100, 'summary': {'beginState': 'validating', 'eventName': 'validated'}}], 'errorMessage': None, 'id': '9d9rag9o', 'overallPercent': 100.0, 'percent': 100, 'summary': {'stateLog': ['running', 'validating', 'running']}}, 'lastModifiedAt': '2019-06-18T19:11:10.410143', 'lastModifiedBy': 99, 'major': 9, 'minor': 0, 'notes': None, 'patch': 9, 'platformVersion': 'v2', 'port': 9999, 'repositoryName': 'registry.realm.lumavate-type.com/hydra', 'rewriteUrl': False, 'stateChangedAt': '2019-06-18T14:55:30.235871+00:00', 'tag': 'd9r9', 'versionNumber': '9.9.9'}}}
    
 .. list-table:: Options 
     :widths: 10 20

     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The widget container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the microservice you want to restart. For example, ``--version "9.9.9"``.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

.. _Widget-version Rm:

Rm
++

 Deletes a widget version. This cannot be done if a widget version is being used in an experience.

 Example:

 .. code-block:: bash
   
     $ luma widget-version rm
       Profile: dragon
       Container: 999
       Version Number: 9.9.9

 Response:
 
 .. code-block:: bash
 
     id  versionNumber label createdAt
     999 9.9.9         prod  02/22/19 20:46:08
     
 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The widget container you want to edit. You can pass either the ID or UrlRef.
     * - ``-vm, --version-mask INTEGER "*.*.*"``
       - Removes all version with that major, minor, or path. Use a * to indicate all. For example, ``--version-mask "9.*.*"`` will delete all versions with a major value of 9. ``--version-mask "*.*.*"`` will delete all versions.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the widget you want to remove. For example: ``--version "9.9.9"``.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
       Container: 999
       Version Number: 9.9.9

 Response:
 
 .. code-block:: bash
 
     id  Current State Version # Created At
     999 running       9.9.9     02/22/19 20:46:08

 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The widget container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the widget you want to start. For example: ``--version "9.9.9"``.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
       Container: 999
       Version Number: 9.9.9

 Response:
 
 .. code-block:: bash
 
     id  Current State Version # Created At
     999 stopped       9.9.9     02/22/19 20:46:08
     
 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The widget container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the widget you want to stop. For example: ``--version "9.9.9"``.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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
       Container: 999
       Version Number: 9.9.9

 Response:
 
 .. code-block:: bash
 
     id  versionNumber label createdAt
     999 9.9.9         dev   02/22/19 20:46:08
  
 .. list-table:: Options 
     :widths: 10 20
 
     * - ``-p, --profile "STRING"``
       - The profile associated with the studio or command center you want to edit.
     * - ``-c, --container ID``
       - The widget container you want to edit. You can pass either the ID or UrlRef.
     * - ``-v, --version INTEGER "*.*.*"``
       - The version number of the widget you want to update. For example: ``--version "9.9.9"``.
     * - ``-l, --label "[prod|dev|old]"``
       - The new status of the version. It can be ready-for-production, in-development, or deprecated respectively.
     * - ``-f, --format "{JSON VALUE}"``
       - Returns a table with the requested JSON values. For example: ``--format "{id} {createdBy}"``. 
     * - ``--json``
       - Returns the raw JSON payload. 
     * - ``--table``
       - Returns a table with several basic JSON values.
     * - ``--help``
       - A list of available sub-commands and options. Several commands and options have a description explaining what they do.

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

 Example:

 .. code-block:: bash
   
    $ luma profile ls --filter "name=gt:dragon"
    
 Response:
 
 .. code-block:: bash
 
    profileName env     orgName       orgId
    dragon-two  Fantasy Dragon Studio 9

.. _Ls Commands lt:

Less Than (lt)
++++++++++++++

 Looks for anything that contains less than the specified value.

 Example:

 .. code-block:: bash
   
    $ luma profile ls --filter "name=lt:dragon"
    
 Response:
 
 .. code-block:: bash
 
    profileName env     orgName       orgId
    drag        prod    Other Studio  3

.. _Ls Commands gte:

Greater Than Or Equal To (gte)
++++++++++++++++++++++++++++++

 Looks for anything that contains either the specified value or more than the specified value.

 Example:

 .. code-block:: bash
   
    $ luma profile ls --filter "name=gte:dragon"
    
 Response:
 
 .. code-block:: bash
 
    profileName env     orgName                orgId
    dragon      Fantasy Dragon Command Center  99
    dragon-two  Fantasy Dragon Studio          9

.. _Ls Commands lte:

Less Than Or Equal To (lte)
+++++++++++++++++++++++++++

 Looks for anything that contains either the specified value or less than the specified value.

 Example:

 .. code-block:: bash
   
    $ luma profile ls --filter "name=lte:dragon"

 Response:
 
 .. code-block:: bash
 
    profileName env     orgName                orgId
    dragon      Fantasy Dragon Command Center  99
    drag        prod    Other Studio           3
    
.. _Ls Commands ct:

Containing (ct)
+++++++++++++++

 Looks for anything that contains the specified value.

 Example:

 .. code-block:: bash
   
    $ luma profile ls --filter "name=ct:dragon"
    
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

.. _Version:

Version
+++++++

Lists the luma version that the current machine is on.

Example:

.. code-block:: bash
   
   $ luma --version

Response:

.. code-block:: bash

   Lumavate CLI Version: 0.11.0
       
.. _Version Commands Install:

Install
+++++++

 Installs luma.

 Example: 

 .. code-block:: bash
   
    $ pip3 install luma

.. _Version Commands Upgrade:

Upgrade
+++++++

 Updates the version of luma on the current machine. 

 Example:

 .. code-block:: bash
   
    $ pip3 install luma --upgrade

.. _Version Commands Help:

Help
++++

 Describes and lists the possible subcommands for any command. This can be done by running any command without passing in any options or by passing in the ``--help`` flag.

 Example:

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
