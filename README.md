-   [Justin James](https://digitaldrummerj.me/) {.show-for-small-only}
    ===========================================

-   [Navigation](https://digitaldrummerj.me/#)

-   [Home](https://digitaldrummerj.me/)
-   [Speaking Engagements](https://digitaldrummerj.me/speaking/)
-   [Blog](https://digitaldrummerj.me/blog/)
-   [Workshops](https://digitaldrummerj.me/workshops/)
    -   ##### [Back](javascript:void(0))

    -   [Workshops](https://digitaldrummerj.me/workshops/)
    -   [Workshops](https://digitaldrummerj.me/workshops/)
    -   [Rapid API Development with
        SailsJS](https://digitaldrummerj.github.io/sails-tutorial)
    -   [Up and Running with
        Angular](https://digitaldrummerj.github.io/angular-tutorial)

-   [About](https://digitaldrummerj.me/about/)
-   [Contact](https://digitaldrummerj.me/contact/)
-   [Search](https://digitaldrummerj.me/search/)

[![Justin
James](./Justin%20James_files/logo.png)](https://digitaldrummerj.me/ "Justin James")

Ionic - How to setup on Windows
===============================

Sun Jan 11, 2015 [ionic](https://digitaldrummerj.me/categories/ionic)

Updates:

-   2016-08-13: Added Gradle and VS Code to software installed. Changed
    from JDK7 to JDK8. Removed Ant. Added Android SDK Apis install to
    Chocolatey script. Switched suggested emulator to Visual Studio
    Emulator for Android.

If you are like me and just starting to work with the [Ionic
Framework](http://www.ionicframework.com/) and don’t already have a
machine setup to do Android, iOS, Node, etc development then many of the
guides out there leave out a number of steps that you need to do in
order to get everything working.

It is really easy to get everything working though once you know the
steps. Since I am a Windows user and love to automate work that is
easily repeatable, I used [Chocolatey](http://www.chocolatey.org/) and
[Boxstarter](http://www.boxstarter.org/) to automate the setup for the
Ionic Framework.

On Windows, you will only be able to setup Android development. Apple
requires a Mac in order to do iOS development.

Software to be installed
------------------------

-   [NodeJS](https://chocolatey.org/packages/nodejs.install)
-   [Git](https://chocolatey.org/packages/git)
-   [Gradle](https://chocolatey.org/packages/gradle)
-   [JDK8](https://chocolatey.org/packages/jdk8)
-   [Android SDK](https://chocolatey.org/packages/android-sdk)
-   [Android Studio](https://chocolatey.org/packages/AndroidStudio)
-   [Google Chrome](https://chocolatey.org/packages/GoogleChrome)
-   Npm Modules:
    -   [cordova](https://www.npmjs.com/package/cordova)
    -   [gulp cli](https://www.npmjs.com/package/gulp-cli)
    -   [bower](https://www.npmjs.com/package/bower)
    -   [ionic](https://www.npmjs.com/package/ionic)
-   [Visual Studio Emulator for Android (Hyper-V
    Based)](https://www.visualstudio.com/en-us/features/msft-android-emulator-vs.aspx)
-   [VS Code](https://code.visualstudio.com/)

How to install software
-----------------------

1.  Install Chocolatey from
    [http://www.chocolatey.org](http://www.chocolatey.org/). Command is
    on the front-page of the site or below. Open an administrative
    command prompt to run the command. To open an administrative command
    prompt on Windows 8, go to the start menu, type cmd and then
    ctrl+shift+click on the cmd search result.

         Command Prompt: @powershell -NoProfile -ExecutionPolicy unrestricted -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin

2.  Install the [BoxStarter](http://boxstarter.org/) Chocolatey package

         choco install -y BoxStarter

3.  Close the command prompt that you opened to install Chocolatey and
    BoxStarter

4.  On the desktop there should be a BoxStarter Shell icon, double-click
    on that to run it. If the icon is not on the desktop, then open up a
    command prompt and type BoxStarterShell.

5.  I have setup a gist file that has all of the Chocolatey commands to
    run to install the rest of the software and configure it. Run the
    gist file from the Boxstarter Shell:

         Install-BoxStarterPackage -PackageName  https://gist.githubusercontent.com/digitaldrummerj/3fe2eb057004b6742b89/raw/3da48d349c313684077d7103547dfe79f7052617/IonicSetup  -DisableReboots

-   **NOTE:** If you want to install any of the optional software you
    will need to fork the gist file and remove the \# in front of the
    line for the package you want to install.

Post Install Steps
------------------

### Configure Visual Studio Emulator for Android

-   Open up the Visual Studio Emulator for Android application
-   Find the devices that you want to download. Any device will do. I
    normally pick one of the latest ones as a starting point
    (Marshmellow 6.0 at the time of this writing)

Verify that everything works
----------------------------

1.  Open a command prompt
2.  Navigate the directory where you store you development projects (I
    use c:\\projects)
3.  From c:\\projects type: ionic start todo tabs
4.  cd into c:\\projects\\todo (directory was created by the ionic start
    command)

The first test that we are going to run is to make sure that we can test
the todo app that we generated in the web browser by running:

     ionic serve --lab

This will start up a node based web server and the –lab will tell it to
launch a page that shows what the app would look like on an iOS and
Android phone. Granted the node based serve is about 80% accurate but
good enough to do a majority of our testing. Ultimately you should test
on a device before releasing into the app stores.

Next we are going to test our Android device setup. The first thing we
need to do is tell ionic that we want to add the Android platform to our
todo app by running:

    ionic platform add android

This sets up the todo app to be able to be build and deployed to an
Android device. To validate that we can build for Android, run the
following:

    ionic build android

The last thing we need to verify is that we can deploy the todo app to
the Visual Studio Emulator for Android. Before we can deploy the
application, we need to start up the emulator.

1.  Open up the Visual Studio Emulator for Android

2.  Find the device that we downloaded

3.  Click the green arrow to start it up

4.  Once the emulator is started, you can deploy to it by running:

         ionic run android

You are now ready to go create your ionic applications.

### Share Post:

-   [](https://twitter.com/intent/tweet?text=Ionic%20-%20How%20to%20setup%20on%20Windows&via=digitaldrummerj "Tweet this")
-   [](https://www.facebook.com/sharer/sharer.php?u=https%3a%2f%2fdigitaldrummerj.me%2fionic-setup-windows%2f "Share on Facebook")
-   [](mailto:subject=Ionic%20-%20How%20to%20setup%20on%20Windows&https://digitaldrummerj.me/ionic-setup-windows/ "Send ia email")
-   [](https://plus.google.com/share?url=https%3a%2f%2fdigitaldrummerj.me%2fionic-setup-windows%2f "Share on Google+")
-   [](https://www.linkedin.com/shareArticle?mini=true&url=https%3a%2f%2fdigitaldrummerj.me%2fionic-setup-windows%2f "Share on LinkedIn")

Please enable JavaScript to view the [comments powered by
Disqus.](http://disqus.com/?ref_noscript)

### Subscribe

-   [RSS Feed](https://digitaldrummerj.me/feed.xml)

### Recent Posts ([All Posts](https://digitaldrummerj.me/blog/))

-   [Solved: Windows 10 Errors When Trying to Watch Video with HEVC
    Extension Not Found](https://digitaldrummerj.me/hevc-not-installed/)
-   [You Need Code
    Coverage](https://digitaldrummerj.me/why-code-coverage-is-important/)
-   [Stop The Zoom Trolls and Prevent
    Zoombombing](https://digitaldrummerj.me/stop-zoom-trolls/)
-   [Git: Clone Branch to New Repo without
    History](https://digitaldrummerj.me/git-clone-branch/)
-   [Which RxJS Operators to use in your NgRx
    Effects](https://digitaldrummerj.me/ngrx-effects-operators/)

### Archive

-   [By Date](https://digitaldrummerj.me/blog/archive/monthview)
-   [By Category](https://digitaldrummerj.me/blog/archive/categoryview)
-   [By Tag Cloud](https://digitaldrummerj.me/blog/archive/tagcloudview)

### Categories

-   [Android  (1)](https://digitaldrummerj.me/categories/android)
-   [Angular  (5)](https://digitaldrummerj.me/categories/angular)
-   [Angularjs  (5)](https://digitaldrummerj.me/categories/angularjs)
-   [Bash  (1)](https://digitaldrummerj.me/categories/bash)
-   [Blogging  (18)](https://digitaldrummerj.me/categories/blogging)
-   [Camtasia  (2)](https://digitaldrummerj.me/categories/camtasia)
-   [Chocolatey  (5)](https://digitaldrummerj.me/categories/chocolatey)
-   [Chrome  (2)](https://digitaldrummerj.me/categories/chrome)
-   [Community  (1)](https://digitaldrummerj.me/categories/community)
-   [Debugging  (1)](https://digitaldrummerj.me/categories/debugging)
-   [Docker  (3)](https://digitaldrummerj.me/categories/docker)
-   [Dotnet  (4)](https://digitaldrummerj.me/categories/dotnet)
-   [Dotnet Core
     (2)](https://digitaldrummerj.me/categories/dotnet-core)
-   [Git  (6)](https://digitaldrummerj.me/categories/git)
-   [Github  (5)](https://digitaldrummerj.me/categories/github)
-   [Gulp  (4)](https://digitaldrummerj.me/categories/gulp)
-   [How To  (2)](https://digitaldrummerj.me/categories/how-to)
-   [Iis  (1)](https://digitaldrummerj.me/categories/iis)
-   [Ionic  (12)](https://digitaldrummerj.me/categories/ionic)
-   [Jekyll  (16)](https://digitaldrummerj.me/categories/jekyll)
-   [Markdown  (1)](https://digitaldrummerj.me/categories/markdown)
-   [Meetup  (1)](https://digitaldrummerj.me/categories/meetup)
-   [Ngrx  (1)](https://digitaldrummerj.me/categories/ngrx)
-   [Node  (4)](https://digitaldrummerj.me/categories/node)
-   [Npm  (4)](https://digitaldrummerj.me/categories/npm)
-   [Nuget  (1)](https://digitaldrummerj.me/categories/nuget)
-   [Powershell  (1)](https://digitaldrummerj.me/categories/powershell)
-   [Productivity
     (5)](https://digitaldrummerj.me/categories/productivity)
-   [Proxy  (2)](https://digitaldrummerj.me/categories/proxy)
-   [Recording  (1)](https://digitaldrummerj.me/categories/recording)
-   [Speaking  (4)](https://digitaldrummerj.me/categories/speaking)
-   [Strongloop  (1)](https://digitaldrummerj.me/categories/strongloop)
-   [Testing  (1)](https://digitaldrummerj.me/categories/testing)
-   [Vagrant  (9)](https://digitaldrummerj.me/categories/vagrant)
-   [Virtualbox  (6)](https://digitaldrummerj.me/categories/virtualbox)
-   [Visual Studio
     (5)](https://digitaldrummerj.me/categories/visual-studio)
-   [Web Api  (3)](https://digitaldrummerj.me/categories/web-api)
-   [Windows  (5)](https://digitaldrummerj.me/categories/windows)
-   [Year in Review
     (1)](https://digitaldrummerj.me/categories/year-in-review)
-   [Zoom  (1)](https://digitaldrummerj.me/categories/zoom)

##### About This Site {.shadow-black}

Sharing my knowledge with others in a manner that is easy to understand
and consume. [More ›](https://digitaldrummerj.me/about/)

##### Services {.shadow-black}

-   [](https://digitaldrummerj.me/)
-   [Contact](https://digitaldrummerj.me/contact/ "Contact")
-   [RSS](https://digitaldrummerj.me/feed.xml "Subscribe to RSS Feed")

Created with ♥ by [Justin James](https://digitaldrummerj.me/about/). All
content is the property of Justin James and digitaldrummerj.me. This
blog, its content, and opinions are my own.

-   [](https://github.com/digitaldrummerj "Code and such...")
-   [](https://www.youtube.com/channel/UCDMvOL1XSKclxwplUT0fzLA "Tech Videos")
-   [](https://twitter.com/digitaldrummerj "Twitter")

