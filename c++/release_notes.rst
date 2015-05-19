.. _release_notes:

Release notes
=============

**3.2** (19-May-2015)

        * Fixed problem with cmake Eclipse generator overwriting every time the project config
        * Dependencies are managed as SYSTEM for include_directories, to avoid compilation warnings, both for absolute and relative includes
        * Opt-out for handling include_directories as system dependencies
        * Fixed bug in migration of old .bii files
        * Fixed bug in publish not upgrading properly user profiles


**3.1.1** (29-Apr-2015)

        * Optimized complete internal workflow, avoiding slow and unnecessary serializations to project DB
        * Files not modified in disk, removed problems with CRLF conversions 
        * Fixed behavior of "bii test" in XCode: https://github.com/biicode/client/issues/12
        
        
**3.0** (15-Apr-2015)

        * Open source release of client and common repositories, dev infraestructure re-made
        * Release of premium accounts for private blocks
        * Enabled OAuth with Github and Google
        * Fixed bug in C++ parser for `using` statements
        * Fixed bug in [tests] pattern that incorrectly affected dependencies
        * New Terms of Service, clarifying source code licenses and accounting for premium accounts and open source contributions
        * Fixed bug in user folder ".biicode" path, some config files were stored out of it

 
**2.8** (7-Apr-2015)

	* Better computation of binary targets, if an executable does not depend on its own block library, it will not be linked
	* Removed automatic creation of cmake_dummy.cpp to avoid problems with header only libraries
	* Removed automatic handling of system deps (math, pthread, winsock), that created problems in new toolchains. Now users directly specify in CMakeLists their libs.
	* ADD_BIICODE_TARGETS() has been superseded by ADD_BII_TARGETS(), which will admit a biicode version number, this is done to achieve backwards compatibility while introducing new build behavior.
	* Fixed bug of include paths missing in [tests] targets
	* Fixed extra verbose message of warning about full path #includes
	* Optimized performance of ignore.bii for large number of patterns, that was incredibly slow
	* Now published blocks show publisher's user name
	* Security fixes
	
	
**2.7** (23-Mar-2015)

	* New [tests] section improved, working fine in Visual Studio
	* "bii test" now allows parameters (-jN for parallel builds/runs, and CTest other parameters -R -E -C Debug, etc)
	* Simpler "policies.bii" configuration, old ones will be automatically migrated
	* Now "bii find" works also with [includes], so it is not necessary to fill both the [includes] and the [requirements]
	* Search in web for file names with the "file:" label inside the search box
	* Issue warning when using absolute #include paths within the current block, as this wouldn't work in simple layouts
	* Fixed bug with "bii publish -r" in simple layout
	* Renamed custom target "check" associated with "bii test" to "biitest", as the check target might collide with user ones
	
	
**2.6.1** (11-Mar-2015)

	* New [tests] section in biicode.conf. Automatically define your tests, and build and run them with "bii test"
	* New simplified alias "bii build", "bii configure", "bii test" for "bii cpp:xxx" commands
	* New "bii buzz" command. It "bii init -L" + "bii find" + "bii build" for quick getting started for newbies, or after a git clone
	* New project layout fixes, the default block at root is named after its biicode.conf [parents] if existing
	* Added layout variables to CMakeLists.txt, so cmake can account for variable layouts. Also added CMake variable to indicate a block is a dependency or not.
	* Added layout variables to hooks (bii.paths.deps, bii.paths.bin, etc)
	* New command options for arduino:settings (--board=uno, --port=auto, etc), so interactive mode can be avoided. Same for rpi:settings
	* Automatic handling of PATH, sh.exe is removed from mingw builds, as cmake-mingw builds doesnt work well with it in the path
	* Updated supported arduino SDKs to 1.6
	* New --hello=c (<stdio>, printf) for pure C projects
	* Fixed broken Eclipse project generation
	* Fixed changing [requirements] when several blocks are simultaneously opened
	* Fixed incorrect warning about bad filenames of files which were in ignore.bii
	
	
**2.5.2** (3-Mar-2015)

	* New custom project layouts available, with layouts.bii. 
	* Enabled edition in the project root folder
	* Fixed problems with paths with spaces
	* Changed arduino toolchains, now use cpp:configure -t=arduino, and cpp:build
	* Fixes to windows installer, shortcuts load biicode path even if not in system path
	* Free accounts have collaborators now too
	* Fix in noderunner script


