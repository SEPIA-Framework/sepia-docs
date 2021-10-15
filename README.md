# Welcome to the documentation page for SEPIA
Here you will (hopefully) find everything you need to know to get started with SEPIA.  

<p align="center">
  <img src="https://github.com/SEPIA-Framework/SEPIA-Framework.github.io/blob/master/img/SEPIA_ecosystem_w.png" alt="S.E.P.I.A. Logo"/>
</p>

Overview of SEPIA ecosystem (note: some parts are still in the dev branches).  
For image icon attributions please check the [homepage](https://sepia-framework.github.io/#attributions)

## Downloads
* SEPIA-Home (Server, Web-App + Apk, Tools): [v2.6.0](https://github.com/SEPIA-Framework/sepia-installation-and-setup/releases)
* SEPIA Client - Android: [v0.24.0 Apk](https://github.com/SEPIA-Framework/sepia-installation-and-setup/releases/download/v2.6.0/SEPIA-Android-Client.apk) | [Play Store](https://play.google.com/store/apps/details?id=de.bytemind.sepia.app.web)
* SEPIA Client - DIY (Raspberry Pi etc.): [Instructions](https://github.com/SEPIA-Framework/sepia-installation-and-setup/tree/master/sepia-client-installation)
* SEPIA STT Server: [v0.9.5](https://github.com/SEPIA-Framework/sepia-stt-server) | [Docker Hub](https://hub.docker.com/r/sepia/stt-server)
* SEPIA SDK: [v0.9.24](https://github.com/SEPIA-Framework/sepia-sdk-java)

## Wiki, Blog & News
Checkout the wiki for detailed descriptions:
[S.E.P.I.A. Framework Wiki](../../wiki)  
Visit Twitter for the latest news:
[S.E.P.I.A. Twitter Feed](https://twitter.com/sepia_fw)  
Visit the blog for summaries and guides:
[S.E.P.I.A. Blog](https://medium.com/sepia-framework)

## Intro
**S.E.P.I.A. is an acronym that stands for: self-hosted, extendable, personal, intelligent assistant**. It is a modular framework for voice-assistants equipped with all the required features and services to build a full-fledged digital assistant app, smart-speaker, smart-display or whatever you come up with :smiley:. It works out-of-the-box and has cross-platform support for browser, iOS and Android. The server is based on Java and can be operated on Windows, Linux and Mac. Due to it's lightweight architecture it even runs smoothly on a Raspberry Pi :relieved: :robot:.  
SEPIA currently has smart-services for: **news, music (radio), timers, alarms, reminders, to-do and shopping lists, smart home (e.g. using open-source tools like [openHAB](https://www.openhab.org)), navigation, places, weather, Wikipedia, web-search, Bundesliga soccer-results, a bit of small-talk and more**. To realize your own ideas you can use tools like the [SEPIA SDK](https://github.com/SEPIA-Framework/sepia-sdk-java) and the code editor integrated into the [SEPIA Control HUB](https://github.com/SEPIA-Framework/sepia-admin-tools/tree/master/admin-web-tools) to build services or write [custom HTML widgets](https://github.com/SEPIA-Framework/sepia-extensions) :man_mechanic::woman_scientist:!

### Architecture
The SEPIA Framework consists of 2 core parts: The SEPIA Client and the Assist-Server.  
  
**[SEPIA Client](https://github.com/SEPIA-Framework/sepia-html-client-app):** The user interface that handles **voice, text or touch interactions** and manages the "dialog" with the SEPIA server. Server responses can be presented as text (chat), graphical elements (cards, buttons) and/or sound including **speech synthesis (text-to-speech) and music (media-player)**. The client usually takes care of the speech-recognition (on-device or via SEPIA STT server) to transform voice into text and can even listen to wake-words like **Hey SEPIA** (thanks to Porcupine by Picovoice). There are clients for the browser, Android, iOS and a [DIY version](https://github.com/SEPIA-Framework/sepia-installation-and-setup/tree/master/sepia-client-installation) that even works "headless" for example on a Raspberry Pi.  
  
**[Assist-Server](https://github.com/SEPIA-Framework/sepia-assist-server):** The "brain" of SEPIA that receives requests from the client via the HTTP REST API and takes care of the **natural-language-understanding (intent and NER), conversation flow, smart-service integration** (like a to-do list or news service), user-accounts, **Text-to-Speech (TTS)** and more. The Assist-Server can run on it's own hardware for example on SBCs like a Raspberry Pi 3 or parallel to the client on more powerful systems (RPi4, desktop PC ect.).  
  
Because speech-recognition is a very delicate topic for multiple reasons (privacy, accuracy, performance, control etc.) the SEPIA Framework includes another major component: The Speech-To-Text (STT) server.  
  
**[SEPIA STT Server](https://github.com/SEPIA-Framework/sepia-stt-server):** An open-source server for **real-time speech-recognition** that runs on most systems (x86, ARM), **including Raspberry Pi** and supports custom, dynamic ASR models (thanks to great tools like Kaldi, [Vosk](https://github.com/alphacep/vosk-api) or [Zamia speech](https://github.com/gooofy/zamia-speech)).  
  
Other notable components of the SEPIA Framework are the [Control HUB](https://github.com/SEPIA-Framework/sepia-admin-tools) to manage server, "headless" clients, Smart Home and more, the [WebSocket server](https://github.com/SEPIA-Framework/sepia-websocket-server-java) for multi-channel chats and duplex data transfer, the [Teach-Server](https://github.com/SEPIA-Framework/sepia-teach-server) to store custom commands and a [Java SDK](https://github.com/SEPIA-Framework/sepia-sdk-java) to create powerful custom services.  

## Languages
Currently SEPIA works in German and English with basic support to create custom commands in other common languages. Some services like news and soccer-results are optimized for German meaning you will get an answer in English but might still see a mix of English and German news outlets or soccer results for the Bundesliga. The smart-services are constantly improving though and you can easily edit the list of outlets yourself.

## Quick-start (for users)
To use S.E.P.I.A. your personal, digital, open-source voice assistant you need 2 things:  
  
1. Access to a S.E.P.I.A. server. This can be [your own one](#quick-start-for-makers), running e.g. on a Raspberry Pi or your Windows/Mac PC (see below) or you can find an open one hosted by a friend or a company (Note: we are currently not hosting any public servers).
2. One of S.E.P.I.A.'s client apps, e.g. the web version: https://sepia-framework.github.io/app/ (hosted on your server as well) or the [official Android app](https://play.google.com/store/apps/details?id=de.bytemind.sepia.app.web)  
  
To connect to a custom server simply open the app, change the "hostname" in the log-in screen and restart the app. A typical hostname could be the IP of the server, "raspberrypi.local", "my-server.example.org/sepia" or simply keep "localhost" (for test-servers on the same machine).

## Quick-start (for makers)

Basic steps to install the server:
* Make sure you have Java JDK 8 or 11 installed
* Download the latest SEPIA-Home bundle from [here](https://github.com/SEPIA-Framework/sepia-installation-and-setup/releases/latest)
* Extract the zip and run "setup" (.bat for Windows, .sh for Linux/Mac)
* Optional (advanced users): If you need a reverse-proxy install Nginx and use the included SEPIA configuration
* Start the server (e.g. with the "run-sepia"-script) and continue with "Quick-start (for users)" [above](#quick-start-for-users) :-)
* Use 'localhost', your IP or the proxy address (with path /sepia) as hostname :-)

Instructions and an (almost) automatic installation script for **Raspberry Pi** can be found [-HERE-](https://github.com/SEPIA-Framework/sepia-docs/wiki/Installation#raspberry-pi-installation-via-script)  
  
Instructions for the installation of the S.E.P.I.A. server stack on **Linux, Windows or Mac** can be found [-HERE-](https://github.com/SEPIA-Framework/sepia-installation-and-setup)  

## Questions and bug-reports
If you have any questions, need help or want to report a bug please go [here](https://github.com/SEPIA-Framework/sepia-docs/issues) or start a [discussion here](https://github.com/SEPIA-Framework/sepia-docs/discussions).

## API keys for services
Some services integrated in SEPIA require an API key to run properly (e.g. navigation/reverse geo-coding). Find out how to get them (for free) [here](../../wiki/API-keys).

## Final notes
If you run your own server and decide to open it to the public or to your friends please make sure it is properly secured and inform the users about your data privacy policy since you are operating a database with potentially sensitive, personal information.
