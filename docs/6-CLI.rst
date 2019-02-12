
.. _CLI:

============
CLI
============

The Lumavate Commandline Line Interface (CLI) can be used to streamline many administrative tasks, such as adding and updating widgets, microservices, and/or component sets.

.. The CLI uses the native REST APIs available via the Platform. To learn more about Lumavate's REST APIs, please go here: <link to come>.

.. If you would like to know more about the CLI, it is available via open-source here: <link to come>.

The following documentation will explain:

* :ref:`Requirements`
* :ref:`Installation`
* :ref:`Provisioning Credentials`
* :ref:`CLI Syntax`

.. _Requirements:

Requirements
-------------
You will need to install `Python 3.1.1 <https://www.python.org/downloads/>`_ or higher in order to use the CLI. 

It is recommended that you install `Gitbash <https://git-scm.com/downloads>`_ as the CLI is written for and tested in a BASH shell. 

.. tip::
   Use `ZSH <https://sourceforge.net/projects/zsh/files/>`_ to get the most out of the CLI. This enables extra features such as showing help text during autocompletion. 

.. _Installation:

Installation
------------
The CLI can be installed two different ways:

 #. Through Pip
 #. From the source.

.. _Installation Pip:

From Pip
^^^^^^^^

 As a Non-admin run:
  
   .. code-block:: bash
     
      $ sudo pip3 install luma

 As an Admin run:
  
   .. code-block:: bash
     
      $ pip3 install luma

.. _Installation Source:

From Source
^^^^^^^^^^^

 Installing the CLI as a Non-admin:

  #. Clone this repo.
  #. CD into the CLI dir
  #. Run:
  
     .. code-block:: bash
      
        $ pip3 install luma --user
 
  #. Add the returned path URL to the path 
   
     Example Response: 
   
     .. code-block:: bash
       
        The script luma.exe is installed in 'C:\ComputerName\UserName\AppData\Roaming\Python\Python37\Scripts' which is not on PATH. 
        Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
  
 Installing the CLI as an Admin:

  #. Clone this repo.
  #. CD into the CLI dir
  #. Run:
   
     .. code-block:: bash
       
        $ sudo pip3 install luma

 .. note::
    To activate autocompletion after install, restart your terminal or source your shell configuration (either .zshrc or .bash_profile).  

_______________________________________________________________________________________________________________________________________

.. _Provisioning Credentials:

Provisioning Credentials
-------------------------

There are two types of configuration in the CLI: configuring environments and configuring profiles.
    
    * **Environments** know how to get and refresh tokens so the user stays authorized with the platform. They also set what command centers or studios you have access to.
    * **Profiles** give the user a company context in a specific environment which is required by most of the platform API. They set what studio or command center the user is modifying.  

.. _Provisioning Environments:

Setting-Up Environments:
^^^^^^^^^^^^^^^^^^^^^^^

 You can use either the Lumavate pre-configured environment or you can setup your own environment configuration.

 Using the preset configuration:

  #. Log into the command center you want to modify with the CLI
  #. Go to the CLI tab located in the side menu bar
  #. Copy the information from the Configure An Environment field. It should look like this:
   
     .. code-block:: bash
       
        $ luma env config --env-name prod --app https://not-a-real-realm.dragonfly.lumavate-type.com --audience https://dragonfly.lumavate-type.com/notarealapp --token dragonfly-lumavate-type.notarealtoken.com --client-id NotARealId1234j2eIxKILomCdA --client-secret NotARealClientSecretEqeKWD5JgUtzsRkhNNXMPQM6auPhTTjVK
      
  #. Past the command into your Bash window 

 Using your own configuration:

  #. Log into the command center you want to modify with the CLI
  #. Go to the CLI tab located in the side menu bar
  #. Take note of the app, audience, token, client-id, and client-secret information from the Configure An Environment field
  #. In your Bash window, run:
   
     .. code-block:: bash
       
        $ luma env config

  #. Fill out the prompts as they appear on the screen with the appropriate information. It should look like this when you are done:
   
     .. code-block:: bash
       
        $ Env Name: <<name of environment in CLI>>
          App: <<enviroment Url>>
          Token: <<enviroment token>>
          Audience: <<envitoment audience>>
          Client id: <<user clientId>>
          Client secret: <<user clientSecret>>

 .. note:: 
    The CLI uses Client Id and Client Secret to associate a user’s context to a machine. From this point forward, user will refer to the client id and client secret information used to setup the environment in the CLI. 

.. _Provisioning Profiles:
  
