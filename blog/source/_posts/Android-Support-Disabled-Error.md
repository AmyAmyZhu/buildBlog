---
title: Android Support Disabled Error
date: 2018-09-18 09:21:50
tags: Android
---

Open Android Studio badly will possiably cause the following problem:

```
Problems found loading plugins:
Plugin "Google Analytics Uploader" was not loaded: required plugin "Android Support" is disabled.
Plugin "SDK Updater" was not loaded: required plugin "Android Support" is disabled.
Plugin "Android NDK Support" was not loaded: required plugin "Android Support" is disabled.
Plugin "Google App Indexing" was not loaded: required plugin "Android Support" is disabled.
Plugin "Google Cloud Tools For Android Studio" was not loaded: required plugin "Android Support" is disabled.
Plugin "Google Cloud Testing" was not loaded: required plugin "Android Support" is disabled.
Plugin "Google Services" was not loaded: required plugin "Android Support" is disabled.
```

What I mean badly is when you close Android Studio but there are some demons still running in background, this will cause linking issues between projects. Or it is possible because you delete caches manually:

```
cd .android
rm -r build-cache
```

## How to Solve this error?

Go to path `File -> Settings -> Plugins`, you will see "Android Support" is disabled. Enable this and restart Android Studio will solve this problem.