**2.4.1** (18-Feb-2015)

	* Improved windows installer, more user options for path, icons, uninstaller, and fixed readme.txt linefeeds
	* Improved cmake installation, with option --interactive "$bii setup:cpp -i", now not adding it to path, so can coexist with 2.8 installs
	* Recovered colored output of cmake builds
	* Enabled blocks linked with symlinks in linux, so 2 different projects can link to the same block
        * Fixed problem of cached badges
        * Fixed biicode.cmake issues for CLion, now CLion can be used with biicode
	

**2.3** (9-Feb-2015)

	* Better toolchain system for cross-compiling
	* Added --remote option to "bii publish" to publish github, bitbucket etc remotes info (remote, branch, tag and commit).
	* Web: Block view with visible VCS remote information.

**2.2** (27-Jan-2015)

	* Fixed errors with local cache and DEV version updates.
	* Web: New biicode badges.

**2.1.1** (12-Jan-2015)

	* Fixed problem with biicode.conf [includes] of the form  block/file.h: username
	* Arduino automatic reset for certain boards, those using the "catarina" uploader (leonardo, yun)
	* bii open better handling of versions and tracks
	* upgraded cmake minimum required version to 3.0
	* fixed security issue of token not discarded after changing password
	* improved error messages when biicode.conf incorrect
	* Website: Better block page header, reuses in Block requirements.

**2.0.1** (17-Dic-2014)

	* Premium accounts to store code privately and share alike. 
	* New and simpler configuration in a single “biicode.conf” file, instead of several tiny files, and with more flexibility.
	* System for reusing CMake scripts. Now, CMakeLists.txt can automatically depend on existing CMake scripts, they will be automatically retrieved, versioned, shared, exactly as other source code files
	* Improved and simpler, CMake and build system, with Interface targets. Possibility of setting options to and configuring blocks you depend on. 
	* Possible to specify #include mappings to blocks, so no modification at all is necessary in code.
	* Support for Arduino 1.5 for Yun board 
	* Python hooks for custom tasks. Examples of hooks that automatically retrieve and configure system-wide some popular and large frameworks as OpenCV or Boost.
	* Blocks can use different variants, called “tracks” to choose and switch between lib versions or flavours. For example, can be used to maintain several development branches simultaneously as lasote/libuv(v1.0) and lasote/libuv(v0.10), and changing from one to the other does not require any change to code.
	* Web: See which blocks depend on your block in the requirements tab 
	* Binary support to WXwidgets
	* New doc style and contents

**1.11** (19-Nov-2014)

	* Block tracks.
	* Client hooks.
	* Improved client output messages.
	* Faster processing of large projects.
	* Improved setups (arduino).
	* Bug of with Publish STABLE after DEV cache invalidating solved.
	* Bug of target_compile_options quotes solved.
	* Web: Block permissions and admin management for premium accounts (for friends).
	* Web: `Improved Search Engine: by tag, user name, block name... <http://blog.biicode.com/improved-search-engine-elastic-search/>`_
	* Web: Block tagging.
	* Web: Fixed bug with some passwords patterns.

**1.10.1** (3-Nov-2014)

	* Create blocks on web interface
	* Lowercase on usernames and blocknames restriction removed
	* Removed branches functionality
	* Fixed RAW code for images
	* Fixed ZIP download for images

**1.9** (20-Oct-2014)

	* Support any Arduino compatible board
	* Improved information messages
	* CMake now defines BIICODE to support biicode and non biicode includes
	* Web: Show achievements in user profile
	* Web: Raw file visualization

**1.8.5** (10-Oct-2014)

	* Fedora and Arch package
	* CMake updated to 3.0.2 and improved setup:cpp command
	* Fixed errors with ignore.bii behaviour
	* Custom tool-chain for CMake
	* Web: Download blocks as ZIP
	* Web: Delete blocks

**1.7.3** (24-Sept-2014)

	* Solved bug in merge.
	* dependencies.bii now accepts file patterns.
	* New apt server for debian based distributions including wheezy.
	* Better and cleaner deb packaging for debian based distributions.

**1.6** (16-Sept-2014)

	* Solved bug in cpp parser
	* Added a new filter with patterns in mains.bii file

**1.5.4** (09-Sept-2014)

	* Deleted "bii status" command
	* Largely improved "bii diff" command
	* Solved some bugs with CMake
	* biicode is now case sensitive

