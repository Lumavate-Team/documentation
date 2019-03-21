Alternative CLI Installations
-----------------------------

For installing the CLI by downloading files, see the instruction sets below. 

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
  