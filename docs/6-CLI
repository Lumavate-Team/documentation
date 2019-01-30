============
CLI
============

The Lumavate Commandline Line Interface (CLI) can be used to streamline many administrative tasks, such as adding & updating widgets, microservices, and/or component sets.

The CLI uses the native REST APIs available via the Platform. To learn more about Lumavate's REST APIs, please go here: <link to come>.

If you would like to know more about the CLI, it is available via open-source here: <link to come>.

The following documentation will explain:

* Requirements
* Installation
* Provisioning Credentials
* Configuration

Requirements
-----------
You will need to install `Python 3.1.1 <https://www.python.org/downloads/>`_ or higher in order to use the CLI. 

It is recommended that you install `Gitbash <https://git-scm.com/downloads>`_ as the CLI is written for and tested in a BASH shell. 

.. Note:
  To get the most out of the CLI, use it with `ZSH <https://sourceforge.net/projects/zsh/files/>`_. This enables extra features such as showing help text during autocompletion. 

Installation
------------
The CLI can be installed two different ways: through Pip or from the source.

From pip
^^^^^^^^
As a Non-admin run:
  .. code-block:: python
     $ sudo pip3 install luma

As an Admin run:
  .. code-block:: python
     $ pip3 install luma

From source
^^^^^^^^^^^
Installing the CLI as a non-admin:
#. Clone this repo.
#. CD into the CLI dir
#. Run:
  .. code-block:: python
     $ pip3 install luma --user
 
#. Add the returned path URL to the path 
   An Example Response: 
   .. code-block:: python
      $ The script luma.exe is installed in 'C:\ComputerName\UserName\AppData\Roaming\Python\Python37\Scripts' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
  
As an Admin:
#. Clone this repo.
#. CD into the CLI dir
#. Run:
   .. code-block:: python
      $ sudo pip3 install luma

.. Note:
  To activate autocompletion after install, restart your terminal or source your shell config (Either .zshrc or .bash_profile).  
  
Provisioning Credentials
-------------------------
There are two types of configuration in the CLI: configuring environments and configuring profiles.
    * **Environments** know how to get and refresh tokens so you stay authorized with the platform as a user, and set what command centers or studios you have access to.
    * **Profiles** give the user a company context in a specific environment which is required by most of the platform API.

Setting-Up Environments:
^^^^^^^^^^^^^^^^^^^^^^^
You can use either the Lumavate pre-configured enviroment or you can setup your own enviorment configuration.

Using the preset configuration:
#. Log into the command center you want to modify with the CLI
#. Go to the CLI tab located in the side menue bar
#. Copy the information from the Configure an Environment field. It should look like this:
   .. code-block:: python
      $ luma env config --env-name prod --app https://not-a-real-realm.dragonfly.lumavate-type.com --audience https://dragonfly.lumavate-type.com/notarealapp --token dragonfly-lumavate-type.notarealtoken.com --client-id NotARealId1234j2eIxKILomCdA --client-secret NotARealClientSecretEqeKWD5JgUtzsRkhNNXMPQM6auPhTTjVK
      
#. Past the command into your Bash window 

Using your own configuration:
#. Log into the command center you want to modify with the CLI
#. Go to the CLI tab located in the side menue bar
#. Take note of the app, audience, token, client-id, and client-secret information from the Configure an Environment field
#. In your Bash window, run:
   .. code-block:: python
      $ luma env config

#. Fill out the prompts as they appear on the screen with the appropriate information. It should look like this when you are done:
   .. code-block:: python
      $ Env Name: <<what you want to call your envrioment>>
        App: <<enviroment Url>>
        Token: <<enviroment token>>
        Audience: <<envitoment audience>>
        Client id: <<user clientId>>
        Client secret: <<user clientSecret>>

.. Note: 
  The CLI uses Client id and Client secret to asscociate a users context to a machine. From this point forward, user will refer to the client id and client secreate information used to setup the envroment in the CLI. 
  
Setting up Profiles:
^^^^^^^^^^^^^^^^^^^
Profiles can be set-up using the Lumavate preset command or using your own configuration. You will need to have configured an envrioment on your machine through the CLI before you configure a profile.  

