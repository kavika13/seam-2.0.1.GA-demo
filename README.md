Seam 2.0.1.GA simple application tutorial
==================

This is a tutorial for creating a Seam 2.0.1.GA web application from scratch.

**Tools used**:

- Java SE JDK 6 (Runtime framework)
- MySql 5.0.37 (Database)
- MySql Workbench (Database access tool - 5.2 is the latest as of now)
- JBoss AS 4.2 (Application Server)
- MySql Connector 5.0.5 (Database access from Java)
- Seam 2.0.1.GA (Web application development platform.  It includes JSF, RichFaces, Hibernate, and other things)
- Eclipse Galileo SR2 (IDE for Java web development)
- JBoss Tools 3.1 for Galileo (Plugins for ease of Seam development under Eclipse)

##Development Tool Installation

*Make sure you're connected to the Internet during all installation*

1. Install Java SE JDK 6 for Eclipse to run on - ([Direct Link](http://download.oracle.com/otn-pub/java/jdk/6u32-b05/jdk-6u32-windows-i586.exe))
  - Get from: [Java Downloads](http://www.oracle.com/technetwork/java/javase/downloads/index.html)  
    -> `Java SE 6` (whichever update version) -> `JDK` -> `Download` -> `Accept license agreement`  
    -> `Windows x86 (32-bit)` -> `jdk-6u32-windows-i586.exe`
  - Install all options (source code, development tools, runtime)
  - Don't bother registering
  - Set `JAVA_HOME` environment variable
     - `My Computer` -> `Properties` -> `Advanced System Settings` -> `Environment Variables` -> `System Variables`
     - `New` -> Variable Name: `JAVA_HOME`, Variable Value: `C:\Program Files (x86)\Java\jdk1.6.0_32` (or similar)
1. Install MySQL 5.0.37 - ([Direct Link](http://downloads.mysql.com/archives/mysql-5.0/mysql-essential-5.0.37-win32.msi))
  - Get from: [MySQL Archived Downloads](http://downloads.mysql.com/archives.php) -> `MySQL Database Server 5.0`  
    -> `5.0.37` -> `Microsoft Windows` -> `Microsoft Windows 32. (Windows Installer format)`
  - Typical install
  - Skip Sign-Up
  - Select `Configure the MySQL Server now` option
  - Select `Detailed Configuration`
  - Select `Developer Machine`
  - Select `Multifunctional Database`
  - Select path *other than* Installation Path - e.g. Drive: `C:` Path: `\MySQL Datafiles\`
  - Select `Decision Support (DSS)/OLAP`
  - Select `Enable TCP/IP Networking` and `Enable Strict Mode`
  - Select `Best Support for Multilingualism` (UTF8)
  - Select `Install As Windows Service`
  - Select `Include Bin Directory in Windows PATH`
  - Select `Modify Security Settings`, and give any root password you want.  
    Make it strong and easy to remember - See:  
     - [XKCD on secure *and* easy passwords](http://xkcd.com/936/)
     - [GRC Password "haystacks" article](https://www.grc.com/haystack.htm)
     - [Diceware low-tech secure password generation algorithm](http://world.std.com/~reinhold/diceware.html)
     - [Random.org secure dice roller](https://www.random.org/dice/)
  - Do *not* select `Enable root access from remote machines`
  - Click `Execute`
1. Install latest MySQL Workbench - ([Direct Link](http://www.mysql.com/downloads/mirror.php?id=408092#mirrors))
  - Get from: [MySQL Workbench Downloads](http://www.mysql.com/downloads/workbench/) -> `32 bit MSI installer`  
    -> Click `No thanks, just take me to the downloads!` instead of registering -> Select any mirror
  - Choose Setup Type: `Complete`
1. Install JBoss 4.2 Application Server - ([Direct Link](http://sourceforge.net/projects/jboss/files/JBoss/JBoss-4.2.3.GA/jboss-4.2.3.GA.zip/download))
  - Get from: [Application Server Downloads](http://www.jboss.org/jbossas/downloads/) -> `4.2` -> `4.2.3`  
    -> `Download` -> `jboss-4.2.3.GA.zip`
  - Unzip to a directory.  I'm using `C:\HappyPath\jboss-4.2.3.GA`
  - Run the `bin/run.bat` file to ensure the installation is okay.  No exceptions = good to go
  - If there are network bind errors, you can use `netstat -ano` to see which processes are using which ports.  
    Kill those processes.  If they are service related, you can using `services.msc` to stop them,  
    and set their startup type to `manual` or `disabled`
  - <kbd>CTRL + C</kbd> to kill the server when you're done.
  - When it asks, type `Y` then <kbd>enter</kbd> to terminate the batch file
1. Install MySQL Connector 5.0.5 - ([Direct Link](http://downloads.mysql.com/archives/mysql-connector-java-5.0/mysql-connector-java-5.0.5.zip))
  - Get from: [MySQL Archived Downloads](http://downloads.mysql.com/archives.php)  
    -> `MySQL Connector/J 5.0 (legacy)` -> `5.0.5` -> `ZIP format`
  - Extract file `mysql-connector-java-5.0.5\mysql-connector-java-5.0.5-bin.jar` to
    -> `<JBoss 4.2 Install Root>\server\default\lib\`
1. Install SEAM 2.0.1.GA library - ? (site is down right now)
  - Unzip to a directory.  I'm using C:\HappyPath\jboss-seam-2.0.1.GA
1. Install supported (Galileo SR2) Eclipse IDE for EE Developers - ([Direct Link](http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/galileo/SR2/eclipse-jee-galileo-SR2-win32.zip))
  - Get from: [Eclipse Download Page](http://www.eclipse.org/downloads/) -> `Older Versions`  
    -> `Eclipse Galileo SR2 Packages (v 3.5.2)` -> `Eclipse IDE for Java EE Developers` -> `Windows 32-bit`
  - Unzip to a directory.  I'm using C:\HappyPath\eclipse
  - Run Eclipse
  - Create your workspace wherever you like.  
    I'm using `C:\HappyPath\seam-2.0.1.GA-demo` and selecting to use it as default (for this install of Eclipse)
1. Install supported (Galileo) JBoss Tools through the Eclipse IDE
  - Found from: [JBoss Tools Download Page](http://www.jboss.org/tools/download)  
    See [Supported version table](https://community.jboss.org/wiki/MatrixofsupportedplatformsruntimesandtechnologiesinJBossToolsJBDS)
  - Make sure you're connected to the Internet
  - Click `Help` -> `Install New Software...`
  - Click `Add`
     - Name: `JBoss Tools Galileo`
     - Location: `http://download.jboss.org/jbosstools/updates/stable/galileo/`
  - Select: `All JBoss Tools`
  - Click `Next` to install those tools
  - On the `Review the items to be installed.` dialog, click `Next`
  - Accept the license agreement and click `Finish`
  - Allow the download and install to complete.  During the install, click to allow unsigned content,  
    and accept all certificates
  - When asked, restart Eclipse

##Setup local development database

1. Open MySql Workbench
1. Create a new schema named `bugtracker`
  - Double-click `Local instance MySQL` under `Open Connection to Start Querying`
  - Enter the `root` password you created above
  - Click the `+` icon to `Create a new schema in the connected server`
  - Name it `bugtracker`, and use Collation: `Server Default` (will end up as UTF8)
  - Click `Apply` and `Apply` again on the modal dialog that runs the command
1. Add a user named `tracker-dev`
  - Click the `Home` icon in the upper-left
  - Double-click `Local MySQL` under `Server Administration`
  - Enter the `root` password you created above
  - Click `Users and Privileges` on the left
  - Click `Add Account` at the bottom
  - Name them `tracker-dev`
  - Give them a dev-only password that can be checked in to source control (e.g. `password`)  
    Remember the password you use
  - Click `Apply`
1. Give ther user named `tracker-dev` priveleges to the `bugtracker` schema
  - Click `Schema Privileges` tab
  - Select `tracker-dev` user
  - Click `Add Entry` on lower-right
  - Click `Selected schema:`
  - Select the `bugtracker` schema
  - Click `OK`
  - Click `Select *ALL*` at the bottom to select to grant all privileges (except `GRANT`)
  - Click `Save Changes`

##Setup new Seam project

1. Start the wizard to create a new `Seam Web Project`
  - `File` -> `New` -> `Project...`
  - `Seam` -> `Seam Web Project`
1. Complete the `Create standalone Seam Web Project` wizard screen
  - Project Name: `simple-bug-tracker`
  - Project Location: `Use default`
  - Target Runtime: <skip>
  - Dynamic web module version: <skip> (says 2.5)
  - Target Server: `JBoss Community` -> `JBoss AS 4.2`
     - Home Directory: Full path to JBoss directory above (e.g. `C:/HappyPath/jboss-4.2.3.GA`)
     - JRE: `Default JRE for ...`
     - Directory: `server`, `default`
     - `Finish`
  - Configuration: `Dynamic Web Project with Seam 2.0`
1. Complete the `Configure project for building a Java application` wizard screen
  - Accept defaults all defaults
     - `src` folder on build path
     - Default output folder at `build\classes`
1. Complete the `Configure web module settings` wizard screen
  - Change the Content Directory
     - Context root stays as: `simple-bug-tracker`
     - Content directory changes to: `view`
     - Keep `Generate web.xml deployment descriptor` checked
1. Complete the `Add JSF capabilities to this Web Project` wizard screen
  - Use the default JSF Implementation Library and options
1. Complete the `Seam Facet` wizard screen
  - Add a Seam Runtime
     - Click `Add...`
     - Home Folder: `C:\HappyPath\jboss-seam-2.0.1.GA`
     - Name: `jboss-seam-2.0.1.GA`
     - Version: `2.0`
     - `Finish`
  - Deploy as: `EAR`
  - Database Type: `MySQL 5 (InnoDB)`
  - Connection Profile: `New`
     - Select `MySQL`, Name: `MySQL connector 5.0.5`, click `Next`
     - Driver: Click the `+`
     - `MySQL JDBC Driver` -> `MySQL` -> `5.0`
     - `Jar List` tab -> `Edit JAR/Zip...`  
       -> `C:\HappyPath\jboss-4.2.3.GA\server\default\lib\mysql-connector-java-5.0.5-bin.jar`
     - Database: `bugtracker`
     - URL: `jdbc:mysql://localhost:3306/bugtracker`
     - User name: `tracker-dev`
     - Password: `...` (Use the one you created for the `bugtracker-dev` user above)
     - Select `Save password`
     - Click `Test Connection` - This should be successful, saying `Ping succeeded!`
     - Click `Finish`
  - Database schema name: leave empty
  - Database catalog name: leave empty
  - Do *not* check `DB Tables already exist in database`
  - Do *not* check `Recreate database tables and data on deploy`
  - Leave the options under `Code Generation` as default
  - Click `Finish`
  - If it asks you about opening the `Seam perspective`, allow the IDE to open that perspective

##Test your new project

1. Click the `Server` tab
1. Select the `JBoss 4.2 Runtime Server`
1. Click the `Start the server` button (<kbd>CTRL + Alt + R</kbd> by default)
1. Verify no errors appear in the console
1. Navigate in your browser to `http://localhost:8080/simple-bug-tracker`

You should see a `Welcome!` page, and a description of the empty shell application you've created
