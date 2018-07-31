---
title: Apply Dexguard for Modules
date: 2018-07-13 09:58:09
---

###How to apply Proguard/Dexguard

Proguard/Dexguard shrink and obsfucate resources and codes by scanning and looping up the dependencies. It will do everything it thinks necessary. To apply proguard, simple change __minifyEnabled__ in the module/app you want to apply to be true. Android will apply for Proguard automatically.

```java
buildTypes {
    release {
        minifyEnabled true
    }
}
```

Make sure you are in the correct building type when you use Proguard/Dexguard. You can check __Build Variants__ to see it you are in the correct building type or not.

For applying Dexguard, you need to first buy licence of dexguard, and then put the licence file under your App library. You also need to change file __gradle.properties__ which sepcify where you put the Dexguard licence. For example:

```java
systemProp.dexguard.licence=./app/libs/
```

Then your app knows where to find and verify your Dexguard licence. It is not only suitable for Dexguard licence, but also other Applications/Library licences.

To apply Dexguard, first add a line in your app/module gradle file that says:

```java
apply plugin: 'dexguard'
```

Next you don’t need to change __minifyEnabled__ to be true. Create a new txt file under your app files. You can call it __dexguard-project.txt__. Add Proguard/Dexguard rules in this file. Then go back to gradle file, add this line to tell your app where you put Dexguard rules:

```java
buildTypes {
    release {
        minifyEnabled false
        proguardFile 'dexguard-project.txt'
    }
}
```

###Apply Dexguard for Android Libraries

If you want to build up an Android library and you want to ship to SDK version to others. It is extremely important you Proguard/Dexguard your SDK, otherwise reverse engineers can see how you implement your library. It is a little bit different when you apply Proguard/Dexguard.

There are four main rules for Proguard/Dexguard to protect your Apps:

- obfuscate: rename things, make revise engineer cannot understand your codes. They might find out multiple classes and methods are called, for example, a, therefore, they cannot find the relationship and dependencies of classes.
- preverify: pre-proguard your app. No need for Android Apps.
- shrink: remove unused resources. It will make your APKs/AARs small and efficient.
- optimize: optimize your code, reduce dependencies of your code.

If you don’t know how to make your module to be library or you don’t know if your module is a library or not. Check if you have this line in your gradle file:

```java
apply plugin: 'com.android.library'
```

Not only you still need __proguardFile__ line, but also please add __cosumerProguardFiles__ to tell Dexguard this is a library.

```java
buildTypes {
    release {
        minifyEnabled false
        proguardFile 'dexguard-project.txt'
        cosumerProguardFiles 'dexguard-project.txt'
        }
}
```

###Key methods in Dexguard

Now we know how to apply Proguard/Dexguard, but how to apply Dexguard rules and how to use them? I am going to illustrate four import keep rules in Proguard/Dexguard.

1. No rule

|           | Classes     | Members  |
|-----------|-------------| ---------|
| shrink    | yes         | yes      |
| obfuscate | yes         | yes      |

It is default. If you don’t specify a keep directive of any kind, then Proguard is going to both shrink (remove unused code) and obfuscate (rename things) both classes and class members.

2. -keep
|           | Classes     | Members  |
|-----------|-------------| ---------|
| shrink    | no         | no      |
| obfuscate | no         | no      |

Keep means opposite of no rules. No shrinking, no obfuscation; not for classes, not for members. __-keepclasseswithmembers__ is same as __-keep__.

3. -keepclassmembers

|           | Classes     | Members  |
|-----------|-------------| ---------|
| shrink    | yes         | no      |
| obfuscate | yes         | no      |

This protects only the members of the class from shrinking and obfuscation.

4. -keepnames

|           | Classes     | Members  |
|-----------|-------------| ---------|
| shrink    | yes         | yes      |
| obfuscate | no         | no      |

This only allows shrinking for classes and members, but not obfuscation. __-keepclasseswithmembernames__ act the same as __-keepnames__.

5. keepclassmembernames

|           | Classes     | Members  |
|-----------|-------------| ---------|
| shrink    | yes         | yes      |
| obfuscate | yes         | no      |

This just not obfuscate members.

6. Others
    - For Android, I faced a problem when I want to apply Proguard/Dexguard to a library which contains jni .so files. Remember to add __-keepresources__ to such source files, otherwise, the name and contant will be obsfucate. Also, add __-dontpreverrify__ at the beginning of your Proguard/Dexguard rules of your Android Application. The reason you’d better to do that is because __-dontpreverify__ prevent pre-proguard your APKs/AARs. There is no need to do so for Android and it will save time.

###Examples

Keep Constructor/Methods of a class:

```java
-keep, allowshrinking, allowoptimization class com.package.company.class {
    <init>(...);
    void iAmAMethod(int);
}
```
