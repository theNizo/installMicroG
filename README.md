written by Nizo aka. the_Nizo

How to install microG on Android Pie (9). Any other version has not been tested
===

## This tutorial aims to show how to get a minimum setup without location services and similar.
### DISCLAIMER: I am NOT responsible for bricked devices, thermonuclear war or for you getting fired because your alarm app failed. Period!

Most Google Apps should work, except Google Play Music or Hangouts. You can find the full List of incompatible Apps [here](https://github.com/microg/android_packages_apps_GmsCore/wiki/Problem-Apps)

## First:
* Get [F-Droid](https://f-droid.org/), or download the .apks from [the official site](https://microg.org/download.html). F-Droid is recommended, because you'll need to download some other stuff from there. I'll explain with F-Droid, but you can also get the required apps on another way if you want.
* Make sure signature spoofing is enabled. Some Custom-ROMs already support Signature Spoofing. I used HavocOS which has built-in Signature Spoofing.
	* Download Signature Spoofing Checker and start it. If it says enabled, you're good to go!
	* If it says disabled, install a patch. You can try [Needle](https://github.com/moosd/Needle), [haystack](https://github.com/Lanchon/haystack) or the [NanoDroid-Patcher](https://github.com/Nanolx/NanoDroid). I took NanoDroid, because you just need to flash a zip file, which you should already be familiar with. **Installing NanoDroid takes 10-15 minutes. Be patient.**

## Install
1. In F-Droid, go to Settings -> Repositories and add [microg.org/fdroid/repo](https://microg.org/fdroid/repo?fingerprint=9BD06727E62796C0130EB6DAB39B73157451582CBD138E86C468ACC395D14165) and activate it. Just copy&paste this link. It has the correct fingerprint within it.
2. Update Repositories.
3. Install:
	* **(needed)** GMScore
	* GsfProxy (if you need Google Cloud messaging. For me, it worked without that app installed)
	* **(needed)** PlayStore APK **(choose one)**
		* BlankStore, which is basically just a blank store.
		* FakeStore, which is basically a dummy.
		* You can also install the original PlayStore.apk, you can get it from [APKmirror](apkmirror.com). I haven't tested it.
	* UnifiedNlp (if you want location services. You will need a location and address lookup backend)
4. Open microG settings
	1. Allow missing permissions (you can still revoke them with XPrivacy or LineageOS's PrivacyGuard)
	2. Enable the Google Services you need (I didn't enable Google Cloud Messaging and didn't even install GsfProxy and it still worked.)
	3. Open Self-Check **(don't activate Battery Optimization yet)**
		* Try enabling everything under "Signature Spoofing support". Here is a known issue where you can't activate "System grants signature spoofing permission", please read the section (Known problems) below. Everything works when the first 4 marks in "Installed Packages" are set.
		* Make sure the Gsf and/or Location points are set, if you installed those features.
5. **Reboot**
6. Open microG settings again
	* Self-Check (**Enable Battery optimizations**)
### Done

## How can I access the Play Store?
* Aurora (based on Yalp)
* Yalp
* install an apk of the official PlayStore **(not tested)**

I recommend Aurora, as it's looking better than Yalp (or even PlayStore) and has one or two features more.

**Note:** Google might not like those apps. You're responsible if something happens to your Google Account. Happily no one has heard of a terminated account.

## Known Problems

Normally, when you click on "System grants signature spoofing permission" in Self-Check under "Sgnature spoofung support", you should get a Dialog where you need to allow the app to use that. I installed my ROM a couple of times and every time I got no dialog. But according to microG settings, everything has the correct signature. So everything's fine.
