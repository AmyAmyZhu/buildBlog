---
title: How to publish your Android App?
date: 2018-06-27 09:55:30
---

###Steps:
1. Make sure the current version is great.
2. Change version number for all gradles.
3. Generate signed APK
    - __File > Project Structure__, deal with Signing and Build Types
    - __Build > Generate Signed APK__
4. Wrap APK and mapping file to a binary directory. Make sure everything is consistent.
5. Add tags
    - git tag -a X.X.X -m “some commit”
    - git push origin X.X.X
    - more info: https://git-scm.com/book/en/v2/Git-Basics-Tagging
6. Go to Google Play, app releases to release.