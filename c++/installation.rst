.. _first_steps:

Installation
============

**Biicode** is a file-oriented Dependencies Manager for C and C++ developers. Install both 
biicode and the C/C++ tools to get started.

.. _download_client_binaries:

Install Biicode
-----------------

**Download** `Biicode Installer <https://www.biicode.com/downloads>`_ and double-click the downloaded package.
Open the terminal and **make sure biicode is installed**:


.. code-block:: bash

   ~$ bii --version

.. container:: infonote

    Check alternative installations for:

    *  :ref:`Debian based distributions <alternative_install_debian>`
    *  :ref:`Arch based distributions <alternative_install_archlinux>`
    *  :ref:`Running biicode from source <alternative_install_source>`


Install C/C++ tools
--------------------

Then install required tools like CMake and MinGW or GCC:

.. code-block:: bash

   ~$ bii setup:cpp


.. container:: infonote

    If any problem installing C/C++ tools, check :ref:`how to install C/C++ tools manually <cpp_installation>`.

.. container:: infonote

    The setup command installs programs in a directory called .biicode in your home directory.

Execute again to make sure the tools are installed:

.. code-block:: bash

   ~$ bii setup:cpp
   CMake 3.0.2 already installed
   gcc 4.8.2 already installed
   g++ 4.8.2 already installed


.. container:: todo

    **You're now ready to** :ref:`get started<cpp_getting_started>`.

.. _alternative_install_debian:

Debian based distributions
---------------------------
**Alternative install for Debian based distributions (Ubuntu, Raspbian)**

Use the ``apt-get`` program to install biicode through the APT repository:

    Quick install: 

    .. code-block:: bash

        wget http://apt.biicode.com/install.sh && chmod +x install.sh && ./install.sh


    .. container:: infonote

        Execute **bii setup:cpp** to make sure you've got all tools required.


    Step by step install:

    .. code-block:: bash

        # 1. Create a file named '/etc/apt/sources.list.d/biicode.list' and put the line corresponding to your linux distribution:
            
    	Ubuntu 12:
            	deb http://apt.biicode.com precise main

    	Ubuntu 13:
    		deb http://apt.biicode.com saucy main

    	Ubuntu 14:
    		deb http://apt.biicode.com trusty main
    		
    	Debian Wheezy:
    		deb http://apt.biicode.com wheezy main
    		

    	# 2. Add our public key executing:
    	sudo wget -O /etc/apt/trusted.gpg.d/biicode.gpg http://apt.biicode.com/keyring.gpg       
     
        # 3. Execute apt-get update:
        sudo apt-get update 
            
        # 4. Execute apt-get install: 
        sudo apt-get -y install biicode

        # 5. Execute bii setup:cpp to make sure you've got all tools required.
        bii setup:cpp
        

.. _alternative_install_archlinux:

Arch based distributions 
------------------------

**Alternative install for Archlinux based distributions (Manjaro, Arch Linux ARM, etc)**

Biicode maintains a package at the Arch User Repository (AUR). Install it using your preferred package manager:

.. code-block:: bash

    $ sudo yaourt -S biicode


The package is maintained in the AUR, so your package manager will notify you automatically when we update the package.

.. _alternative_install_source:

Run biicode from source
-----------------------

The most flexible way to make a package for your distro is running biicode from source. Also, if you are developing biicode, testing  new feature or helping to resolve a bug, you may need to run biicode directly from source. 

Follow this guide at GitHub to `run biicode from source <http://biicode.github.io/biicode/>`_. 

.. _cpp_installation:

Install C/C++ tools manually
--------------------------------

Install, set up and verify some **tools to build C and C++ projects with biicode**. 

Follow these steps if something failed during the automatic installation explained before. If you experience any issues, please `contact us at our forum <http://forum.biicode.com/category/client>`_, we'll try to solve your problem as soon as possible.