Setting up Profiles:
^^^^^^^^^^^^^^^^^^^

 Profiles can be setup using the Lumavate pre-set command or using your own configuration. 

 You will need to have configured an environment on your machine through the CLI to configure a profile.  

 Using a preset configuration:

  #. Log into a Lumavate command center
  #. Navigate to the CLI tab located in the side menu bar
  #. Copy the information from the Add A Profile field. It should look like this:
   
     .. code-block:: bash
       
        $ luma profile add --env prod

  #. Past the command into your Bash window
  #. You will be prompted to name your profile. It should look like this:
   
     .. code-block:: bash
       
         Profile Name: <<name of profile in CLI>>

  #. You will then be presented with a list of organizations. Pick the one you want to edit with this profile. It should look like this:
   
     .. code-block:: bash
       
          id Org Name                  Org Type Test Org
          35 Sample Command Center     dev      None
          49 Sample Studio             studio   False

          Org ID you want to associate with this profile: <<org id>>

     
 Using your own configuration:

  #. In your Bash window, run:
   
     .. code-block:: bash
       
        $ luma profile add

  #. You will be prompted to name your profile. It should look like this:
   
     .. code-block:: bash
       
         Profile Name: <<name of profile in CLI>>

  #. A list of environments will appear. Select which environment you wish to associate with the profile:
   
     .. code-block:: bash
       
        Env Name                                    App                                                  Audience                                  Token                                     Name
       https://not-a-realm.place.lumavate-type.com https://not-a-real-realm.dragonfly.lumavate-type.com https://place.lumavate-type.com/notanapp dragonfly-lumavate-type.notarealtoken.com prod
     
         Env: <<name of environment you want the profile associated with>>

  #. A list of organizations will appear. Pick the one you want to edit with this profile. It should look like this:
   
     .. code-block:: bash
       
         id Org Name                  Org Type Test Org
         35 Sample Command Center     dev      None
         49 Sample Studio             studio   False

         Org ID you want to associate with this profile: <<org id>>

 .. warning::
    If there are two profiles or environments with the same name, the newer version will overwrite the older version. Profiles in different environments can have the same name without overwriting each other.  

 .. note::
    While running the profile command, you will have the option to associate the new profile to any organization the user has access to regardless of the command center you are currently in.

_______________________________________________________________________________________________________________________________________

.. _CLI Syntax:

CLI Syntax
----------

The CLI will allow users to interact with the Lumavate platform from a terminal. For setup instructions, look at the `Github readme <https://github.com/Lumavate-Team/documentation/blob/master/CLI.rst>`_ or the :ref:`CLI setup documentation <CLI>`. All the main commands are listed in the Command Index below. Each of the main commands has their subcommands listed in their section. 

In Bash, pass the ``--help`` flag with the command for more information on how to use them and how to use their subcommands.

