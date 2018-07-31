---
title: Read and Store Json Files in Internal Storage
date: 2018-06-28 11:39:53
---

Understanding the storages in an Android device, you can easily check or transfer files in both directions: your app and the device. For example, if your app have a licence file, and you want to check the permission, you can store licence file in Android device for further updating and changing.

###Storages in an Android Device

To work with your device’s file system, do the following:

1. Open the device file browser by clicking __View > Tool Windows > Device File Explorer__.
2. Select a device from the drop-down list.

There two useful storages you can store your data:

- one is the internal storage, which is located at: `data/data/app_name/`
- another one is the external user storage, which is located at: `sdcard/`

###Examples for Creating files

Here is a sample code that creates a file in the internal storage:

```java
 public void createFile() {
    try {
        File checkFile = new file(context.getApplicationInfo().dataDir + "/new_directory_name/");
        if(!checkFile.exists()) {
            checkFile.mkdir();
        }
        FileWriter file = new FileWriter(checkFile.getAbsolutePath() + "/filename");
        file.write("what you want to write in internal storage");
        file.flush();
        file.close();
    } catch(IOException e) {
        e.printStackTrace();
}
```
