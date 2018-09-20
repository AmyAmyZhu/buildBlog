title: Build Proguard For Release Takes Too Long
date: 2018-09-18 08:52:10
categories:
- [Android, Errors]
tags:
- Proguard/Dexguard
- Errors
- Android
---

Recently when I enabled Proguard in my program like the following:

```
release {
    minifyEnabled true
    shrinkResources true
    proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
}
```

I faced the problem that it tooks like for ever for the process of `transformClassesAndResourcesWithProguardForRelease`. This problem happens when you have multiple libraries need to be Proguard/Dexguard. Add the line `multiDexEnabled true` in to your gradle `defaultConfig` will fix this problem.

<!-- more -->