All commands sent to Bash will start with ``luma``.

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
 #. :ref:`Ls Commands`
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
   
    $ luma api post /iot/v1/containers?expand=all -d ‘{“id:9, ”type”:”widget”, ”name”:”Fire Breathing”, ”urlRef”:”fireball”, ”ephemeralKey”: "99/temp/c287aaecab1840bc8bd6e52132409c30__adobe.svg”}’
      Profile: dragon

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
   
    $ luma api post /iot/v1/containers?expand=all -d ‘{“id:9, ”type”:”widget”, ”name”:”Fire Breathing”, ”urlRef”:"fireball", "ephemeralKey”: "99/temp/c287aaecab1840bc8bd6e52132409c30__adobe.svg”}’
      Profile: dragon

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

 Shares and Unshares component-set containers with child organizations.

 Example:

 .. code-block:: bash
   
    $ luma component-set access --add 99
      Profile: dragon
      Component set: 999

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
      Name: Fire Breathing
      Url Ref: fireball

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
   
    $ luma component-set update --name “Frosty Breath”
      Profile: dragon
      Component set: 999

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
     Label: prod
     Version: 9.9.99
     Component set file: “C:\fantasy\creatures\dragons\firebreather.zip”

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
     Version number: 9.9.99 

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

Options: 

 * ``-p, --profile “STRING”``
 * ``-cs, --component-set ID``
 * ``-v, --version INTAGER (*.*.*)``
 * ``-l, --label “[prod, dev, old]”``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
 * ``--json``
 * ``--table``
 * ``--help``

.. warning:: 
   ``--table`` is deprecated.
   Use ``--format`` to see JSON values organized in table format.

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

Options: 

 * ``--env-name “STRING”``
 * ``--app “LINK”``
 * ``--token “LINK”``
 * ``--audience “LINK”``
 * ``--client-id ID``
 * ``--client-secret SECRET``
 * ``--json``
 * ``--help``

.. _Env Ls:

Ls
++

Lists all the environments the user has access to.

Example:

.. code-block:: bash
   
   $ luma env ls

Options: 

 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
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

Options: 

 * ``--env-name “STRING”``
 * ``--help``

.. _Experience:

Experience
^^^^^^^^^^

Commands that move and list experiences.

.. _Experience Export:

Export
++++++

Exports an experience as a JSON file form a studio.

Example:

.. code-block:: bash
   
   $ luma experience export
     Profile: dragon
     Export file: “C:\fantasy\creatures\dragons\firebreather.json”
     Label: Fire Breather

Options:

 * ``-p, --profile "STRING"``
 * ``-l, --label "STRING"``
 * ``-n, --name "STRING"``
 * ``-path, --export-file "FILE PATH"``
 * ``--json``
 * ``--help``

.. _Experience Import:

Import
++++++

Imports an experience JSON file to a studio.

Example:

.. code-block:: bash
   
   $ luma experience import
     Profile: dragon
     Label: Fire Breather
     Activation code: fireball
     Import file: “C:\fantasy\creatures\dragons\firebreather.json”
     Collection Name: Dragons

Options:

 * ``-p, --profile "STRING"``
 * ``-l, --label "STRING"``
 * ``-d, --description "STRING"``
 * ``-ci, --collection-id ID``
 * ``-cn, --collection-name "STRING"``
 * ``-ac, --activation-code "STRING"``
 * ``-t, --template``
 * ``-ru, --redirect-url "URL"``
 * ``-path, --import-file "FILE PATH"``
 * ``--json``
 * ``--help``

.. _Experience Ls:

Ls
++

Lists all the experiences in the studio associated with the specified profile.

Example:

.. code-block:: bash
   
   $ luma experience ls
      Profile: dragon

Options:

 * ``-p, --profile "STRING"``
 * ``-f, --format "{JSON VALUE}, {JSON VALUE}"``
 * ``--filter "{JSON VALUE=SPECIFIC VALUE}"``
 * ``--page INTEGER``
 * ``--pagesize INTEGER``
 * ``--json``
 * ``--help``

.. _Experience-collection:

Experience-collection
^^^^^^^^^^^^^^^^^^^^^

List experience collections in the studio associated with the specified profile.

Example:

.. code-block:: bash

   $ luma experience-collection ls
     Profile: dragon

Options:
 
 * ``--help``

.. _Microservice:

Microservice
^^^^^^^^^^^^

Commands that create, modify, share, and delete microservice containers.

.. _Microservice Access:

Access
++++++

Shares and/or unshares a microservice container with child organizations. 

Example:

.. code-block:: bash
   
   $ luma microservice access --add 99
     Profile: dragon
     Microservice: 999

Options: 

 * ``-p, --profile “STRING”``
 * ``-ms, --microservice ID``
 * ``--add ID``
 * ``--rm ID``
 * ``--absolute ID``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
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
     Name: Fire Breather
     Url Ref: fireball

Options: 

 * ``-p, --profile “STRING”``
 * ``--name “STRING”``
 * ``--url-ref “STRING”``
 * ``-path, --icon-file “FILE PATH”``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
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

.. _Microservice Rm:

Rm
++

Removes a microservice container. 

Example:

.. code-block:: bash
   
   $ luma microservice rm 
     Profile: dragon 
     Microservice: 999

Options: 

 * ``-p, --profile “STRING”``
 * ``-ms, --microservice ID``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
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
   
   $ luma microservice update --name “Frosty Breath”  
     Profile: dragon 
     Microservice: 999 

Options: 

 * ``-p, --profile “STRING”``
 * ``-ms, --microservice ID``
 * ``--name “STRING”``
 * ``-path, --icon-file “FILE PATH”``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
 * ``--json``
 * ``--table``
 * ``--help``

.. warning:: 
   ``--table`` is deprecated.
   Use ``--format`` to see JSON values organized in table format.

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
     Microservice-file-path: “C:\fantasy\creatures\dragons\firebreather.tar.gz”

Options: 

 * ``-p, --profile “STRING”``
 * ``-ms, --microservice ID``
 * ``--port INTAGER``
 * ``-image, --docker-image “FILE PATH”``
 * ``-path, --microservice-file-path “FILE PATH”``
 * ``-fv, --from-version INTAGER (*.*.*)``
 * ``-v, --version INTAGER (*.*.*)``
 * ``--patch INTAGER``
 * ``--minor INTAGER``
 * ``--major INTAGER``
 * ``--env-var "{“STRING”:”KEY”}"``
 * ``-l, --label "[dev, old, prod]"``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
 * ``--json``
 * ``--table``
 * ``--help``

.. warning:: 
   ``--table`` is deprecated. 
   Use ``--format`` to see JSON values organized in table format.

.. _Microservice-version Exec:

Exec
++++

Sends commands directly to Docker. For more information, consult the `Docker documentation <https://docs.docker.com/engine/reference/commandline/docker/>`_.

Example:

.. code-block:: bash
   
   $ luma microservice-version exec “Docker command” 
     Profile: dragon 
     Mirocservice: 999 
     Version Number: 9.9.9

Options: 

 * ``-p, --profile “STRING”``
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

Options: 

 * ``-p, --profile “STRING”``
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

Options: 

 * ``-p, --profile “STRING”``
 * ``-ms, --microservice ID``
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

Options: 

 * ``-p, --profile “STRING”``
 * ``-ms, --microservice ID``
 * ``-vm, --version-mask INTAGER (*.*.*)``
 * ``-v, --version INTAGER (*.*.*)``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
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

Options: 

 * ``-p, --profile “STRING”``
 * ``-ms, --microservice ID``
 * ``-v, --version INTAGER (*.*.*)``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
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

Options: 

 * ``-p, --profile “STRING”``
 * ``-ms, -- microservice ID``
 * ``-v, --version INTAGER (*.*.*)``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
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

Options: 

 * ``-p, --profile “STRING”``
 * ``-ms, -- microservice ID``
 * ``-v, --version INTAGER (*.*.*)``
 * ``-l, --label “[dev, old, prod]”``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
 * ``--json``
 * ``--table``
 * ``--help``

.. warning:: 
   ``--table`` is deprecated.
   Use ``--format`` to see JSON values organized in table format.

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

Options: 

 * ``-p, --profile “STRING”``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
 * ``--filter “{JSON VALUE=SPECIFIC VALUE}”``
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

Options: 

 * ``--env “STRING”``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
 * ``--filter “{JSON VALUE=SPECIFIC VALUE}”``
 * ``--json``
 * ``--help``

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
     <<lists of envs user has access to>>
     Name of Env you want to use with this profile: Fantasy
     <<lists of orgs in the selected env>>
     Org ID you want to associate with this profile: 99

Options: 

 * ``--profile-name “STRING”``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
 * ``--help``

.. _Profile Ls:

Ls
++

Lists all profiles associated with the client id and secrete.

Example:

.. code-block:: bash
   
   $ luma profile ls

Options: 

 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
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

Options: 

 * ``-p, --profile “STRING”``
 * ``--help``

.. _Version:

Version
^^^^^^^

Lists the luma version that the current machine is on.

Example:

.. code-block:: bash
   
   $ luma version

Options: 

 * ``--help``

.. _Widget:

Widget
^^^^^^

Commands that add, modify, share, and delete widget containers.

.. _Widget Access:

Access
++++++

Shares and/or Unshares a widget container with child organizations.

Example:

.. code-block:: bash
   
   $ luma widget access --add 99
     Profile: dragon
     Widget: 999

Options: 

 * ``-p, --profile “STRING”``
 * ``-w, --widget ID``
 * ``--add ID``
 * ``--rm ID``
 * ``--absolute ID``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
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
     Name: Fire Breathing
     Url Ref: fireball

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

.. _Widget Ls:

Ls
++

Lists all the widget containers in an organization associated with the specified profile. 

Example:

.. code-block:: bash
   
   $ luma widget ls
     Profile: dragon

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

.. _Widget Rm:

Rm
++

Removes a widget container.

Example:

.. code-block:: bash
   
   $ luma widget rm
     Profile: dragon
     Widget: 999

Options: 

 * ``-p, --profile “STRING”``
 * ``-w, --widget ID``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
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
   
   $ luma widget update --name “Frosty Breath”
     Profile: dragon
     Widget: 999

Options: 

 * ``-p, --profile “STRING”``
 * ``-w, --widget ID``
 * ``--name “STRING”``
 * ``-path, --icon-file “FILE PATH”``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``  
 * ``--json``
 * ``--table``
 * ``--help``

.. warning:: 
   ``--table`` is deprecated.
   Use ``--format`` to see JSON values organized in table format.

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
     Widget File Path: “C:\fantasy\creatures\dragons\firebreather.tar.gz”
     Port: 8080 

Options: 

 * ``-p, --profile “STRING”``
 * ``--port INTAGER``
 * ``-w, --widget ID``
 * ``-path, --widget-file-path “FILE PATH”``
 * ``-image, --docker-image “FILE PATH”``
 * ``-fv, --from-version INTAGER (*.*.*)``
 * ``-v, --version INTAGER (*.*.*)``
 * ``--patch INTAGER``
 * ``--minor INTAGER``
 * ``--major INTAGER``
 * ``--env-var "{“STRING”:”KEY”}"``
 * ``-l, --label “[dev, old, prod]”``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
 * ``--json``
 * ``--table``
 * ``--help``

.. warning:: 
   ``--table`` is deprecated.
   Use ``--format`` to see JSON values organized in table format.

.. _Widget-version Exec:

Exec
++++

Sends commands directly to Docker. For more information, consult the `Docker documentation <https://docs.docker.com/engine/reference/commandline/docker/>`_.

Example:

.. code-block:: bash
   
   $ luma widget-version exec “Docker command”
     Profile: dragon
     Widget: 999
     Version Number: 9.9.9

Options: 

 *	-p, --profile “STRING”
 *	-w, --widget ID
 *	-v, --version INTAGER (*.*.*)
 *	--target [one, all]
 *	--json 
 *	--table
 *	--help

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

Options: 

 * ``-p, --profile “STRING”``
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

Options: 

 * ``-p, --profile “STRING”``
 * ``-w, --widget ID``
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

.. _Widget-version Rm:

Rm
++

Deletes a widget version. This cannot be done if a widget version is being used in an experience.

Example:

.. code-block:: bash
   
   $ luma widget version rm
     Profile: dragon
     Widget: 999
     Version Number: 9.9.9

Options: 

 * ``-p, --profile “STRING”``
 * ``-w, --widget ID``
 * ``-vm, --version-mask INTAGER (*.*.*)``
 * ``-v, --version INTAGER (*.*.*)``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
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

Options: 

 * ``-p, --profile “STRING”``
 * ``-w, --widget ID``
 * ``-v, --version INTAGER (*.*.*)``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
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

Options: 

 * ``-p, --profile “STRING”``
 * ``-w, --widget ID``
 * ``-v, --version INTAGER (*.*.*)``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
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

Options: 

 * ``-p, --profile “STRING”``
 * ``-w, --widget ID``
 * ``-v, --version INTAGER (*.*.*)``
 * ``-l, --label “[dev, old, prod]”``
 * ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
 * ``--json``
 * ``--table``
 * ``–help``

.. warning:: 
   ``--table`` is deprecated.
   Use ``--format`` to see JSON values organized in table format.

.. _Ls Commands:

Ls Commands
^^^^^^^^^^^

Limits Ls search results by:

 * :ref:`Greater Than <Ls Commands gt>`
 * :ref:`Less Than <Ls Commands lt>`
 * :ref:`Greater Than or Equal To <Ls Commands gte>`
 * :ref:`Less Than or Equal To <Ls Commands lte>`
 * :ref:`Containing <Ls Commands ct>`

.. _Ls Commands gt:

gt
++

Looks for anything that contains more than the specified value. 

example:

.. code-block:: bash
   
   $ luma profile ls --filter “name=gt:dragon”

.. _Ls Commands lt:

lt
++

Looks for anything that contains less than the specified value.

example:

.. code-block:: bash
   
   $ luma profile ls --filter “name=lt:dragon”

.. _Ls Commands gte:

gte
+++

Looks for anything that contains either the specified value or more than the specified value.

example:

.. code-block:: bash
   
   $ luma profile ls --filter “name=gte:dragon”

.. _Ls Commands lte:

lte
+++

Looks for anything that contains either the specified value or less than the specified value.

example:

.. code-block:: bash
   
   $ luma profile ls --filter “name=lte:dragon”

.. _Ls Commands ct:

ct
++

Looks for anything that contains the specified value.

example:

.. code-block:: bash
   
   $ luma profile ls --filter “name=ct:dragon”

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

    $ luma --help
   
    $ luma ls --help

.. _Additional Info:

Additional Info
^^^^^^^^^^^^^^^

* Dates must be in the format: year-month-day
* Must include “” around all arguments
* Must include “&” between arguments when using multiple arguments
