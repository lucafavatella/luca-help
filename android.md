## Store-less apps

[Store-less logcat reader](https://f-droid.org/en/packages/com.dp.logcatapp/) (on [root-less 4.1+](https://android.stackexchange.com/questions/157/does-access-to-logcat-need-root/7260#7260): `adb shell pm grant com.dp.logcatapp android.permission.READ_LOGS` [undocumented whether surviving reboots/upgrades](https://developer.android.com/studio/command-line/adb#pm))

[Store-less Viber](https://download.viber.com/viber.apk) (looks like old version)

[Store-less Signal](https://signal.org/android/apk/) ([ref](https://whispersystems.discoursehosting.net/t/how-to-get-signal-apks-outside-of-the-google-play-store/808))

[Stripped-out Store-less maps.me](https://f-droid.org/en/packages/com.github.axet.maps/) (slightly out-of-date), [Store-less maps.me](https://maps.me/apk/).

## Known Android issues

### DownloadManager not working in Android 7 with VPN

[DownloadManager does not work in Nougat with VPN running (Oct 2016)](https://github.com/julian-klode/dns66/issues/31#issuecomment-256695500) (Android 7.*).

## Misc notes re [DNS66](https://f-droid.org/en/packages/org.jak_linux.dns66/), [NetGuard](https://f-droid.org/en/packages/eu.faircode.netguard/), [AFWall+](https://f-droid.org/en/packages/dev.ukanth.ufirewall/)

DNS66 blocks per-app DNS resolution - [not per-add Internet access as that would make it analogous to a per-app Internet blocking firewall app e.g. NetGuard: con is ineffectiveness with hardcoded IP, pro is lower battery usage (Oct 2016)](https://github.com/julian-klode/dns66/issues/30#issuecomment-256664179).

Some [non-Google](https://github.com/julian-klode/dns66/issues/125#issuecomment-379421006) system apps are indirectly responsible for ads serving - e.g. ["Android System WebView" and "HTML Viewer" (Oct 2017)](https://github.com/julian-klode/dns66/issues/125#issuecomment-335353015).
