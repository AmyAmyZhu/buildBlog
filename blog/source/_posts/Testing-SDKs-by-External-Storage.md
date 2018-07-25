---
title: Testing SDKs by External Storage
date: 2018-07-19 09:54:22
---

After I built up release version of APKs/AARs files and push SDK to Artifactory for exposing Android libraries for developing and testing (I will write an article explaining what is Artifactory), I find out it is still hard to testing. I don’t know what is wrong with my SDKs after I imported to a new App since there is no log for realease version and I cannot use debug mode.

I finally find out one solution. I still feel like it is not the best. However, right now, I have no better solution. If you can solve this problem, please leave your comment and method here, it will help me out a lot.

My solution is to write logs into External Storage of my device. Remeber the article I write to explain how to write information into a device, I use this method to help me see where is the problem.

First, in order to write into external storage, I need to ask the device to have permission that can __WRITE_EXTERNAL_STORAGE__ in new App side. Here is the sample code:

```java
if (ContextCompat.checkSelfPermission(this, Manifest.permission.WRITE_EXTERNAL_STORAGE) != PackageManager.PERMISSION_GRANTED) {
    if (ActivityCompat.shouldShowRequestPermissionRationale(this,  Manifest.permission.WRITE_EXTERNAL_STORAGE)) {

    } else {
        ActivityCompat.requestPermissions(this,
            new String[]{Manifest.permission.WRITE_EXTERNAL_STORAGE},
            MY_PERMISSIONS_REQUEST);
    }
}
```

You can use the above code to ask other permissions as well. It is useful.