Ionic - How to setup on Windows
 Sun Jan 11, 2015  ionic
Updates:

2016-08-13: Added Gradle and VS Code to software installed. Changed from JDK7 to JDK8. Removed Ant. Added Android SDK Apis install to Chocolatey script. Switched suggested emulator to Visual Studio Emulator for Android.
If you are like me and just starting to work with the Ionic Framework and don’t already have a machine setup to do Android, iOS, Node, etc development then many of the guides out there leave out a number of steps that you need to do in order to get everything working.

It is really easy to get everything working though once you know the steps. Since I am a Windows user and love to automate work that is easily repeatable, I used Chocolatey and Boxstarter to automate the setup for the Ionic Framework.

On Windows, you will only be able to setup Android development. Apple requires a Mac in order to do iOS development.

Software to be installed
NodeJS
Git
Gradle
JDK8
Android SDK
Android Studio
Google Chrome
Npm Modules:
cordova
gulp cli
bower
ionic
Visual Studio Emulator for Android (Hyper-V Based)
VS Code
How to install software
Install Chocolatey from http://www.chocolatey.org. Command is on the front-page of the site or below. Open an administrative command prompt to run the command. To open an administrative command prompt on Windows 8, go to the start menu, type cmd and then ctrl+shift+click on the cmd search result.

 Command Prompt: @powershell -NoProfile -ExecutionPolicy unrestricted -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
Install the BoxStarter Chocolatey package

 choco install -y BoxStarter
Close the command prompt that you opened to install Chocolatey and BoxStarter

On the desktop there should be a BoxStarter Shell icon, double-click on that to run it. If the icon is not on the desktop, then open up a command prompt and type BoxStarterShell.

I have setup a gist file that has all of the Chocolatey commands to run to install the rest of the software and configure it. Run the gist file from the Boxstarter Shell:

 Install-BoxStarterPackage -PackageName  https://gist.githubusercontent.com/digitaldrummerj/3fe2eb057004b6742b89/raw/3da48d349c313684077d7103547dfe79f7052617/IonicSetup  -DisableReboots
NOTE: If you want to install any of the optional software you will need to fork the gist file and remove the # in front of the line for the package you want to install.
Post Install Steps
Configure Visual Studio Emulator for Android
Open up the Visual Studio Emulator for Android application
Find the devices that you want to download. Any device will do. I normally pick one of the latest ones as a starting point (Marshmellow 6.0 at the time of this writing)
Verify that everything works
Open a command prompt
Navigate the directory where you store you development projects (I use c:\projects)
From c:\projects type: ionic start todo tabs
cd into c:\projects\todo (directory was created by the ionic start command)
The first test that we are going to run is to make sure that we can test the todo app that we generated in the web browser by running:

 ionic serve --lab
This will start up a node based web server and the –lab will tell it to launch a page that shows what the app would look like on an iOS and Android phone. Granted the node based serve is about 80% accurate but good enough to do a majority of our testing. Ultimately you should test on a device before releasing into the app stores.

Next we are going to test our Android device setup. The first thing we need to do is tell ionic that we want to add the Android platform to our todo app by running:

ionic platform add android
This sets up the todo app to be able to be build and deployed to an Android device. To validate that we can build for Android, run the following:

ionic build android
The last thing we need to verify is that we can deploy the todo app to the Visual Studio Emulator for Android. Before we can deploy the application, we need to start up the emulator.

Open up the Visual Studio Emulator for Android

Find the device that we downloaded

Click the green arrow to start it up

Once the emulator is started, you can deploy to it by running:

 ionic run android
You are now ready to go create your ionic applications.