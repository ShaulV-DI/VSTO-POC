# Visual Studio Tools For Office (VSTO) POC

This is a proof-of-concept created for academic/learning purposes, demonstrating both local and remote use of VSTO "Add-In's".

<<< VIDEO/GIF HERE? >>>

## Requirements:

* Visual Studio
* Office 2016 (or later)
* An http server (optional, only required for remote delivery of VSTO)

## Notes:

The POC contains 2 components - a "loader" built in both local and remote flavors and "persist" which can be installed either locally or remotely.

### "Loader"

The "loader" component is intended to deliver and execute an executable from a hard-coded local network address (executable not provided. please make your own.) and install the accompanying "persist" add-in (from the same local network address) which will execute when word is executed. (you should change the network location of these in the code based upon your own testing environment!)

Local variant (all files required locally to execute) - can be found in ***/loader/bin/Release/***

Remote variant (only .docx required locally to execute) - can be found in ***/loader/Publish/*** (folder contents should be placed on delivering http server in %/loader/%)

### "Persist"

The "persist" component is intended to execute upon Word application startup, and will deliver and execute and executable from the same local network address as the "loader", and display a msgbox.

Local installation (all files required locally to install) - can be found in ***/persist/bin/Release/***

Remote installation - can be found in ***/loader/Publish/***, to install: ```%commonprogramfiles%\Microsoft Shared\VSTO\10.0\vstoinstaller.exe /i <network_path_to_persist.vso>``` (folder contents should be placed on delivering http server in %/persist/%)

## Establishing "trust":

In order to avoid easy weaponization of this POC, it's components are not signed in a trustworthy fashion, and if remote execution/installation is attempted without establishing prior "trust", it will fail.

If you intend on using this POC in remote fashion in your own environment please add your delivering http server to your executing machine's trusted intranet sites via windows internet options.

## Disclamer:

The code provided is offered as-is and is intended for educational or informational purposes only. The user assumes all responsibility for the use of this code and any consequences that may arise from its use. The creator of this code and its affiliates cannot be held liable for any damages or losses resulting from the use of this code

## Credit to prior research:

[https://bohops.com/2018/01/31/vsto-the-payload-installer-that-probably-defeats-your-application-whitelisting-rules/](https://bohops.com/2018/01/31/vsto-the-payload-installer-that-probably-defeats-your-application-whitelisting-rules/)

[https://medium.com/@airlockdigital/make-phishing-great-again-vsto-office-files-are-the-new-macro-nightmare-e09fcadef010](https://medium.com/@airlockdigital/make-phishing-great-again-vsto-office-files-are-the-new-macro-nightmare-e09fcadef010)