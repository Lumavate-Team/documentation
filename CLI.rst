============
CLI
============

The Lumavate Commandline Line Interface (CLI) can be used to streamline many administrative tasks, such as adding & updating widgets, microservices, and/or component sets.

The CLI uses the native REST APIs available via the Platform. To learn more about Lumavate's REST APIs, please go here: <link to come>.

If you would like to know more about the CLI, it is available via open-source here: <link to come>.

The following documentation will explain:

* Requarments
* Support Infomration
* Installation
* Provisioning Credentials
* Configuration
* Example Commands

Requarments
-----------
You will need to install 'Python 3.1.1 <https://www.python.org/downloads/>' or higher in order to use the CLI. 

It is also recomended that you install 'Gitbash <https://git-scm.com/downloads>'. 

### CLI support:
---
* The CLI is written for and tested in a BASH shell.
* To get the most out of the CLI, use it with ZSH. This enables extra features such as showing help text during autocompletion.
* To activate autocompletion after install, restart your terminal or source your shell config (Either .zshrc or .bash_profile).

Installation
------------
The CLI can be installed two differnt ways: through Pip or from the source.

From pip
^^^^^^^^
As a Non-admin::
  $ sudo pip3 install luma

As an Admin::
  $ pip3 install luma

From source
^^^^^^^^^^^

Installing the CLI as a non-admin:
1) Clone this repo.
2) CD into the CLI dir
3) Run::
  $ pip3 install luma --user
4) Add the returned path url to the path 
  (Example Response):: 
  $

As an Admin
1) Clone this repo.
2) CD into the CLI dir
3) Run::
  $ sudo pip3 install .

Provisioning Credentials
-------------------------
1) Navigate to the Lumavate CLI page in a Lumavate command center
2) Click the Provisioning CLI credentials button. Several boxes The platform will generate credentials for the user you are currently signed in as.
3) Copy the information from the Configure an Environment field
4) Past the command into your Bash window
5) Copy the information from the Add a Profile field
6) You will be presented with a list of organizations, pick the one you want to associate your profile with

.. Note:
While running the profile command, you will have the option to associate the new profile to any organization your user has access to, regardless of the command center you are currently in

Configuration
-------------
* Configuring the CLI requires two steps, configuring environments and configuring profiles.
    * **Environments** know how to get and refresh tokens so you stay authorized with the platform as a user.
    * **Profiles** give the user a company context which is required by most of the platform API.

#### CLI Env:
* To configure the CLI Env, run the generated command from the Lumavate CLI page in the app in your terminal
* To configure each Env value one by one, run::
$ luma env config

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

