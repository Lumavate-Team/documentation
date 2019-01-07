============
CLI
============

The Lumavate Commandline Interface (CLI) can be used to streamline many administrative tasks, such as adding & updating widgets, microservices, and/or
component sets.

Behind the scenes, the CLI uses the native REST APIs available via the Platform.
The CLI is also available via open-source here.

Config Summary
^^^^^^^^^^^^^^

* Installation
* Provisioning Credentials
* Configuration
* Example Commands

Installation
------------

From pip
^^^^^^^^

* On Windows, run BASH as admin and omit 'sudo'

  `$ sudo pip3 install luma`

From source
^^^^^^^^^^^

* Clone this repo.
* CD into the CLI dir and run

  `$ sudo pip3 install .`

Installing the CLI as a non-admin
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* Install luma using the --user flag and then add to path
  `$ pip3 install luma --user`

CLI Support
-----------

* The CLI is written for and tested in a BASH shell
* To get the most of of the CLI, use it with ZSH. This enables extra features such as showing help text during autocompletion
* To activate autocompletion after install, restart your terminal or source your shell config (Either .zshrc or .bash_profile)

Provisioning Credentials
-------------------------

* In the Lumavate App, navigate to the Lumavate CLI page inside a command center
* Provisioning CLI credentials will generate credentials for the user you are currently signed in as
* When running the add profile command, you will have the option to associate the new profile to any organization your user has access to, regardless of the command center you are currently in

Configuration
-------------

* Configuring the CLI requires two steps, configuring environments and configuring profiles.
    * **Environments** know how to get and refresh tokens so you stay authorized with the platform as a user.
    * **Profiles** give the user a company context which is required by most of the platform API.

CLI Env
^^^^^^^
* To configure the CLI Env, run the generated command from the Lumavate CLI page in the app in your terminal
* To configure each Env value one by one, run
  `$ luma env config`

Env Name: prod
App: appUrl
Token: token
Audience: audience
Client id: clientId
Client secret: clientSecret

#### CLI Profile:
* To add a profile to the CLI, run::
$ luma profile add

Profile Name: intel
Env: prod
Org ID you want to associate with this profile: 11

Running Commands
----------------
* To list top level commands, run::
  $ luma

* To get help with any command or subcommand, run it without passing in any options or, pass in the --help flag
* As an example let's create a microservice, create a version, upload a docker image, and start the service

::
$ luma microservice add
Profile: intel
Name: Auth Service
Url ref: auth
| id | name         | urlRef | createdAt         | createdBY          |
| 45 | Auth Service | auth   | 10/16/18 20:29:49 | john+doe@gmail.com |

::
$ luma microservice access --profile intel
Microservice: auth
| failed | sharedWith | unsharedWith | resultingGrantees |
| []     | []         | []           | []                |

::
$ luma microservice access -p intel --microservice auth --add "Eli Lilly" --add Nvidia
| failed | sharedWith   | unsharedWith | resultingGrantees        |
| []     | [{id}, {id}] | []           | ['Eli Lilly', 'Nvidia']  |

::
$ luma microservice-version add -p intel --version-number 0.1.0 --microservice-file-path ~/Desktop/auth-service.tar.gz --label prod --port 8080 -ms auth
| id  | actualState | versionNumber | label | createdAt         | createdBy          |
| 107 | created     | 0.1.0         | prod  | 10/16/18 20:46:44 | john+doe@gmail.com |

::
$ luma microservice-version start -p intel
Microservice: auth
Version: 0.1.0

