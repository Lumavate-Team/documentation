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
You will need to install 'Python 3.1.1 <https://www.python.org/downloads/>' or higher in order to use the CLI. 

It is recommended that you install 'Gitbash <https://git-scm.com/downloads>' as the CLI is written for and tested in a BASH shell. 

.. Note:
  To get the most out of the CLI, use it with 'ZSH <https://sourceforge.net/projects/zsh/files/>'. This enables extra features such as showing help text during autocompletion. 

Installation
------------
The CLI can be installed two different ways: through Pip or from the source.

From pip
^^^^^^^^
As a Non-admin:
  :$ sudo pip3 install luma

As an Admin:
  :$ pip3 install luma

From source
^^^^^^^^^^^

Installing the CLI as a non-admin:
1) Clone this repo.
2) CD into the CLI dir
3) Run:
  :$ pip3 install luma --user
4) Add the returned path URL to the path 
  (Example Response): 
  :$ The script luma.exe is installed in 'C:\ComputerName\UserName\AppData\Roaming\Python\Python37\Scripts' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
  
As an Admin
1) Clone this repo.
2) CD into the CLI dir
3) Run:
  :$ sudo pip3 install luma

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

Using the pre-set configuration:
1) Log into the command center you want to modify with the CLI
2) Go to the CLI tab located in the side menue bar
3) Copy the information from the Configure an Environment field. It should look like this:
  :$ luma env config --env-name prod --app https://not-a-real-realm.dragonfly.lumavate-type.com --audience https://dragonfly.lumavate-type.com/notarealapp --token dragonfly-lumavate-type.notarealtoken.com --client-id NotARealId1234j2eIxKILomCdA --client-secret NotARealClientSecretEqeKWD5JgUtzsRkhNNXMPQM6auPhTTjVK
4) Past the command into your Bash window 

Using your own configuration:
1) Log into the command center you want to modify with the CLI
2) Go to the CLI tab located in the side menue bar
3) Take note of the app, audience, token, client-id, and client-secret information from the Configure an Environment field
4) In your Bash window, run:
  : $ luma env config
5) Fill out the prompts as they appear on the screen with the appropriate information. It should look like this when you are done:
  :$ Env Name: <<what you want to call your envrioment>>
  App: <<enviroment Url>>
  Token: <<enviroment token>>
  Audience: <<envitoment audience>>
  Client id: <<user clientId>>
  Client secret: <<user clientSecret>>

.. Note: 
  The CLI uses Client id and Client secret to asscociate a users context to a machine. From this point forward, user will refer to the client id and client secreate information used to setup the envroment in the CLI. 
  
Setting up Profiles:
^^^^^^^^^^^^^^^^^^^
Profiles can be set-up using the Lumavate pre-set command or using your own configuration. You will need to have :ref: 'configured an envrioment' on your machine through the CLI before you configure a profile.  

Using a pre-set configuration:
1) Log into a Lumavate command center
2) Navigate to the CLI  tab located in the side menue bar
2) Copy the information from the Add a Profile field. It should look like this:
  :$ luma profile add --env prod
3) Past the command into your Bash window
4) You will be prompted to name your profile. It should look like this:
   :$ Profile Name: <<what you want to call your profile>>
5) You will then be presented with a list of organizations. Pick the one you want to edit with this profile. It should look like this:
  :$ id Org Name                 Org Type Test Org
     35 Sample command center     dev      None
     49 Sample Studio             studio   False

    Org ID you want to associate with this profile: <<org id>>

     
Using your own configuration:
1) In your Bash window, run:
  :$ luma profile add
2) You will be prompted to name your profile. It should look like this:
   :$ Profile Name: <<what you want to call your profile>>
3) A list of environments will appear. Select which environment you wish to associate with your profile:
    
    Env Name            App                                         Audience                               Token
     Name      https://not-a-realm.place.lumavate-type.com https://place.lumavate-type.com/notaapp place-lumavate-dev.notatokey.com
     
     Env: <<envrioment name you want your profile associated with>>
4) A list of organizations will appear. Pick the one you want to edit with this profile. It should look like this:
     :$ id Org Name                 Org Type Test Org
     35 Sample command center     dev      None
     49 Sample Studio             studio   False

     Org ID you want to associate with this profile: <<org id>>

.. Warning:
  If there are two profiles or environments with the same name, the newer version will overwrite the older version. Profiles in different environments can have the same name without overwriting each other.  

