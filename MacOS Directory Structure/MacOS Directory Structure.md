In macOS, there are some standard directories, which can be in one of the user, local, system, or network domains. There are also some standard unix/posix directories.

This article will start by explaining what is the user, local, system, and network domain. After that, it will explain the standard directories, that belongs to these domains. Next it will explain the unix/posix directories. Finally it will elucidate, the other macos directories.

![what is the user , local , system network domains ? what are the standard folders ? what are the posix / unix like folders ?](https://difyel.com/assets/articles/macos-directory-structure-apple-macos/img/macos-directory-structure-tutorial-279-216.png)

Table of contents[What are the user, local, system, and network domains?](https://difyel.com/apple/macos/macos-directory-structure/#What_are_the_user_local_system_and_network_domain "What are the user , local , system and network domain ?")[Standard folders](https://difyel.com/apple/macos/macos-directory-structure/#Standard_folders "Standard folders")[Applications](https://difyel.com/apple/macos/macos-directory-structure/#Applications "Applications")[Library](https://difyel.com/apple/macos/macos-directory-structure/#Library "Library")[Application Support](https://difyel.com/apple/macos/macos-directory-structure/#Application_Support "Application Support")[Caches](https://difyel.com/apple/macos/macos-directory-structure/#Caches "Caches")[Frameworks](https://difyel.com/apple/macos/macos-directory-structure/#Frameworks "Frameworks")[Preferences](https://difyel.com/apple/macos/macos-directory-structure/#Preferences "Preferences")[Network](https://difyel.com/apple/macos/macos-directory-structure/#Network "Network")[System](https://difyel.com/apple/macos/macos-directory-structure/#System "System")[Users](https://difyel.com/apple/macos/macos-directory-structure/#Users "Users")[Posix or Unix directories](https://difyel.com/apple/macos/macos-directory-structure/#Posix_or_unix_directories "Posix or unix directories")[Other directories](https://difyel.com/apple/macos/macos-directory-structure/#Other_directories "Other directories")

## [1- What are the user, local, system, and network domains?](https://difyel.com/apple/macos/macos-directory-structure/#toc_What_are_the_user_local_system_and_network_domain)

In macOs, there are some standard folders, these standard folders can be in one or multiple domains. The domains that a folder can be in are the:

-   user domain
-   local domain
-   system domain
-   network domain

The user domain, is the user directory, it contains files and applications and resources, which are related to a given user. This folder is located under the `/Users/username`, and it contains multiple folders, such as the `Applications` folder, the `Library` folder, the `Movies` folder. A user can make changes to his files. The user directory can also be placed on the network.

The local domain is the domain which is related to the current computer, as such it contains applications, files, and resources, related to to the current computer, and shared among the users. The local domain contains multiple folders, and an administrator, can make changes to these folders and files.

1.  # examples of folders in
2.  # the local domain.
3.  /Applications
4.  /Library
5.  ..

The system domain, contains resource files, and applications, which are related to the system , and which are installed by apple. The `/System` directory, placed under the root directory `/`, is part of the system domain.

The network domain, are the applications, files and resources, which are located on a network, and shared by the users of a network.

## [2- Standard folders](https://difyel.com/apple/macos/macos-directory-structure/#toc_Standard_folders)

### [2.1- Applications](https://difyel.com/apple/macos/macos-directory-structure/#toc_Applications)

There are multiple Applications folders, and they can be located under multiple domains.

The Applications folder that belongs to the local domain, is placed under the root directory `/Applications`. It contains the applications that will be used by all the users. These applications can be installed by using apple store, or by dragging and dropping an application into the application folder. Applications under the `/Applications` folder, will appear under the launchpad. An example of an application in the local domain is: pages…

The Applications folder, that belong to the user domain, is placed under `/Users/username/Applications`, and it contains applications related to the user .

The Applications folder, that belong to the system domain, is placed under `/System/Applications`, and it contains applications installed by Apple. Applications under the `/System/Applications` folder, will appear under the launchpad. Examples of such applications, are the App Store, or Automator…

1.  macBook:/System/Applications$ ls
2.  # Applications under the /System/Applications folder
3.  App Store.app          Image Capture.app      Preview.app
4.  Automator.app          Launchpad.app          QuickTime Player.app
5.  Books.app              Mail.app               Reminders.app
6.  Calculator.app         Maps.app               Siri.app
7.  Calendar.app           Messages.app           Stickies.app
8.  Chess.app              Mission Control.app    Stocks.app
9.  Contacts.app           Music.app              System Preferences.app
10.  Dictionary.app         News.app               TV.app
11.  FaceTime.app           Notes.app              TextEdit.app
12.  FindMy.app             Photo Booth.app        Time Machine.app
13.  Font Book.app          Photos.app             Utilities
14.  Home.app               Podcasts.app           VoiceMemos.app

### [2.2- Library](https://difyel.com/apple/macos/macos-directory-structure/#toc_Library)

A library is a collection of information, which is kept to be used. In macOs there are multiple library folders, and each of them belong to a different domain. A Library folder can contain cache files, resources, configurations, preferences… related to an application.

In the user domain, the Library folder is used to store informations, about the applications related to the current user. It is located under the user directory: `/Users/username/Library` .

1.  macBook:/Users/username/Library$ ls
2.  # Library folder in the user domain
3.  # /Users/username/Library
4.  Accounts                Keychains
5.  Application Scripts     LaunchAgents
6.  Application Support     Logs
7.  ColorPickers            PersonalizationPortrait
8.  Colors                  Personas
9.  Containers              PreferencePanes
10.  Fonts                   Sounds
11.  FrontBoard              Spelling
12.  ...
13.  ...
14.  .

In the local domain, the Library folder is located under the root directory `/Library`, and it contains informations related to an application(s), and shared by all the users of this application(s).

1.  macBook:/Library$ ls
2.  # Library folder in the local domain
3.  # /Library
4.  ColorPickers          Java                  Ruby
5.  Components            Keychains             Fonts
6.  Frameworks            Preferences           Python
7.  ...
8.  ....
9.  .

In the system domain, the Library folder is located under `/System/Library`. This folder is used by macOS, and it will contains files and resources, related to system applications.

1.  macBook:/System$ ls Library/
2.  # Library folder under the system domain
3.  # /System/Library
4.  AWD                     Filesystems             PreferencePanes
5.  Accessibility           Filters                 Preferences
6.  ..
7.  .

The Library folder, contains some subfolders, that can be used by all the installed applications, and they are:

-   `Library/Application Support`
-   `Library/Caches`
-   `Library/Frameworks`
-   `Library/Preferences`

#### [2.2.1- Application Support](https://difyel.com/apple/macos/macos-directory-structure/#toc_Application_Support)

The Application Support folder, contains files to support the application. Applications can place inside this folder, their data and configuration files, in multiple domains.

If the Application Support folder, is located under the local domain `/Library/Application Support`, it will contain files related to all the users. If it is within the user domain `/Users/username/Library/Application Support`, it will only contain files related to the current user. For example, the `App Store` application, contains support files in the local domain , and in the user domain .

1.  macBook:/Library/Application Support/App Store$ ls
2.  # /Library/Application Support/App Store
3.  # files in the local domain,
4.  adoption.plist

6.  macBook:/Users/username/Library/Application Support/App Store$ ls
7.  # /Users/username/Library/Application Support/App Store
8.  # files in the user domain.
9.  StoreKit.db         updatejournal.plist

#### [2.2.2- Caches](https://difyel.com/apple/macos/macos-directory-structure/#toc_Caches)

Used for caching by an application. An application can recreate the content which is stored inside this folder, and this folder can belong to multiple domains. For example, an application can use the Caches folder, to download its update files.

1.  macBook:~/Library/Caches/com.apple.iTunes$ ls
2.  # ~ stands for the user home directory
3.  # # /Users/username/Library/Caches/com.apple.iTunes
4.  # files under user domain.
5.  CommerceRequestCache

#### [2.2.3- Frameworks](https://difyel.com/apple/macos/macos-directory-structure/#toc_Frameworks)

A framework, is the frame under which an application can work. As such the Frameworks directory, contains the libraries that are used, or needed, to create an application. The Frameworks directory, can belong to multiple domain. Under the system domain, the Frameworks directory contains the frameworks, needed to create an application.

1.  macBook:/System/Library/Frameworks$ ls
2.  # Frameworks folder under the system
3.  # domain

5.  AVFoundation.framework            ImageIO.framework
6.  AVKit.framework                   InputMethodKit.framework
7.  Cocoa.framework                   MetalKit.framework
8.  ColorSync.framework               ModelIO.framework
9.  Contacts.framework                MultipeerConnectivity.framework
10.  ContactsUI.framework              NaturalLanguage.framework
11.  CoreAudio.framework               NetFS.framework
12.  CoreAudioKit.framework            Network.framework
13.  CoreML.framework                  PhotosUI.framework
14.  ...

Under the local domain , the Frameworks directory, contains frameworks needed to interact with a local application.

1.  macBook:/Library/Frameworks$ ls
2.  # Frameworks folder under the local
3.  # domain
4.  iTunesLibrary.framework
5.  ...
6.  ..

#### [2.2.4- Preferences](https://difyel.com/apple/macos/macos-directory-structure/#toc_Preferences)

The Preferences folder contains the application preferences, it can belong to multiple domains. If it is in the local domain, it is the preferences of the application for all users. If it is in the user domain, it is the user preferences for a given application. If it is in the system domain, it contains preferences for applications in the system domain.

1.  macBook:/Library/Preferences$ ls
2.  # Preferences folder in the local
3.  # domain
4.  com.apple.PowerManagement.plist
5.  com.apple.SoftwareUpdate.plist
6.  com.apple.TimeMachine.plist
7.  com.apple.commerce.plist
8.  com.apple.dock.plist
9.  com.apple.driver.AppleIRController.plist
10.  com.apple.dt.Xcode.plist
11.  com.apple.security.plist

14.  macBook:/System/Library/Preferences$ ls
15.  # Preferences folder in the system
16.  # domain
17.  Calendar              Logging               ProtectedCloudStorage

### [2.3- Network](https://difyel.com/apple/macos/macos-directory-structure/#toc_Network)

The `/Network` folder, contains files and resources, which belong to the network domain. As such it can contain a list of computers, that are on the local network, and which files and ressources can be accessed.

### [2.4- System](https://difyel.com/apple/macos/macos-directory-structure/#toc_System)

The `/System` folder, contains files and resources, which belong to the system domain, these files are installed by apple, and they shouldn't be modified.

1.  macBook:/System$ tree -L 1
2.  # List only the top level 
3.  # directories in the /System 
4.  # folder
5.  .
6.  |-- Applications
7.  |-- DriverKit
8.  |-- Library
9.  |-- Volumes
10.  |-- iOSSupport

### [2.5- Users](https://difyel.com/apple/macos/macos-directory-structure/#toc_Users)

The `/Users` folder, belongs to the user domain, as such it contains user related applications, files and resources. Each user has its own user folder, which is located under `/Users/username`, and the user user folder, is formed of many standard subfolders, which are:

-   `/Users/username/Applications`: contains user installed applications. A user can install applications under the user domain `~/Applications` folder, or under the local domain `/Applications` folder. Those that are installed under the local domain `/Applications` folder, are shared between the users, and those that are installed in the user directory `~/Applications` folder, are user related applications.
-   `/Users/username/Desktop`: contains items located on the user's Desktop. The desktop is the first screen that the user sees, when he logs into his computer.
-   `/Users/username/Documents`: contains files created by the user.
-   `Users/username/Downloads`: contains user files, that are downloaded from the internet.
-   `/Users/username/Library` : The Library folder contains information to be used by an application, such as its data files, its configurations, its ressources and preferences. A Library folder can be in the user domain, or in the local domain, or in the system domain. If it is in the user domain, it contains application information related to the current user, if it is in the local domain, it contains application information related to all users.
-   `/Users/username/Movies`: contains video files, related to the current user.
-   `/Users/username/Music`: contains music files, related to the current user.
-   `Users/username/Pictures`: contains user picture files .
-   `/Users/username/Public`: contains files and folders, that a user wants to share, with other users on the same machine, or on the network.

## [3- Posix or Unix directories](https://difyel.com/apple/macos/macos-directory-structure/#toc_Posix_or_unix_directories)

MacOs also has some unix directories, these directories are:

`/bin`: This directory contains unix like user commands or utilities, such as ls, which is used to get the list of files and directories.

1.  macBook:/bin$ ls
2.  # The /bin directory contains user commands
3.  [         date      hostname  ls        rm        tcsh
4.  bash      dd        kill      mkdir     rmdir     test
5.  cat       df        ksh       mv        sh        unlink
6.  chmod     echo      launchctl pax       sleep     wait4path
7.  cp        ed        link      ps        stty      zsh
8.  csh       expr      ln        pwd       sync

`/dev`: contains some unix like device files, which allow a user, to interact with a device, like he is interacting with a file.

1.  macBook:/dev$ ls
2.  # device files, also known
3.  # as special files.
4.  HAX                        disk1                      rdisk0
5.  afsc_type5                 disk1s1                    rdisk0s1
6.  auditpipe                  disk1s2                    rdisk0s2
7.  auditsessions              disk1s3                    rdisk1
8.  autofs                     disk1s4                    rdisk1s1
9.  autofs_control             dtrace                     rdisk1s2
10.  autofs_homedirmounter      dtracehelper               rdisk1s3
11.  autofs_notrigger           fbt                        rdisk1s4
12.  autofs_nowait              fsevents                   sdt
13.  bpf0                       io8log                     stderr
14.  bpf1                       io8logmt                   stdin
15.  bpf2                       io8logtemp                 stdout
16.  bpf3                       klog                       systrace
17.  bpf4                       lockstat                   urandom
18.  console                    machtrace                  vboxdrv
19.  cu.Bluetooth-Incoming-Port null                       vboxdrvu
20.  disk0                      oslog                      vboxnetctl
21.  disk0s1                    oslog_stream               xcpm
22.  disk0s2                    random

`/etc`: This folder contains configurations files, for unix applications, for example passwd or groups…

1.  macBook:/etc$ ls
2.  # configuration files for unix/posix application

4.  apache2                               ntp.conf
5.  auto_home                             passwd
6.  auto_master                           paths
7.  autofs.conf                           paths.d
8.  bashrc                                periodic
9.  csh.cshrc                             php-fpm.conf.default
10.  csh.login                             php-fpm.d
11.  csh.logout                            php.ini.default
12.  hosts                                 rpc
13.  mach_init.d                           ssl
14.  mach_init_per_login_session.d         sudo_lecture
15.  mach_init_per_user.d                  sudoers
16.  mail.rc                               sudoers.d
17.  man.conf                              syslog.conf
18.  manpaths                              ttys
19.  manpaths.d                            vpns1.2.4.1
20.  ...
21.  ..

`/sbin`: contains unix utilities and commands, used by system administrators, like for example commands used for networking, or for the filesystem.

1.  macBook:/sbin$ ls
2.  # The /sbin folder contains
3.  # system commands and utilities

5.  autodiskmount    disklabel        dmesg            halt
6.  nologin          mount_hfs        ping             fsck
7.  ping6            md5              reboot           route
8.  shutdown         umount
9.  ...
10.  ..

`/tmp`: contains temporary files and folders, created by applications and the system, these temporary files can be deleted .

`/usr`: this directory contains commands, utilities, libraries and shared resources, which are not essential for the system.

1.  macBook:/usr$ ls
2.  # The /usr directory content
3.  bin        libexec    sbin       standalone
4.  lib        local      share
5.  ..
6.  .

`/var`: contains data, which content and size might change, such as log files.

1.  @MacBook:/var$ ls
2.  # The /var directory content
3.  mail     log      msgs
4.  ...
5.  ..

`/opt`: contains optional commands, binaries, libraries and ressources, which are not part of a unix distribution.

## [4- Other directories](https://difyel.com/apple/macos/macos-directory-structure/#toc_Other_directories)

`/Volumes`: This is where all the volumes are mounted, for example the hard drive is found in here.

1.  macBook:/Volumes$ tree -dlL 2
2.  # print directories tree in Volumes
3.  # -d : show only the directories
4.  # l : follow symbolic links
5.  # L 2 : show only level one and
6.  #       level two directories

8.  .
9.  |-- Macintosh\ HD -> /
10.      |-- Applications
11.      |-- Library
12.      |-- Network
13.      |-- System
14.      |-- Users
15.      |-- Volumes
16.      |-- bin
17.      |-- cores
18.      |-- dev
19.      |-- etc -> private/etc
20.      |-- home
21.      |-- net
22.      |-- opt
23.      |-- private
24.      |-- sbin
25.      |-- tmp -> private/tmp
26.      |-- usr
27.      |-- var -> private/var

`/cores`: contains core dumps, as in when an application has crashed.

`/private`: this is a folder which contains the etc, tmp and var folders, described earlier. `/etc`, `/tmp` and `/var`, are symbolic links to folders inside this directory.