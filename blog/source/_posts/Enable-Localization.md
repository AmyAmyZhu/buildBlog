---
title: Enable Localization
date: 2018-06-29 09:55:28
---

When we have customized strings in an Andriod App, where are you store them? Some people choose to assign strings directly in the code. However, cosidering a good desgin patern, Andriod separates code and resources. Most of good Android developer put strings in `strings.xml` which is located under __res > values__. This is because we can easily manipulates and customize values.

One of the benefits that is intuitionally affects an Andriod App is we can enable localizations. Localization means you can have multiple languages of your App based on the language users setted up. For example, if you implements your App in English, but your user is a French. You can translates values in `strings.xml` in French version, so that when user open your App, they can understand your App because the language of your App will be French.

###How to Enable Localization?
It is easy, just follow the following steps:

1. Select __res > values__.
2. Right-click the strings.xml file and select Open Translations Editor.

Then traslations editor will displays the key and value pairs from the `strings.xml`, you can add any languages you want by click the small add button. It will generate a new row that you can put the new language values your want to translate.

Actually, traslations editor is just a GUI table for you to manipulates values, sometimes, if your App is big, Android Studio might be slow to change values. Then you can go to the language specific `strings.xml`, for example, you will find `strings.xml(ch)` after your first time add value in translations editor. Go there, and change values in those new files.