**1.4.1** (04-Sept-2014)

	* Minimum CMake version updated to 2.8.12 (it was 2.8, but 2.8.12 was indeed required)
	* Added -p (--password) option to "bii user" so biicode can be scripted (e.g. travis-ci) without interactivity
	* Largely improved "bii deps" command
	* New structure and data of "xxx_vars.cmake" files, allowing choosing to build or not in block library (both static and shared), with better embedded comment string docs
	* CMake printing of built targets
	* CMake path inserted for upgrades to cmake 3.0 in bii setup:cpp
	* Files in web user profile ordered alphabetically
	* Bug of web navigation back-forth solved

**1.3.3** (21-08-2014)

	* Bugfix: colored output

**1.3.2 (13-08-2014)**

	* Bugfix: login not required anymore when not really needed
	* Web performance improvements  

**1.2.1 (07-08-2014)**

	* Bugfix for recursive system dependencies compilation

**1.2 (06-08-2014)**

	* Bugfix Open command computed deps incorrectly
	* Bugfix Incorrect find policies for DEV versions
	* Bugfix Solved transitivity problems in cmake for complex deps
	* Rpi cmake pre-built custom package
	* UX Improvements
	* Web fixes:
	* Files tree alphabetically ordered
	* Show pictures in blocks
	* Fixed log in and password recovery

**1.1.1 (25-07-2014)**

	* Bugfixes
	* UX Improvements
	* Web Bugfixes, dependencies and deps graph

**1.0.4 (25-07-2014)**

	* Bugfixes
	* UX Improvements

**1.0.1 (15-07-2014)**

	* No sign up required
	* No more workspaces, any folder can hold a project
	* Plain configuration files
	* Simplified project settings
	* Relative includes allowed
	* Configuration options with CMake (extensible)
	* Bugfixes
	* Improved web-page

**0.17.3 (28-06-2014)**

	* Bugfixes in arduino build (bad transitive dependencies)
	* Bugfixes in Raspberry Pi commands
	* Reduced Arduino.cmake and CMakelists.txt for arduino projects
	* Bugfixes in deps command

**0.16 (24-04-2014)**

	* Improved project graph visualization
	* Bugfixes in publish command

**0.15.3 (11-04-14)**

	* Now work, find and upload can be done from arduino monitor GUI
	* Output information improvements
	* Auto remove empty dep folders
	* Arduino selection improvements, now you can select among different connected devices
	* Improved readme.md layout
	* Relative imports within the same block allowed

**0.14.1 (03-04-14)**

	* Fixed Ubuntu 64b installation issues
	* Arduino serial monitor (GUI) improvements
	* Bugfixes
	* Node integration improvement
	* Improved block deletion support

**0.13.1 (28-03-14)**

	* Bugfixes in arduino build
	* Now you can upload to the arduino from the serial monitor
	* Better Node.js support
	* ``bii clean`` command now deletes the build folder
	* Removed main and class creation wizards
	* Removed ``bii cpp:exe`` command
	* Projects and Blocks can now be deleted from your user profile web page

**0.12 (21-03-14)**

	* Allow to define MS Visual version from cpp:settings
	* Arduino bugfixes
	* Git support improvements

**0.11.1 (14-03-14)**

	* New installation wizards for C++, Arduino, and Raspberry Pi
	* Arduino port automatic detection. The ``bii arduino:usb`` command is deprecated
	* Removed ``environment.bii`` config file
	* Add direct access icon for Windows biicode client
	* Fix find bug
	* Fix local cache bug
	* Nicer ``bii arduino:monitor`` in MacOS
	* Removed ``--default`` option in ``bii init`` and ``bii new``. New parameters for ``bii new`` command.
	* Enry points automatic detection in files with ``setup`` and ``loop`` functions
	* Adding ``import`` as valid preprocessor directive.

**0.10 (21-02-14)**

	* Removed the workspace ``default_settings.bii`` file. Now, new projects' settings are obtained from the workspace ``environment.bii`` file.
	* Node.js support
	* Debian wheezy support
	* Fix a bug that caused open to fail if the block was already in edition

**0.09 (13-02-14)**

	* There is a brand new visualization in browser of projects and dependencies with "$bii deps --graph"
	* minor bugfixes
	* improved :ref:`open command<bii_open_command>`, now any block can be open inside a project
	* improved performance of finds in server and connections pools
	* setup totally new. Only setup:cpp working now experimentaly. Also rpi:setup moved to setup:rpi
	* apt-get repository for debian based (ubuntu, raspbian) distributions
	* new "bii info" command

**0.08 (5-Feb-14)**

	* Merge bugfixes
	* Project download bugfixes
	* Size and performance optimizations in macos and linux clients

**0.07.2 (31-Jan-14)**

	* Merge bugfixes
	* Various bugfixes
	* Deps output improved