Using a preset configuration:
#. Log into a Lumavate command center
#. Navigate to the CLI  tab located in the side menue bar
#. Copy the information from the Add a Profile field. It should look like this:
   .. code-block:: python
      $ luma profile add --env prod

#. Past the command into your Bash window
#. You will be prompted to name your profile. It should look like this:
   .. code-block:: python
      $ Profile Name: <<what you want to call your profile>>

#. You will then be presented with a list of organizations. Pick the one you want to edit with this profile. It should look like this:
   .. code-block:: python
      $ id Org Name                 Org Type Test Org
        35 Sample command center     dev      None
        49 Sample Studio             studio   False

        Org ID you want to associate with this profile: <<org id>>

     
Using your own configuration:
#. In your Bash window, run:
   .. code-block:: python
      $ luma profile add

#. You will be prompted to name your profile. It should look like this:
   .. code-block:: python
      $ Profile Name: <<what you want to call your profile>>

#. A list of environments will appear. Select which environment you wish to associate with your profile:
    .. code-block:: python
       Env Name            App                                         Audience                               Token
     Name      https://not-a-realm.place.lumavate-type.com https://place.lumavate-type.com/notaapp place-lumavate-dev.notatokey.com
     
       Env: <<envrioment name you want your profile associated with>>

#. A list of organizations will appear. Pick the one you want to edit with this profile. It should look like this:
   .. code-block:: python
      $ id Org Name                 Org Type Test Org
        35 Sample command center     dev      None
        49 Sample Studio             studio   False

        Org ID you want to associate with this profile: <<org id>>

.. Warning:
  If there are two profiles or environments with the same name, the newer version will overwrite the older version. Profiles in different environments can have the same name without overwriting each other.  

.. Note:
  While running the profile command, you will have the option to associate the new profile to any organization your user has access to   regardless of the command center you are currently in.

.. _CLI Syntax:

CLI Syntax
==========

This CLI will allow users to interact with the Lumavate platform from a terminal. For setup instructions, look at the `Github readme <https://github.com/Lumavate-Team/documentation/blob/master/CLI.rst>`_ or the :ref:`CLI documentation <CLI>`. All the main commands can be found in the side navigation pane. Each of the main commands has their subcommands listed below them. 

Pass the ``--help`` flag with the command for more information on how to use them and how to use their subcommands.

All commands sent to bash will start with ``luma``.

Index: 
#. API
#. Component-set
#. Component-set-version
#. Env
#. Experience
#. Experience-collection
#. Microservice
#. Microservice-version
#. Org
#. Profile
#. Version
#. Widget
#. Widget-version
#. Ls Commands
#. Version Commands
#. Additional Info

.. _API:

API
---
Commands that directly query the API.

Delete
^^^^^^
Calls a delete command in order to remove something through the API. 

Example:
 .. code-block:: python
    $ luma api delete /iot/v1/containers/898?expand=all
      profile: dragon-sib

Options:
* ``-p, --profile “STRING”``
* ``--help``

.. note:
   API paths cannot include sort criteria.

.. _API Get:

Get
^^^
Calls a get command in order to return information from the API.

Example:
.. code-block:: python
   $ luma api get /iot/v1/containers?expand=all
     profile: dragon-sib

Options: 
* ``-p, --profile “STRING”``
* ``--help``

.. note:
   API paths cannot include sort criteria.

.. _API Post:

Post
^^^^
Calls a post command in order to add something through the API. 

