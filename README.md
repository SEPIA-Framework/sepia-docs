# Welcome to the documentation page for SEPIA
Here you will (hopefully) find everything you need to know to get started with SEPIA.  

<p align="center">
  <img src="https://github.com/SEPIA-Framework/SEPIA-Framework.github.io/blob/master/img/SEPIA_ecosystem_w.png" alt="S.E.P.I.A. Logo"/>
</p>

Overview of SEPIA ecosystem (note: some parts are still in the dev branches).  
For image icon attributions please check the [homepage](https://sepia-framework.github.io/#attributions)

## Wiki, Blog & News
Checkout the wiki for detailed descriptions:
[S.E.P.I.A. Framework Wiki](../../wiki)  
Visit Twitter for the latest news:
[S.E.P.I.A. Twitter Feed](https://twitter.com/sepia_fw)  
Visit the blog for summaries and guides:
[S.E.P.I.A. Blog](https://medium.com/sepia-framework)

## Intro
**S.E.P.I.A. stands for server-based, extendable, personal, intelligent assistant** and is a modular framework for voice-assistants on the one hand and a ready-for-action digital assistant app that works cross-platform on browser, iOS and Android on the other hand. The server is based on Java and can be operated on Windows, Linux and Mac. Due to it's lightweight architecture it even works on a Raspberry Pi smooth and easy :relieved: :robot:  
SEPIA has smart-services for: **news, music (radio), timers, alarms, reminders, to-do and shopping lists, navigation, places, weather, Bundesliga soccer-results, Wikipedia, web-search and a bit of small-talk**. Some smart-home commands are prepared for integration as well and are waiting to get connected to other great open-source tools like Home Assistant (anybody wants to help? ^^).

### Architecture
The SEPIA Framework basically consists of 2 major parts: The [SEPIA Client](https://github.com/SEPIA-Framework/sepia-html-client-app) and the [Assist-Server](https://github.com/SEPIA-Framework/sepia-assist-server).  
  
**SEPIA Client:** The user interface that takes care of the speech-recognition to transform voice into text, sending that text to a SEPIA server for interpretation, receiving the result (in JSON format) and presenting it to the user via text, graphical elements and/or sound (text-to-speech). Typical clients can be iOS and Android apps, websites or even command-line tools combined with just a microphone.

**Assist-Server:** The "brain" of SEPIA that receives requests from the client via the HTTP REST API and takes care of the natural-language-understanding (intent and NER), conversation flow, smart-service integration (like a to-do list or news service), user-accounts and more. The Assist-Server can run on it's own Raspberry Pi or parallel to the client on more powerful systems (desktop PC ect.).  
  
Other notable components of the SEPIA Framework include a [WebSocket server](https://github.com/SEPIA-Framework/sepia-websocket-server-java) for chats and a [wake-word tool](https://github.com/SEPIA-Framework/sepia-wakeword-tools) for **"Hey SEPIA"** that even works on a Raspberry Pi Zero :relaxed: (thanks to Porcupine by Picovoice) and a [Speech-To-Text server](https://github.com/SEPIA-Framework/sepia-stt-server) that supports Kaldi open-source ASR (thanks to [Zamia speech](https://github.com/gooofy/zamia-speech)).  

## Languages
Currently SEPIA works in German and English with some services like news and soccer-results still optimized only for German meaning you will get an answer in English but see German news outlets for example or only Bundesliga results. The smart-services are constantly improving though.

## Quick-start (for users)
To use S.E.P.I.A. your personal, digital, open-source voice assistant you need 2 things:

1. One of S.E.P.I.A.'s client apps, e.g. the web version: https://sepia-framework.github.io/app/ (app store versions coming soon)
2. Access to a S.E.P.I.A. server. This can be [your own one](https://github.com/SEPIA-Framework/sepia-installation-and-setup), running e.g. on a Raspberry Pi or your Windows/Mac PC (see below) or you can find an open one hosted by a friend or a company (Note: the official SEPIA team is currently not hosting any public servers).

To connect to a custom server simply open the app, change the "hostname" in the log-in screen and restart the app. A typical hostname could be the IP of the server, "raspberrypi.local", "my-server.example.org/sepia" or "[your-ngrok-url]/sepia" (for test-servers). 

## Quick-start (for makers)
Release bundles and instructions for easy-installation of the S.E.P.I.A. server stack on Linux, Windows or Mac can be found here:
https://github.com/SEPIA-Framework/sepia-installation-and-setup  

Basically the steps are:
* Make sure you have at least Java 8 installed
* Download the latest SEPIA-Home bundle from [here](https://github.com/SEPIA-Framework/sepia-installation-and-setup/releases/latest)
* Extract the zip and run "setup" (.bat for Windows, .sh for Linux/Mac)
* Start the server (e.g. with the "run-sepia"-script) and continue with "quick-start (for users)" :-)
* Optionally start the SEPIA proxy (e.g. with the "run-reverse-proxy"-script) if you need one 
* Continue with "Quick-start (for users)" and use 'localhost', your IP or the proxy address (with path /sepia) as hostname :-)

## Questions and bug-reports
If you have any questions, need help or want to report a bug please go [here](https://github.com/SEPIA-Framework/sepia-docs/issues).

## API keys for services
Some services integrated in SEPIA require an API key to run properly (e.g. Weather via forecast.io). Find out how to get them (for free) [here](../../wiki/API-keys).

## Final notes
If you run your own server and decide to open it to the public or to your friends please make sure to inform them about your data privacy policy since you are operating a database with user-accounts.