**0.06.2 (28-Jan-14)**

	* Added :ref:`arduino support <arduino>`
	* Created raspbian native client
	* Improved python native libraries
	* Improved virtual cells management
	* :ref:`Policies <policies>` made easier and now  user find their own DEV (in master branches) versions by default
	* Bugfixes
	* Added new tagging system comments_tags.
	* Added cpp:exe command that allows executing an already compiled binary w/o recompiling
	* Improved renaming support
	* Adding OpenGL ES for RPI project generation
	* Improved cpp wizard

**0.05 (10-Jan-14)**

	* Raspberry now using rsync instead of scp
	* Wizard rpi:setup for automatic install of cross compilers
	* New breadcrumb navigation bar for blocks in browser
	* Reduced computation by an order of magnitude, especially noticeable in large projects
	* Fixed bugs in parsers, that kept old state even the file was modified
	* Improved normalization of endlines, for handling also \\r
	* Fixed bug of not finding new dependencies of files in already dependents blocks

**0.04 (20-Dec-13)**

	* Improved wizards behavior
	* Added cookies announcement in web as dictated by law

**0.03.4 (17-Dec-13)**

	* Init and new configuration wizards
	* Improved Eclipse support. You can read about it :ref:`here <ide_eclipse>`
	* Improved Raspberry Pi support.
	* Changed project structure. It's now easier.
	* User can edit cmakes.

**0.02.3 (2-Dec-13)**

	* Experimental upload-download of projects to biicode, so it is not necessary to publish to keep working in other computer.
	* Navigation of uploaded projects in the web
	* Updated exe creation to pyinstaller2.1, as 2.0 had some problems in some windows installs.
	* Creation (experimental) of dynamic libraries from C code. Integration from python code with cffi.
	* Improved use of biicode for C/C++ dev with RaspberryPI (linux only)

**0.01.11 (28-Oct-13)**

	* Fixed bug in Eclipse Cmake generated project with empty targets
	* Fixed bug that failed when trying to reuse just a data file from another published block (not reusing sources)
	* Fixed bug of virtual cells in fortran, due to the "include" does not require to build source file
	* Improved NMake support, launching vcvarsall in a .bat file to include environment variables
	* Web loads much improved, loading of files with Ajax, rendering of color syntax highlighting with JS, client side and paginated to handle large files
	* Web styles improvements, back and forward buttons
	* Solved bug of project with multiple src blocks, that was overwriting references to dep blocks
	* WxWidgets binary support improved
	* Improved handling of python imports, solved bug that didnt renamed properly to absolute imports
	* Ctrl+C when init bug fixed (it created empty, wrong workspace)
	* Applied some limits and constraints to block sizes, file sizes, number of files in a block and in a project

**0.01.10.1**

	* Fixed bug of crash when dep folder had connected cpp_rules files

**0.01.10**

	* Setup & install in windows problem with setting PATH of biicode solved
	* Defined C++0x as default, with possibility of changing it in settings
	* Changed "find" command, now with parameters "update", "downgrade", "modify"
	* Block referencing in client changed from full "owner/creator/block/branch" to "creator/block (owner/branch)"
	* Improved setup tools, mainly  setup:cpp and setup:node, they update the Environment.bii
	* Improved cpp:wizard to create classes and mains
	* "dependencies.bii" now able to add, remove and redefine dependencies manually
	* SyntaxHighligher done in browser instead of server to avoid timeouts while browsing large code files
	* Solved some bugs in renaming files
	* Transitive propagation of cpp_rules from libraries to executables requiring those libraries.
	* Solved bugs for user login camelcase
	* checkout --deps --force flow improved
	* Use system proxy

**0.01.9**

	* Added check of client version, so clients are informed about new releases and deprecated versions, with a download URL
	* bii deps --detail command improved showing data dependencies and type of file
	* Solved bugs in virtual resources that didn't let reuse published virtual resources
	* cpp_rules files now can accept multiple statements per rule as well as rules without condition and else clauses
	* Improved merge, but still very experimental
	* Solved bug that allowed to "find" dependencies with cycles to own project blocks
	* bii deps --graph now working, showing project block graph in browser
	* Fixed problem with renaming files.
	* Solved bug with user login upper-lower case mismatch
	* Improved possibility of editing directly in dep folder, but still discouraged practice.
	* Improved detection of implicit implementations in CPP with static class variables.
	* Added preliminary support for fortran, and improved java and node; still experimental languages
	* Changed folders in node, now using NODE_PATH variable so they dont have to be named node_modules