.. Note:
  While running the profile command, you will have the option to associate the new profile to any organization your user has access to   regardless of the command center you are currently in.

CLI Syntax
==========

This CLI will allow users to interact with the Lumavate platform from a terminal. For setup instructions, look at the 'Github readme <>' or the :ref: 'CLI documentation <CLI>'. All the main commands can be found in the side navigation pane. Each of these main commands has their subcommands listed below them. Pass the --help flag with the command for more information on how to use them and how to use their subcommands.

All commands sent to bash will start with::$ luma

Index: 
1.	API
2.	Component-set
3.	Component-set-version
4.	Env
5.	Microservice
6.	Microservice-version
7.	Org
8.	Profile
9.	Version
10.	Widget
11.	Widget-version
12.	Ls Commands
13. Version Commands
14.	Additional Info


API
---
Commands that directly query the API.

Delete
^^^^^^
Calls a delete command in order to remove something through the API. 

Example:
:$ luma api delete /iot/v1/containers/898?expand=all
    profile: dragon-sib

Options:
* -p, --profile “STRING”
* --help

Get
^^^
Calls a get command in order to return information from the API.

Example:
:$ luma api get /iot/v1/containers?expand=all
    profile: dragon-sib

Options: 
* -p, --profile “STRING”
* --help

Post
^^^^
Calls a post command in order to add something through the API. 

