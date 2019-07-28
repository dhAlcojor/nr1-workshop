Lab 0: Building your first Add-on
=======================================================

The purpose of this lab is to provide hands on experice building your first Add-on interacting with NR1 CLI and the capabilities of New Relic One.

After this lab you should understand:

* How to create and locally develop an Add-on
* How to use the CLI to create a launcher
* How to use the CLI to create a Nerdlet
* How to connect a launcher to a Nerdlet

# Step 0: Setup and Prerequisites

Load the prequisites and follow the setup instructions in [Setup](../SETUP.md).

**Reminder**: Make sure that you're ready to go with your `lab0` by ensuring you've run the following commands:

```bash
# from the nr1-eap-workshop directory
cd lab0
npm install
```

# Step 1: Create a launcher
Launchers are a type of artifact within an Add-on that is selectable form the New Relic One homepage, and serves as an entry to a Nerdlet.

1. Use the NR1 CLI to create a launcher

```bash
# assuming we're in nr1-eap-workshop/lab0
nr1 create
? What kind of component do you want to create? launcher
? Name your component. lab0-launcher
Component created successfully!

your lab0-launcher is available at "./lab0/launchers/lab0-launcher"
```
You'll notice that the CLI creates a `./lab0/launchers/lab0-launcher` directory: with a nr1.json configuration.

2. Navigate in Google Chrome to https://one.newrelic.com?use_version=45a97944&packages=local and click on the Lab 0 Launcher.

![lab0-launcher](../screenshots/lab0_screen01.png)

3. Your browser should look like the screenshot below showing a 404 error message. Currently, the Lab 0 launcher is not connected to a Nerdlet and causes an error to be displayed.

![lab0-launcher-clicked](../screenshots/lab0_screen02.png)

In the next steps we'll create a new Nerdlet and connect our launcher to this Nerdlet.


# Step 2: Create a Nerdlet
A Nerdlet is the main artifact that is included within an Add-on package. A Nerdlet consits of three files by default: index.js, styles.scss, and a nr1.json configuration.

Within a Nerdlet is where the bulk of the code in your Add-on will live.

1. Use the CLI to create a Nerdlet

```bash
# assuming we're in nr1-eap-workshop/lab0
nr1 create
? What kind of component do you want to create? nerdlet
? Name your component. lab0-nerdlet
Component created successfully!

your lab0-nerdlet is available at "./lab0/nerdlets/lab0-nerdlet"
```

You'll notice that the CLI creates three files in the `./lab0/nerdlets/lab0-nerdlet` directory: index.js, styles.scss, and a nr1.json configuration.

2. Open the project in your text editor or IDE (reminder: these instructions assume Visual Studio Code)

```bash
# if you're not there already, navigate to the workshop directory
cd nr1-eap-workshop/lab0
# open the current project directory in your IDE
code .
# voilà
```

3. A nerdlet is created and added to the `./lab0/nerdlets` folder. Your code editor should look similar to the screenshot below:

![lab0-nerdlet-created](../screenshots/lab0_screen03.png)

4. If you navigate back to https://one.newrelic.com?use_version=45a97944&packages=local and click on the Lab 0 Launcher. You'll notice that you get the same error message from Step 1.

![lab0-launcher-clicked](../screenshots/lab0_screen02.png)

This is because your launcher configuration needs to be updated to connect to the `lab0-nerdlet`.

# Step 3: Connecting your launcher and Nerdlet

1. Within `./lab0/launchers/lab0-launcher` open the launcher `nr1.json` configuration file adding the correct `rootNerdletId`

![lab0-launcher](../screenshots/lab0_screen04.png)

2. Replace the code within your `./lab0/launchers/lab0-launcher/nr1.json` with the JSON object below.

```bash
{
    "schemaType": "LAUNCHER",
    "id": "lab0-launcher",
    "displayName": "Lab0Launcher",
    "description": "",
    "icon": "interface_placeholders_icon-placeholder",
    "rootNerdletId": "lab0.lab0-nerdlet"
}

```

3. Save the nr1.json, then navigate back https://one.newrelic.com?use_version=45a97944&packages=local and click on the Lab 0 Launcher. Your browser window should look similar to below with the `lab0-nerdlet` launched.

![lab0-nerdlet](../screenshots/lab0_screen05.png)

_Note: if not, restart your local developer server by typing a Ctrl+ESC in the Terminal and then running npm start.

# Step 4: Creating a package

## What is a package? ##

A package is a deployable unit that contains one or more artifacts.  A Nerdlet is the main artifact in of a package, but packages can also include launchers, overlays, hooks, and enitites.

In steps 1 -3 we were creating a `lab0` package. Yet, there is a quicker way to create packages with a launcher and Nerdlet already connected.

`nr1 create` will do it for you!

From your root directory (or the directory your want your packages located). Run the following command in your terminal:

```bash
# The CLI will create a new folder to contain the artifacts within your package
nr1 create
? What kind of component do you want to create? package
? Name your component. lab0-package
Component created successfully!

```
You'll notice that the CLI creates a `/lab0-package` directory: including a launchers and nerdlets folder, and all the needed internal files.

![lab0-package](../screenshots/lab0_screen06.png)

# For Consideration / Discussion

- How do you use a Nerdlet to build custom visaulizations? How do you access your account data?