.. container:: tabs-section
     
    .. _cpp_desktop_linux:
    .. container:: tabs-item

        .. rst-class:: tabs-title
            
            Linux

        Install the required development tools as root:

        .. code-block:: bash

            $ sudo apt-get install build-essential cmake

        That's all!

    .. _cpp_desktop_mac:
    .. container:: tabs-item

        .. rst-class:: tabs-title
            
            MacOS

        You need to get installed both XCode Developer Tools and CMake:

        #. The XCode Developer Tools

           .. code-block:: bash

            $ xcode-select --install


        #. Download and install the appropriate `version of CMake <http://www.cmake.org/cmake/resources/software.html>`_ for your Mac OSX.

    .. _cpp_desktop_win:
    .. container:: tabs-item

        .. rst-class:: tabs-title

            Windows

        To develop C/C++ programs in Windows you need:

        - `CMake <http://www.cmake.org/>`_. Open Source tool that manages the software building process in a compiler-independent manner.

        - Compilers and build system. This could be one of the following (among other alternatives):

           - `MinGW <http://www.mingw.org/>`_ (make sure to include gcc, g++, and mingw32-make with your installation)
           - Visual Studio C++


        These are the **steps for manual installation** of our recommended tools:

        1. Download and install CMake. You can `download the latest version of CMake here <http://www.cmake.org/cmake/resources/software.html>`_.

        2. Download and install "base, g++" packages of MinGW. Follow `this link <http://sourceforge.net/projects/mingw/files/Installer/>`_ to get the installer, and choose while installing two additional packages, GCC and G++ package.

        3. Add to your user ``PATH`` environment variable the paths to these tools. We recommend `Rapid Environment Editor <http://www.rapidee.com/>`_ for editing environment variables. Otherwise, go to **My Computer**, click **Properties**, click **Advanced System Settings** and in the System Properties window click the **Environment Variables** button. then you will see a new window and in **User Variables** you'll find the variable ``PATH``:

           .. image:: /_static/img/cpp_windows_path.png

        Add your tools binaries folders (i.e. ``C:\MinGW\bin`` for MiGW, and ``C:\Program Files (x86)\CMake\bin`` for CMake).

        You might need to close and open again any ``cmd`` windows in order to load the new value for the ``PATH`` variable.


Verify your installation
^^^^^^^^^^^^^^^^^^^^^^^^^^^

To check your automatic installation open the Terminal and type **bii setup:cpp**. To check your manual installation, run the following commands. If the output messages look similar to these, the tools are successfully installed.

.. code-block:: bash

    $ cmake --version
    cmake version [version]

.. code-block:: bash
    
    $ gcc --version
    gcc (GCC) [version]
    ...

.. code-block:: bash
    
    $ g++ --version
    g++ (GCC) [version]
    ...
    
.. code-block:: bash
    
    $ mingw32-make --version
    GNU Make [version]
    ...


.. _proxy_configuration:

Connect through a proxy server
--------------------------------

Set an environment variable "HTTPS_PROXY" with your proxy server address.

**Linux/OSx**: 

.. code-block:: bash

	$ export HTTPS_PROXY="http://user:pass@proxy_ip:port"


.. container:: infonote

    You need to export this variable whenever you open a new shell. Append previous line on ~/.bashrc file and it will be executed when a shell is opened.

**Windows**:

	1. From the Desktop, right-click the very bottom left corner of the screen to get the Power User Task Menu.
	2. From the Power User Task Menu, click System.
	3. Click the Advanced System Settings link in the left column.
	4. In the System Properties window, click on the Advanced tab, and then click the Environment Variables button near the bottom of that tab.
	5. In the Environment Variables window, click "New" and add variable name HTTPS_PROXY and value "http://user:pass@proxy_ip:port"


**Example**: If my proxy is on localhost (port 7775) and my user is "lasote" with password "mypp":

.. code-block:: bash

	$ export HTTPS_PROXY="http://lasote:mypp@localhost:7775"



If you have any questions, we are available at |biicode_forum_link|. You can also |biicode_write_us| for suggestions and feedback.

.. |biicode_forum_link| raw:: html

   <a href="http://forum.biicode.com" target="_blank">biicode's forum</a>
 

.. |biicode_write_us| raw:: html

   <a href="mailto:support@biicode.com" target="_blank">write us</a>
