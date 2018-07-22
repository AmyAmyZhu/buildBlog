---
title: Maunally Import a Library in an Android Project
date: 2018-06-27 09:56:15
---

Sometimes we use third-party library, or we implements a module and want it to be a part of our main code’s library. In both scenarios, we can import a library as a module.

###How to import a library in Android Studio?

1. __File > New > Import modlue > add the library path__.
2. Change library module gradle:
    1. Change `“apply plugin: ‘com.android.application’”` to `“apply plugin: ‘com.android.library’”`
    2. Remove applicationId.
3. Change dependency from “compile” to “implementation”
4. __File > Project Structure > app > Dependencies__, add module library.
5. Downgrade gradle version in project gradle to “2.3.3” or “2.3.2”
6. Put/Change “buildToolsVersion “27.0.1” and “useLibrary ‘org.apache.http.legacy’” in app and carto library module.

###UnsatisfiedLinkError happens?

This is because no .so file in the app to let the app know there is a new library added. There are several steps involved to add up .so file.

1. Go to __Project__ view.
2. Copy library directory, move it under __app > libs__. Now you are able to see .so files.
3. Copy __jni__ directory under __app > src > main__.
4. Change name of this directory from __jni__ to __jniLibs__.
5. Delete no longer using library directory in __app > libs__.

Now .so file exists in the app in a correct directory.
Then open mainAcitivity add those lines in the class:

```java
static {         
    System.loadLibrary("library"); 
}
```

###How to Run?

Since we added a library as a module, therefore, our compile will ask us to edit configuration. To avoid that, go back to MainActivity and run MainActivity instead.

###Import library by .aar file

It is much more easy than import a library by moudle. Some library provide .aar file, we can simply import it by those following steps:

1. add `flatDir {dirs 'libs' }` in the project level build.gradle under `allprojects { repositories { ... } }` level.

2. copy .aar file that you want to import under the app’s libs directory.

3. add `implementation(name: 'XXX', ext: 'aar')` in the app level build.gradle under dependencies level.
