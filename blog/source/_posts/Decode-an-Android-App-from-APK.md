---
title: Decode an Android App from APK
date: 2018-06-27 09:57:04
---

If an Android App not doing encryption or obfuscation, an APK (Android application package) is easily be decoded. A reverse engineer can see its source codes and XML files.

Here is the procedure how to decoding .apk files to get source files.

1. Go to project, Build -> Build APK(s). After .apk file is generated, click “locate” to the path of the file.
2. Create a new folder, let’s call it “decode”.
3. Copy .apk file into decode folder. Rename the extension of it to .zip and save it. Now you can see classes.dex file in this directory.
4. Extract .zip file in decode folder.
5. Download [dex2jar](https://sourceforge.net/projects/dex2jar/files/latest/download) and extract it in decode directory.
6. Copy classes.dex and paste it besides dex2jar.jar, which is inside dex2jar directory.
7. Open command prompt and go to dex2jar directory, call `d2j-dex2jar classes.dex` to pass in calsses.dex into d2j-dex2jar and execute it to get classes.dex.dex2jar.
8. Download [jd-gui](http://jd.benow.ca/). For Windows, download jd-gui-windows-X.X.X.zip.
9. Open jd-gui, and open classes.dex.dex2jar file.

Now you are able to see all source files from .apk file.