Example:
:$ luma api post /iot/v1/containers?expand=all -d ‘{“id:0, ”type”:”widget”, ”name”:”examplepost2”, ”urlRef”:”examplepost2”, ”ephemeralKey”: "67/temp/c287aaecab1840bc8bd6e52132409c30__adobe.svg”}’
  profile: dragon-sib

Options: 
* -p, --profile “STRING”
* -d, --data ‘{JSON}’
* --help

Put
^^^
Calls a put command in order to change something through the API.

Example:
:$ luma api post /iot/v1/containers?expand=all -d ‘{“id:0, ”type”:”widget”, ”name”:”examplepost2”, ”urlRef”:”exaplepost2”,                 ”ephemeralKey”: "67/temp/c287aaecab1840bc8bd6e52132409c30__adobe.svg”}’
  profile: dragon-sib

Options: 
* -p, --profile “STRING”
* -d, --data ‘{JSON}’
* --help

Component-set
-------------
Commands that create, modify, share, and delete component-set containers.

Access
^^^^^^
Shares and Unshares component-set containers with child organizations.

Example:
:$ luma component-set access --add 68
  profile: drag-sib
  component set: 273

Options: 
*	-p, --profile “STRING”
*	-cs, --component-set ID
*	--add ID
*	--rm ID
*	--absolute ID
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help

Add
^^^
Adds a component-set container to the command center your profile is associated with. 

Example:
:$ luma component-set add
  Profile: drag-sib
  Name: example1
  Url Ref: example1

Options: 
*	-p, --profile “STRING”
*	--name “STRING”
*	--url-ref “STRING”
*	-path, --icon-file “FILE PATH”
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json 
*	–table (will be depricated)
*	--help

Ls
^^
Lists all component-set containers in the specified profile environment. 

Example:
:$ luma component-set ls
   Profile: drag-sib

Options:
*	-p, --profile “STRING”
*	-f, --format “{JSON VALUE}, {JSON VALUE}” 
*	--filter “{JSON VALUE=SPECIFIC VALUE}”
*	--page INTAGER 
*	--pagesize INTAGER
*	--json
*	--table (will be depricated)
*	--help

Rm
^^
Deletes a component-set container. This can only be done after all versions in the container have been deleted.

Example:
  :$ luma component-set rm
    Profile: drag-sib
    Component set: 463

Options: 
*	-p, --profile “STRING”
*	-cs, --component-set ID
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help 

Update
^^^^^^
Updates the name or image of a component-set container. 

Example:
  :$ luma component-set update --name ExampleUpdateName1
     Profile: drag-sib
     Component set: 246

Options: 
*	-p, --profile “STRING”
*	-cs, --component-set ID
*	--name “STRING”
*	-path, --icon-file “FILE PATH”
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help

Component-set-version
---------------------
Commands that create, modify, and delete component-set versions.

Add
^^^
Adds a version to a specified component-set container.  

Example:
  :$ luma component-set-version add 
     Profile: drag-sib
     Component set: 272
     Label: prod
     Version: 1.0.11
     Component set file: “C:\Tests\Auto\WidgetFiles\Archive.zip”

Options: 
*	-p, --profile “STRING”
*	-cs, --component-set ID
*	-path, --component-set-file-path “FILE PATH”
*	-fv, --from-version ID
*	-v, --version INTAGER (*.*.*)
*	--patch INTAGER
*	--minor INTAGER
*	--major INTAGER
*	--css-includes “STRING”
*	--direct-includes “STRING”
*	-l, --label “[prod, dev, old]”
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help

.. Warning:
  File paths with spaces in them may need to be specified in the main command using the :$ -path option as some computers do not accept these paths any other way.
  
Components
^^^^^^^^^^
Returns the JSON of a component-set version. 

Example:
  :$ luma component-set-version components
     Profile: drag-sib
     Component set: 272

Options: 
*	-p, --profile “STRING”
*	-cs, --component-set ID
*	-v, --version INTAGER (*.*.*)
*	--json
*	--table (will be depricated)
*	--help

Ls
^^
Lists all versions in a specified component-set container.

Example:
  :$ luma component-set-version ls
     Profile: drag-sib
     Component-set: 274

Options: 
*	-p, --profile “STRING”
*	-cs, --component-set ID
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--filter “{JSON VALUE=SPECIFIC VALUE}”
*	--page INTAGER
*	--pagesize INTAGER
*	--json
*	--table (will be depricated)
*	--help

Rm
^^
Deletes a version from a specified component-set container.

Example:
  :$ luma component-set-version rm
     Profile: drag-sib
     Component set: 272
     Version number: 1.0.11 

Options: 
*	-p, --profile “STRING”
*	-cs, --component-set ID
*	-vm, --version-mask INTAGER (*.*.*)
*	-v, --version INTAGER (*.*.*)
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help

Update
^^^^^^
Updates the label of a specified component-set version.

Example:
  :$ luma component-set-version update -l dev 
     Profile: drag-sib 
     Component set: 272 
     Version number: 3.0.0

Options: 
*	-p, --profile “STRING”
*	-cs, --component-set ID
*	-v, --version INTAGER (*.*.*)
*	-l, --label “[prod, dev, old]”
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help

Env
---
Commands that create, modify, and delete environments.

Config
^^^^^^
Creates an environment. 

Example:
  :$ luma env config
     Env name: Dragonfly
     App: https://example-realm.dragonfly.lumavate-type.com
     Token: dragonfly-lumavate-type.not-a-real-token.com
     Audience: https://dragonfly.lumavate-type.com/notarealaudience
     Client secret: NotARealClientSecretEqeKWD5JgUtzsRkhNNXMPQM6auPhTTjVK
     Client id: NotARealId1234j2eIxKILomCdA

Options: 
*	--env-name “STRING”
*	--app “LINK”
*	--token “LINK”
*	--audience “LINK”
*	--client-id ID
*	--client-secret SECRET
*	--json
*	--help

Ls
^^
Lists all the environments the user has access to.

Example:
  :$ luma env ls

Options: 
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--help

Rm
^^
Removes a specified environment. 

Example:
  :$ luma env rm
     Name: Environment I Want To Remove

Options: 
*	--env-name “STRING”
*	--help

Microservice
------------
Commands that create, modify, share, and delete microservice containers.

Access
^^^^^^
Shares and/or unshares a microservice container with the specified child organizations. 

Example:
  :$ luma microservice access --add 68
     Profile: drag-sib
     Microservice: 851

Options: 
*	-p, --profile “STRING”
*	-ms, --microservice ID
*	--add ID
*	--rm ID
*	--absolute ID
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated) 
*	--help

Add
^^^
Adds a microservice container to the command center associated with the specified profile.

Example:
  :$ luma microservice add 
     Profile: drag-sib
     Name: example1
     Url Ref: example1

Options: 
*	-p, --profile “STRING”
*	--name “STRING”
*	--url-ref “STRING”
*	-path, --icon-file “FILE PATH”
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help

Ls
^^
Lists all microservices containers in the command center associated with the specified profile.

Example:
  :$ luma microservice ls 
     Profile: drag-sib

Options: 
*	-p, --profile “STRING”
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--filter “{JSON VALUE=SPECIFIC VALUE}”
*	--page INTAGER
*	--pagesize INTAGER
*	--json
*	--table (will be depricated)
*	--help

Rm
^^
Removes a microservice container from the command center associated with the specified profile. 

Example:
  :$ luma microservice rm 
     Profile: drag-sib 
     Microservice: 916

Options: 
*	-p, --profile “STRING”
*	-ms, --microservice ID
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help

Update
^^^^^^
Updates the name or image of a microservice container from the command center associated with the specified profile.

Example:
  :$ luma microservice update --name wdupdate1  
     Profile: drag-sib 
     Microservice: 916 

Options: 
*	-p, --profile “STRING”
*	-ms, --microservice ID
*	--name “STRING”
*	-path, --icon-file “FILE PATH”
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help

Microservice-version
--------------------
Commands that add, modify, and delete microservice versions.

Add
^^^
Adds a version to a specified microservice.

Example:
  :$ luma microservice-version add 
     Profile: drag-sib 
     Microservice: 916
     Label: prod
     Version: 1.0.8 
     Port: 5000
     Microservice-file-path: “C:\Tests\ProtractorAuto\WidgetFiles\magic.tar.gz”

Options: 
*	-p, --profile “STRING”
*	-ms, --microservice ID
*	--port INTAGER
*	-image, --docker-image “FILE PATH”
*	-path, --microservice-file-path “FILE PATH”
*	-fv, --from-version INTAGER (*.*.*)
*	-v, --version INTAGER (*.*.*)
*	--patch INTAGER
*	--minor INTAGER
*	--major INTAGER
*	--env-var ‘{“STRING”:”KEY”}’
*	-l, --label “[dev, old, prod]”
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help

Exec
^^^^
Sends commands directly to Docker. For more information, consult the 'Docker documentation <https://docs.docker.com/engine/reference/commandline/docker/>'

Example:
  :$ luma microservice-version exec “Docker command” 
     Profile: drag-sib 
     Mirocservice: 916 
     Version Number: 1.0.8

Options: 
*	-p, --profile “STRING”
*	-ms, --microservice ID
*	-v, --version VERSION NUMBER
*	--target [one, all] 
*	--json
*	--table (will be depricated)
*	--help

Logs
^^^^
Returns the logs for a specified microservice version.

Example:
  :$ luma microservice-version logs 
     Profile: drag-sib 
     Microservice: 916
     Version Number: 1.0.8

Options: 
*	-p, --profile “STRING”
*	-ms, --microservice ID
*	-v, --version INTAGER (*.*.*)
*	--json
*	--table (will be depricated)
*	--help

Ls
^^
Lists all versions of a specified microservice container.

Example:
  :$ luma microservice-version ls 
     Profile: drag-sib 
     Microservice: 916

Options: 
*	-p, --profile “STRING”
*	-ms, --microservice ID
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--filter “{JSON VALUE=SPECIFIC VALUE}”
*	--page INTAGER
*	--pagesize INTAGER
*	--json
*	--table (will be depricated)
*	--help

Rm
^^
Removes a version from a specified microservice container.

Example:
  :$ luma microservice-version rm
     Profile: drag-sib
     Microservice: 916
     Version: 1.0.9

Options: 
*	-p, --profile “STRING”
*	-ms, --microservice ID
*	-vm, --version-mask INTAGER (*.*.*)
*	-v, --version (will be removed)
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help

Start
^^^^^
Starts a microservice version.

Example:
  :$ luma microservice-version start
     Profile: drag-sib
     Microservice: 916
     Version: 1.0.8

Options: 
*	-p, --profile “STRING”
*	-ms, --microservice ID
*	-v, --version INTAGER (*.*.*)
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help

Stop
^^^^
Stops a microservice version. A microservice version cannot be stopped if it is being used in an experience.

Example:
  :$ luma microservice-version stop
     Profile: drag-sib
     Microservice: 916
     Version: 1.0.8

Options: 
*	-p, --profile “STRING”
*	-ms, -- microservice ID
*	-v, --version INTAGER (*.*.*)
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help

Update
^^^^^^
Updates the label of a microservice version.

Example:
  :$ luma microservice-version update --label dev
     Profile: drag-sib
     Microservice: 916
     Version: 1.0.8

Options: 
*	-p, --profile “STRING”
*	-ms, -- microservice ID
*	-v, --version INTAGER (*.*.*)
*	-l, --label “[dev, old, prod]”
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help

Org
---
Commands that list the organizations associated with a specified environment or organization.

Child-orgs
^^^^^^^^^^
Lists the child organizations that a specified profile’s organization can share with.

Example:
  :$ luma org child-orgs
     Profile: drag-sib

Options: 
*	-p, --profile “STRING”
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--filter “{JSON VALUE=SPECIFIC VALUE}”
*	--json
*	--help

Ls
^^
Lists the organizations inside a specified environment.

Example:
  :$ luma org ls
     Env: Dragonfly

Options: 
*	--env “STRING”
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--filter “{JSON VALUE=SPECIFIC VALUE}”
*	--json
*	--help

Profile
-------
Commands that add, modify, or delete profiles.

Add
^^^
Adds a profile to a specified enviroment, and associates the profile to a specific organization.

Example:
  :$ luma profile add
     Profile name: dragon-sib
     Name of Env you want to use with this profile: Dragonfly
     Org ID you want to associate with this profile: 67

Options: 
*	--profile-name “STRING”
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--help

Ls
^^
Lists all profiles associated with the client id and secrete.

Example:
  :$ luma profile ls

Options: 
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--help

Rm
^^
Deletes a profile'

Example:
  :$ luma profile rm
     Profile: drag-sib

Options: 
*	-p, --profile “STRING”
*	--help

Version
-------
Command that list what version of luma the current machine is using.

Version
^^^^^^^
Lists the luma version that the current machine is on.

Example:
  :$ luma version

Options: 
*	--help

Widget
------
Commands that add, modify, share, and delete widget containers.

Access
^^^^^^
Shares and/or Unshares a widget container with the specified child organizations.

Example:
  :$ luma widget access --add 68
     Profile: drag-sib
     Widget: 834

Options: 
*	-p, --profile “STRING”
*	-w, --widget ID
*	--add ID
*	--rm ID
*	--absolute ID
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json
*	--table (will be depricated)
*	--help

Add
^^^
Adds a widget container.

Example:
  :$ luma widget add
     Profile: dragon-sib
     Name: example1
     Url Ref: example1

Options: 
*	-p, --profile “STRING”
*	--name “STRING”
*	--url-ref “LOWERCASE STRING”
*	-path, --icon-file “FILE PATH”
*	-f, --format “{JSON VALUE}, {JSON VALUE}” 
*	--json 
*	--table (will be depricated) 
*	--help

Ls
^^
Lists all the widget containers in a specified profile's organization. 

Example:
  :$ luma widget ls
     Profile: drag-sib

Options: 
*	-p, --profile “STRING”
*	-f, --format “{JSON VALUE}, {JSON VALUE}” 
*	--filter “{JSON VALUE=SPECIFIC VALUE}” 
*	--page INTAGER
*	--pagesize INTAGER
*	--json 
*	--table (will be depricated) 
*	--help

Rm
^^
Removes a widget container.

Example:
  :$ luma widget rm
     Profile: drag-sib
     Widget: 890

Options: 
*	-p, --profile “STRING”
*	-w, --widget ID
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json 
*	--table (will be depricated) 
*	--help

Update
^^^^^^
Updates a widget container’s name or image.

Example:
  :$ luma widget update --name example1
     Profile: drag-sib
     Widget: 893

Options: 
*	-p, --profile “STRING”
*	-w, --widget ID
*	--name “STRING”
*	-path, --icon-file “FILE PATH” 
*	-f, --format “{JSON VALUE}, {JSON VALUE}”  
*	--json 
*	--table (will be removed) 
*	--help

Widget-version
--------------
Commands that add, modify, and delete widget versions.

Add
^^^
Adds a version to a specified widget container.

Example:
  :$ luma widget-version add
     Profile: drag-sib
     Widget: 899
     Label: prod 
     Version Number: 1.0.4
     Widget File Path: “C:\Tests\Auto\WidgetFiles\layout.tar.gz”
     Port: 8080 

Options: 
*	-p, --profile “STRING”
*	--port INTAGER
*	-w, --widget ID
*	-path, --widget-file-path “FILE PATH”
*	 -image, --docker-image “FILE PATH”
*	-fv, --from-version INTAGER (*.*.*)
*	-v, --version INTAGER (*.*.*)
*	--patch INTAGER
*	--minor INTAGER
*	--major INTAGER
*	--env-var ‘{“STRING”:”KEY”}’ 
*	-l, --label “[dev, old, prod]”
*	-f, --format “{JSON VALUE}, {JSON VALUE}”  
*	--json 
*	--table (will be removed) 
*	--help

Exec
^^^^
Sends commands directly to Docker. For more information, consult the 'Docker documentation <https://docs.docker.com/engine/reference/commandline/docker/>'.

Example:
  :$ luma widget-version exec “Docker command”
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

Logs
^^^^
Returns the logs for a widget version.

Example:
  :$ luma widget-version logs
     Profile: drag-sib
     Widget: 899
     Version Number: 1.0.6

Options: 
*	-p, --profile “STRING”
*	-w, --widget ID
*	-v, --version INTAGER (*.*.*)
*	--json 
*	--table (will be depricated) 
*	--help

Ls
^^
Lists all the version for a specified widget container.

Example:
  :$ luma widget-version ls
     Profile: drag-sib
     Widget: 899

Options: 
*	-p, --profile “STRING”
*	-w, --widget ID
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--filter “{JSON VALUE=SPECIFIC VALUE}”
*	--page INTAGER
*	--pagesize INTAGER
*	--json 
*	--table (will be depricated) 
*	--help

Rm
^^
Deletes a widget version. This cannot be done if a widget version is being used in an experience.

Example:
  :$ luma widget version rm
     Profile: drag-sib
     Widget: 899
     Version Number: 1.0.7

Options: 
*	-p, --profile “STRING”
*	-w, --widget ID
*	-vm, --version-mask INTAGER (*.*.*)
*	-v, --version INTAGER (*.*.*)
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json 
*	--table (will be depricated) 
*	--help
	
Start
^^^^^
Starts a widget version.

Example:
  :$ luma widget-version start
     Profile: drag-sib
     Widget: 899
     Version Number: 1.0.0

Options: 
*	-p, --profile “STRING”
*	-w, --widget ID
*	-v, --version INTAGER (*.*.*)
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json 
*	--table (will be depricated) 
*	--help

Stop
^^^^
Stops a widget version. This cannot be done if a widget version is being used in an experience.

Example:
  :$ luma widget-version stop
     Profile: drag-sib
     Widget: 899
     Version Number: 1.0.0

Options: 
*	-p, --profile “STRING”
*	-w, --widget ID
*	-v, --version INTAGER (*.*.*)
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json 
*	--table (will be depricated) 
*	--help

Update
^^^^^^
Updates a widget version’s label.

Example:
  :$ luma widget-version update -l dev
     Profile: drag-sib
     Widget: 899
     Version Number: 1.0.0

Options: 
*	-p, --profile “STRING”
*	-w, --widget ID
*	-v, --version INTAGER (*.*.*)
*	-l, --label “[dev, old, prod]”
*	-f, --format “{JSON VALUE}, {JSON VALUE}”
*	--json 
*	--table (will be depricated) 
*	–help

Ls Commands
-----------
If you want to limit your ls results use:

gt
^^
Looks for anything that contains more than the specified value. 

example:
  :$ luma org ls --filter “name=gt:dragon”

lt
^^
Looks for anything that contains less than the specified value.

example:
  :$ luma org ls --filter “name=lt:dragon”

gte
^^^
Looks for anything that contains either the specified value or more than the specified value.

example:
  :$ luma org ls --filter “name=gte:dragon”

lte
^^^
Looks for anything that contains either the specified value or less than the specified value.

example:
  :$ luma org ls --filter “name=lte:dragon”

ct
^^
Looks for anything that contains the specified value.

example:
  :$ luma org ls --filter “name=ct:dragon”

Version Commands
----------------

install
^^^^^^^
Installs luma.

example: 
  :$ pip3 install --index-url https://test.pypi.org/simple/ --extra-index-url https://pypi.org/simple luma

upgrade
^^^^^^^
Updates the version of luma on the current machine. 

example:
  :$ pip3 install luma --upgrade
  
help
^^^^
Describes and lists the possible sub-commands for any command. This can be done by running any command without passing in any options or by passing in the --help flag.

example:
  :$ luma --help
Or
  :$ luma ls --help

Additional Info
---------------
* Dates must be in the format: year-month-day
* Must include “” around all arguments
* Must include “&” between arguments when using multiple arguments 
* Widget, microservice, and component-set version number is filtered as “major=*&minor=*&patch=*”
* API paths cannot include sort criteria
