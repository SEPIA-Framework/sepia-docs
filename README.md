## [UNDER CONSTRUCTION]  

# Welcome to the documentation page for SEPIA
Here you will (hopefully) find everything you need to know to get started with SEPIA.  

<p align="center">
  <img src="https://github.com/SEPIA-Framework/SEPIA-Framework.github.io/blob/master/img/icon-w.png" alt="S.E.P.I.A. Logo"/>
</p>

## Wiki
Checkout the wiki for detailed descriptions:
[S.E.P.I.A. Framework Wiki](../../wiki)

## Quick-start (for users)
To use S.E.P.I.A. your personal, digital, open-source voice assistant you need 2 things:

1. One of S.E.P.I.A.'s client apps, e.g. the web version: https://sepia-framework.github.io/app/ (app store versions coming soon)
2. Access to a S.E.P.I.A. server. This can be [your own one](https://github.com/SEPIA-Framework/sepia-installation-and-setup), running e.g. on a Raspberry Pi or your Windows/Mac PC (see below) or you can find an open one hosted by a friend or a company (Note: the official SEPIA team is currently not hosting any public servers).

To connect to a custom server simply open the app, skip the log-in, change the "host name" in the main menu and restart the app. A typical host name would be "my-server.example.org/sepia". 

## Quick-start (for makers)
Release bundles and instructions for easy-installation of the S.E.P.I.A. server stack can be found here:
https://github.com/SEPIA-Framework/sepia-installation-and-setup

## Build-your-own (for experts)
Since everything in S.E.P.I.A. is open-source you can always build the whole framework from scratch using the Github repositories.
A first draft of the requirements to do so can be found [here](https://github.com/SEPIA-Framework/sepia-docs/wiki/Requirements).
This is (very) roughly what you need to do if you deploy all servers on one machine:

* Create a SEPIA folder and clone the core components of the framework:  
`git clone https://github.com/SEPIA-Framework/sepia-core-tools-java.git`  
`git clone https://github.com/SEPIA-Framework/sepia-websocket-server-java.git`  
`git clone https://github.com/SEPIA-Framework/sepia-assist-server.git`  
`git clone https://github.com/SEPIA-Framework/sepia-teach-server.git`

* Import each repository in your IDE (e.g. [Eclipse](https://de.wikipedia.org/wiki/Eclipse_(IDE)) as Maven-Project. Then export the servers as executable JARs (use .../server/Start.java as main method).

* Copy your executable JARs and the 'Xtensions' folder for each server to a new folder. Check out [these](https://github.com/SEPIA-Framework/sepia-installation-and-setup/tree/master/) examples for a base folder. You will also find start, stop and other useful scripts to operate the server there.

* Get [Elasticsearch](https://www.elastic.co/products/elasticsearch) 5.3.3. ([official zip-file](https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-5.3.3.zip)) and run it on port 20724 (or change the default port in the config-files of the SEPIA servers, e.g.: [this one](https://github.com/SEPIA-Framework/sepia-assist-server/blob/master/Xtensions/assist.properties) and [this one](https://github.com/SEPIA-Framework/sepia-teach-server/blob/master/Xtensions/teach.properties))

* While Elasticsearch is running use the setup-function included in the Assist-Server to initialize the database, e.g.:  
`java -jar sepia-assist.jar setup --my`  
Note the flag **"--my"**! It can be used to switch server configurations between "--test", "--my" and "--live" (corresponding to the files in the 'Xtensions' folder) and has to be used when starting each server as well. The setup will also write some core accounts to your database and config files.

* If everything worked out you can boot up the whole server stack now. Start the database and servers in the following order:  
  * Elasticsearch (if not running already)
  * Assist-Server, e.g. `java -jar sepia-xyz.jar --my` (used by other servers get config data and authenticate users)
  * Chat-Server and Teach-Server (order does not matter here)
    
* Use one of the SEPIA clients to connect to your server stack. Inside the client you might want to set a proper host-name (see menu). If you are not running the client on the same machine you can replace 'localhost' by either an IP address or you can set-up your own proxy (e.g. [Nginx](https://de.wikipedia.org/wiki/Nginx)). Another great tool to use here is [ngrok](https://ngrok.com/docs). More help about this part will be added soon!

## Final notes
If you run your own server and decide to open it to the public or to your friends please make sure to inform them about your data privacy policy since you are operating a database with user-accounts.
