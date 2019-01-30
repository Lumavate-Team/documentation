============
CLI
============

The Lumavate Commandline Line Interface (CLI) can be used to streamline many administrative tasks, such as adding & updating widgets, microservices, and/or component sets.

.. The CLI uses the native REST APIs available via the Platform. To learn more about Lumavate's REST APIs, please go here: <link to come>.

.. If you would like to know more about the CLI, it is available via open-source here: <link to come>.

The following documentation will explain:

* Requirements
* Installation
* Provisioning Credentials
* Configuration

Requirements
-----------
You will need to install `Python 3.1.1 <https://www.python.org/downloads/>`_ or higher in order to use the CLI. 

It is recommended that you install `Gitbash <https://git-scm.com/downloads>`_ as the CLI is written for and tested in a BASH shell. 

.. note::
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
       
       The script luma.exe is installed in 'C:\ComputerName\UserName\AppData\Roaming\Python\Python37\Scripts' which is not on PATH. 
       Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
  
Installing the CLI as an Admin:

 #. Clone this repo.
 #. CD into the CLI dir
 #. Run:
   
    .. code-block:: python
       
       $ sudo pip3 install luma

.. note::
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

.. note:: 
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
       
        profile Name: <<what you want to call your profile>>

 #. You will then be presented with a list of organizations. Pick the one you want to edit with this profile. It should look like this:
   
    .. code-block:: python
       
         id Org Name                 Org Type Test Org
         35 Sample command center     dev      None
         49 Sample Studio             studio   False

         Org ID you want to associate with this profile: <<org id>>

     
Using your own configuration:

 #. In your Bash window, run:
   
    .. code-block:: python
       
       $ luma profile add

 #. You will be prompted to name your profile. It should look like this:
   
    .. code-block:: python
       
        profile Name: <<what you want to call your profile>>

 #. A list of environments will appear. Select which environment you wish to associate with your profile:
   
    .. code-block:: python
       
       Env Name                                    App                                                  Audience                                         Token                                                                      Name
       https://not-a-realm.place.lumavate-type.com https://not-a-real-realm.dragonfly.lumavate-type.com https://place.lumavate-type.com/notanapp dragonfly-lumavate-type.notarealtoken.com place-lumavate-dev.notatokey.com prod
     
        Env: <<envrioment name you want your profile associated with>>

 #. A list of organizations will appear. Pick the one you want to edit with this profile. It should look like this:
   
    .. code-block:: python
       
        id Org Name                 Org Type Test Org
        35 Sample command center     dev      None
        49 Sample Studio             studio   False

        Org ID you want to associate with this profile: <<org id>>

.. warning::
   If there are two profiles or environments with the same name, the newer version will overwrite the older version. Profiles in different environments can have the same name without overwriting each other.  

.. note::
   While running the profile command, you will have the option to associate the new profile to any organization your user has access to   regardless of the command center you are currently in.