Example:
.. code-block:: python
   $ luma api post /iot/v1/containers?expand=all -d ‘{“id:0, ”type”:”widget”, ”name”:”examplepost2”, ”urlRef”:”examplepost2”, ”ephemeralKey”: "67/temp/c287aaecab1840bc8bd6e52132409c30__adobe.svg”}’
     profile: dragon-sib

Options: 
* ``-p, --profile “STRING”``
* ``-d, --data "{JSON}, {JSON}"``
* ``--help``

.. note:
   API paths cannot include sort criteria.

.. _API Put:

Put
^^^
Calls a put command in order to change something through the API.

Example:
.. code-block:: python
   $ luma api post /iot/v1/containers?expand=all -d ‘{“id:0, ”type”:”widget”, ”name”:”examplepost2”, ”urlRef”:”exaplepost2”,                 ”ephemeralKey”: "67/temp/c287aaecab1840bc8bd6e52132409c30__adobe.svg”}’
     profile: dragon-sib

Options: 
* ``-p, --profile “STRING”``
* ``-d, --data "{JSON}, {JSON}"``
* ``--help``

.. note:
   API paths cannot include sort criteria.

.. _Component-set:

Component-set
-------------
Commands that create, modify, share, and delete component-set containers.

.. _Component-set Access:

Access
^^^^^^
Shares and Unshares component-set containers with child organizations.

Example:
.. code-block:: python
   $ luma component-set access --add 68
     profile: drag-sib
     component set: 273

Options: 
* ``-p, --profile “STRING”``
* ``-cs, --component-set ID``
* ``--add ID``
* ``--rm ID``
* ``--absolute ID``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``--help``

 .. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Component-set Add:

Add
^^^
Adds a component-set container to the command center your profile is associated with. 

Example:
.. code-block:: python
   $ luma component-set add
     Profile: drag-sib
     Name: example1
     Url Ref: example1

Options: 
* ``-p, --profile “STRING”``
* ``--name “STRING”``
* ``--url-ref “STRING”``
* ``-path, --icon-file “FILE PATH”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json`` 
* ``--table``
* ``--help``

 .. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Component-set Ls:

Ls
^^
Lists all component-set containers in the specified profile environment. 

Example:
.. code-block:: python
   $ luma component-set ls
     Profile: drag-sib

Options:
* ``-p, --profile “STRING”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”`` 
* ``--filter “{JSON VALUE=SPECIFIC VALUE}”``
* ``--page INTAGER`` 
* ``--pagesize INTAGER``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Component-set Rm:

Rm
^^
Deletes a component-set container. This can only be done after all versions in the container have been deleted.

Example:
.. code-block:: python
   $ luma component-set rm
     Profile: drag-sib
     Component set: 463

Options: 
* ``-p, --profile “STRING”``
* ``-cs, --component-set ID``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``--help`` 

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Component-set Update:

Update
^^^^^^
Updates the name or image of a component-set container. 

Example:
.. code-block:: python
   $ luma component-set update --name ExampleUpdateName1
     Profile: drag-sib
     Component set: 246

Options: 
* ``-p, --profile “STRING”``
* ``-cs, --component-set ID``
* ``--name “STRING”``
* ``-path, --icon-file “FILE PATH”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Component-set-version:

Component-set-version
---------------------
Commands that create, modify, and delete component-set versions.

.. _Component-set-version Add:

Add
^^^
Adds a version to a specified component-set container.  

Example:
.. code-block:: python
   $ luma component-set-version add 
     Profile: drag-sib
     Component set: 272
     Label: prod
     Version: 1.0.11
     Component set file: “C:\Tests\Auto\WidgetFiles\Archive.zip”

Options: 
* ``-p, --profile “STRING”``
* ``-cs, --component-set ID``
* ``-path, --component-set-file-path “FILE PATH”``
* ``-fv, --from-version ID``
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

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. Warning:
  File paths with spaces in them may need to be specified in the main command using the ``$ -path`` option as some computers do not accept these paths any other way.

.. _Component-set-version Components:

Components
^^^^^^^^^^
Returns the JSON of a component-set version. 

Example:
.. code-block:: python
   $ luma component-set-version components
     Profile: drag-sib
     Component set: 272

Options: 
* ``-p, --profile “STRING”``
* ``-cs, --component-set ID``
* ``-v, --version INTAGER (*.*.*)``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table`` and ``--json``
     The CLI will return the JSON file by default. The file cannot be organized by the CLI.

.. _Component-set-version Ls:

Ls
^^
Lists all versions in a specified component-set container.

Example:
.. code-block:: python
   $ luma component-set-version ls
     Profile: drag-sib
     Component-set: 274

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

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. note:
   Version number is filtered as “major=*&minor=*&patch=*”

.. _Component-set-version Rm:

Rm
^^
Deletes a version from a specified component-set container.

Example:
.. code-block:: python
   $ luma component-set-version rm
     Profile: drag-sib
     Component set: 272
     Version number: 1.0.11 

Options: 
* ``-p, --profile “STRING”``
* ``-cs, --component-set ID``
* ``-vm, --version-mask INTAGER (*.*.*)``
* ``-v, --version INTAGER (*.*.*)``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Component-set-version Update:

Update
^^^^^^
Updates the label of a specified component-set version.

Example:
.. code-block:: python
   $ luma component-set-version update -l dev 
     Profile: drag-sib 
     Component set: 272 
     Version number: 3.0.0

Options: 
* ``-p, --profile “STRING”``
* ``-cs, --component-set ID``
* ``-v, --version INTAGER (*.*.*)``
* ``-l, --label “[prod, dev, old]”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Env:

Env
---
Commands that create, modify, and delete environments.

.. _Env Config:

Config
^^^^^^
Creates an environment. 

Example:
.. code-block:: python
   $ luma env config
     Env name: Dragonfly
     App: https://example-realm.dragonfly.lumavate-type.com
     Token: dragonfly-lumavate-type.not-a-real-token.com
     Audience: https://dragonfly.lumavate-type.com/notarealaudience
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
^^
Lists all the environments the user has access to.

Example:
.. code-block:: python
   $ luma env ls

Options: 
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--help``

.. _Env Rm:

Rm
^^
Removes a specified environment. 

Example:
.. code-block:: python
   $ luma env rm
     Name: dragon-realm

Options: 
* ``--env-name “STRING”``
* ``--help``

.. _Microservice:

Microservice
------------
Commands that create, modify, share, and delete microservice containers.

.. _Microservice Access:

Access
^^^^^^
Shares and/or unshares a microservice container with the specified child organizations. 

Example:
.. code-block:: python
   $ luma microservice access --add 68
     Profile: drag-sib
     Microservice: 851

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

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Microservice Add:

Add
^^^
Adds a microservice container to the command center associated with the specified profile.

Example:
.. code-block:: python
   $ luma microservice add 
     Profile: drag-sib
     Name: example1
     Url Ref: example1

Options: 
* ``-p, --profile “STRING”``
* ``--name “STRING”``
* ``--url-ref “STRING”``
* ``-path, --icon-file “FILE PATH”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Microsevice Ls:

Ls
^^
Lists all microservices containers in the command center associated with the specified profile.

Example:
.. code-block:: python
   $ luma microservice ls 
     Profile: drag-sib

Options: 
* ``-p, --profile “STRING”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--filter “{JSON VALUE=SPECIFIC VALUE}”``
* ``--page INTAGER``
* ``--pagesize INTAGER``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Microservice Rm:

Rm
^^
Removes a microservice container from the command center associated with the specified profile. 

Example:
.. code-block:: python
   $ luma microservice rm 
     Profile: drag-sib 
     Microservice: 916

Options: 
* ``-p, --profile “STRING”``
* ``-ms, --microservice ID``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Microserivce Update:

Update
^^^^^^
Updates the name or image of a microservice container from the command center associated with the specified profile.

Example:
.. code-block:: python
   $ luma microservice update --name wdupdate1  
     Profile: drag-sib 
     Microservice: 916 

Options: 
* ``-p, --profile “STRING”``
* ``-ms, --microservice ID``
* ``--name “STRING”``
* ``-path, --icon-file “FILE PATH”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Microserivce-version:

Microservice-version
--------------------
Commands that add, modify, and delete microservice versions.

.. _Microservice-version Add:

Add
^^^
Adds a version to a specified microservice.

Example:
.. code-block:: python
   $ luma microservice-version add 
     Profile: drag-sib 
     Microservice: 916
     Label: prod
     Version: 1.0.8 
     Port: 5000
     Microservice-file-path: “C:\Tests\ProtractorAuto\WidgetFiles\magic.tar.gz”

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

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Microservice-version Exec:

Exec
^^^^
Sends commands directly to Docker. For more information, consult the 'Docker documentation <https://docs.docker.com/engine/reference/commandline/docker/>'

Example:
.. code-block:: python
   $ luma microservice-version exec “Docker command” 
     Profile: drag-sib 
     Mirocservice: 916 
     Version Number: 1.0.8

Options: 
* ``-p, --profile “STRING”``
* ``-ms, --microservice ID``
* ``-v, --version VERSION NUMBER``
* ``--target [one, all]`` 
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Microservice-version Logs:

Logs
^^^^
Returns the logs for a specified microservice version.

Example:
.. code-block:: python
   $ luma microservice-version logs 
     Profile: drag-sib 
     Microservice: 916
     Version Number: 1.0.8

Options: 
* ``-p, --profile “STRING”``
* ``-ms, --microservice ID``
* ``-v, --version INTAGER (*.*.*)``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Microservice-version Ls:

Ls
^^
Lists all versions of a specified microservice container.

Example:
.. code-block:: python
   $ luma microservice-version ls 
     Profile: drag-sib 
     Microservice: 916

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

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. note:
   Version number is filtered as “major=*&minor=*&patch=*”

.. _Microservice-version Rm:

Rm
^^
Removes a version from a specified microservice container.

Example:
.. code-block:: python
   $ luma microservice-version rm
     Profile: drag-sib
     Microservice: 916
     Version: 1.0.9

Options: 
* ``-p, --profile “STRING”``
* ``-ms, --microservice ID``
* ``-vm, --version-mask INTAGER (*.*.*)``
* ``-v, --version INTAGER (*.*.*)``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Microservice-version Start:

Start
^^^^^
Starts a microservice version.

Example:
.. code-block:: python
   $ luma microservice-version start
     Profile: drag-sib
     Microservice: 916
     Version: 1.0.8

Options: 
* ``-p, --profile “STRING”``
* ``-ms, --microservice ID``
* ``-v, --version INTAGER (*.*.*)``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Microservice-version Stop:

Stop
^^^^
Stops a microservice version. A microservice version cannot be stopped if it is being used in an experience.

Example:
.. code-block:: python
   $ luma microservice-version stop
     Profile: drag-sib
     Microservice: 916
     Version: 1.0.8

Options: 
* ``-p, --profile “STRING”``
* ``-ms, -- microservice ID``
* ``-v, --version INTAGER (*.*.*)``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Microservice-version Update:

Update
^^^^^^
Updates the label of a microservice version.

Example:
.. code-block:: python
   $ luma microservice-version update --label dev
     Profile: drag-sib
     Microservice: 916
     Version: 1.0.8

Options: 
* ``-p, --profile “STRING”``
* ``-ms, -- microservice ID``
* ``-v, --version INTAGER (*.*.*)``
* ``-l, --label “[dev, old, prod]”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Org:

Org
---
Commands that list the organizations associated with a specified environment or organization.

.. _Org Child-orgs:

Child-orgs
^^^^^^^^^^
Lists the child organizations that a specified profile’s organization can share with.

Example:
.. code-block:: python
   $ luma org child-orgs
     Profile: drag-sib

Options: 
* ``-p, --profile “STRING”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--filter “{JSON VALUE=SPECIFIC VALUE}”``
* ``--json``
* ``--help``

.. _Org Ls:

Ls
^^
Lists the organizations inside a specified environment.

Example:
.. code-block:: python
   $ luma org ls
     Env: Dragonfly

Options: 
* ``--env “STRING”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--filter “{JSON VALUE=SPECIFIC VALUE}”``
* ``--json``
* ``--help``

.. _Profile:

Profile
-------
Commands that add, modify, or delete profiles.

.. _Profile Add:

Add
^^^
Adds a profile to a specified enviroment, and associates the profile to a specific organization.

Example:
.. code-block:: python
   $ luma profile add
     Profile name: dragon-sib
     
     Name of Env you want to use with this profile: Dragonfly
     
     Org ID you want to associate with this profile: 67

Options: 
* ``--profile-name “STRING”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--help``

.. _Profile Ls:

Ls
^^
Lists all profiles associated with the client id and secrete.

Example:
.. code-block:: python
   $ luma profile ls

Options: 
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--help``

.. _Profile Rm:

Rm
^^
Deletes a profile.

Example:
.. code-block:: python
   $ luma profile rm
     Profile: drag-sib

Options: 
* ``-p, --profile “STRING”``
* ``--help``

.. _Version:

Version
-------
Command that list what version of luma the current machine is using.

Version
^^^^^^^
Lists the luma version that the current machine is on.

Example:
.. code-block:: python
   $ luma version

Options: 
* ``--help``

.. _Widget:

Widget
------
Commands that add, modify, share, and delete widget containers.

.. _Widget Access:

Access
^^^^^^
Shares and/or Unshares a widget container with the specified child organizations.

Example:
.. code-block:: python
   $ luma widget access --add 68
     Profile: drag-sib
     Widget: 834

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

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Widget Add:

Add
^^^
Adds a widget container.

Example:
.. code-block:: python
   $ luma widget add
     Profile: dragon-sib
     Name: example1
     Url Ref: example1

Options: 
* ``-p, --profile “STRING”``
* ``--name “STRING”``
* ``--url-ref “LOWERCASE STRING”``
* ``-path, --icon-file “FILE PATH”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”`` 
* ``--json`` 
* ``--table`` 
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Widget Ls:

Ls
^^
Lists all the widget containers in a specified profile's organization. 

Example:
.. code-block:: python
   $ luma widget ls
     Profile: drag-sib

Options: 
* ``-p, --profile “STRING”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”`` 
* ``--filter “{JSON VALUE=SPECIFIC VALUE}”`` 
* ``--page INTAGER``
* ``--pagesize INTAGER``
* ``--json`` 
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Widget Rm:

Rm
^^
Removes a widget container.

Example:
.. code-block:: python
   $ luma widget rm
     Profile: drag-sib
     Widget: 890

Options: 
* ``-p, --profile “STRING”``
* ``-w, --widget ID``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table`` 
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Widget Update:

Update
^^^^^^
Updates a widget container’s name or image.

Example:
.. code-block:: python
   $ luma widget update --name example1
     Profile: drag-sib
     Widget: 893

Options: 
* ``-p, --profile “STRING”``
* ``-w, --widget ID``
* ``--name “STRING”``
* ``-path, --icon-file “FILE PATH”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``  
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Widget-version:

Widget-version
--------------
Commands that add, modify, and delete widget versions.

.. _Widget Add:

Add
^^^
Adds a version to a specified widget container.

Example:
.. code-block:: python
   $ luma widget-version add
     Profile: drag-sib
     Widget: 899
     Label: prod 
     Version Number: 1.0.4
     Widget File Path: “C:\Tests\Auto\WidgetFiles\layout.tar.gz”
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

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Widget-version Exec:

Exec
^^^^
Sends commands directly to Docker. 

For more information, consult the `Docker documentation <https://docs.docker.com/engine/reference/commandline/docker/>`_.

Example:
.. code-block:: python
   $ luma widget-version exec “Docker command”
     Profile: drag-sib
     Widget: 899
     Version Number: 1.0.6

Options: 
*	-p, --profile “STRING”
*	-w, --widget ID
*	-v, --version INTAGER (*.*.*)
*	--target [one, all]
*	--json 
*	--table (will be depricated) 
*	--help

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Widget-version Logs:

Logs
^^^^
Returns the logs for a widget version.

Example:
.. code-block:: python
   $ luma widget-version logs
     Profile: drag-sib
     Widget: 899
     Version Number: 1.0.6

Options: 
* ``-p, --profile “STRING”``
* ``-w, --widget ID``
* ``-v, --version INTAGER (*.*.*)``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Widget-version Ls:

Ls
^^
Lists all the version for a specified widget container.

Example:
.. code-block:: python
   $ luma widget-version ls
     Profile: drag-sib
     Widget: 899

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

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. note:
   Version number is filtered as “major=*&minor=*&patch=*”

.. _Widget-version Rm:

Rm
^^
Deletes a widget version. This cannot be done if a widget version is being used in an experience.

Example:
.. code-block:: python
   $ luma widget version rm
     Profile: drag-sib
     Widget: 899
     Version Number: 1.0.7

Options: 
* ``-p, --profile “STRING”``
* ``-w, --widget ID``
* ``-vm, --version-mask INTAGER (*.*.*)``
* ``-v, --version INTAGER (*.*.*)``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table`` 
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Widget-version Start:

Start
^^^^^
Starts a widget version.

Example:
.. code-block:: python
   $ luma widget-version start
     Profile: drag-sib
     Widget: 899
     Version Number: 1.0.0

Options: 
* ``-p, --profile “STRING”``
* ``-w, --widget ID``
* ``-v, --version INTAGER (*.*.*)``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Widget-version Stop:

Stop
^^^^
Stops a widget version. This cannot be done if a widget version is being used in an experience.

Example:
.. code-block:: python
   $ luma widget-version stop
     Profile: drag-sib
     Widget: 899
     Version Number: 1.0.0

Options: 
* ``-p, --profile “STRING”``
* ``-w, --widget ID``
* ``-v, --version INTAGER (*.*.*)``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``--help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Widget-version Update:

Update
^^^^^^
Updates a widget version’s label.

Example:
.. code-block:: python
   $ luma widget-version update -l dev
     Profile: drag-sib
     Widget: 899
     Version Number: 1.0.0

Options: 
* ``-p, --profile “STRING”``
* ``-w, --widget ID``
* ``-v, --version INTAGER (*.*.*)``
* ``-l, --label “[dev, old, prod]”``
* ``-f, --format “{JSON VALUE}, {JSON VALUE}”``
* ``--json``
* ``--table``
* ``–help``

.. deprecated:: ``--table``
     Use ``--format`` to see the JSON values organized in table format.

.. _Ls Commands:

Ls Commands
-----------
Limits Ls search results by:

* Greater Than
* Less Than
* Greater Than or Equal To
* Less Than or Equal To
* Containing

.. _Ls Commands gt:

gt
^^
Looks for anything that contains more than the specified value. 

example:
.. code-block:: python
   $ luma org ls --filter “name=gt:dragon”

.. _Ls Commands lt:

lt
^^
Looks for anything that contains less than the specified value.

example:
.. code-block:: python
   $ luma org ls --filter “name=lt:dragon”

.. _Ls Commands gte:

gte
^^^
Looks for anything that contains either the specified value or more than the specified value.

example:
.. code-block:: python
   $ luma org ls --filter “name=gte:dragon”

.. _Ls Commands lte:

lte
^^^
Looks for anything that contains either the specified value or less than the specified value.

example:
.. code-block:: python
   $ luma org ls --filter “name=lte:dragon”

.. _Ls Commands ct:

ct
^^
Looks for anything that contains the specified value.

example:
.. code-block:: python
   $ luma org ls --filter “name=ct:dragon”

.. _Version Commands:

Version Commands
----------------
Commands that modify your CLI or version.

.. _Version Commands Install:

Install
^^^^^^^
Installs luma.

example: 
.. code-block:: python
   $ pip3 install --index-url https://test.pypi.org/simple/ --extra-index-url https://pypi.org/simple luma

.. _Version Commands Upgrade:

Upgrade
^^^^^^^
Updates the version of luma on the current machine. 

example:
.. code-block:: python
   $ pip3 install luma --upgrade

.. _Version Commands Help:

Help
^^^^
Describes and lists the possible sub-commands for any command. This can be done by running any command without passing in any options or by passing in the ``--help`` flag.

example:
.. code-block:: python
    $ luma --help
   
    $ luma ls --help

.. _Additional Info:

Additional Info
---------------
* Dates must be in the format: year-month-day
* Must include “” around all arguments
* Must include “&” between arguments when using multiple arguments 
