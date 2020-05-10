written by Nizo aka. the_Nizo

How to install microG on Android Pie (9) manually. Any other version has not been tested
===

## This tutorial aims to show how to get a minimum setup without location services and similar.
### DISCLAIMER: I am NOT responsible for bricked devices, thermonuclear war or for you getting fired because your alarm app failed. Period!

Most Google Apps should work, except Google Play Music or Hangouts. You can find the full List of incompatible Apps [here](https://github.com/microg/android_packages_apps_GmsCore/wiki/Problem-Apps)

## First:
This tutorial assumes that you've already installed a Custom ROM that doesn't have microG bundled, like LineageOS for microG. It also assumes that you have root access.

* Get [F-Droid](https://f-droid.org/), or download the .apks from [the official site](https://microg.org/download.html). F-Droid is recommended, because you'll need to download some other stuff from there. I'll explain with F-Droid, but you can also get the required apps on another way if you want.
* Make sure Signature Spoofing is enabled. Some Custom-ROMs already support Signature Spoofing. If your ROM doesn't have Signature Spoofing support, you can flash a patch, however I recommend against it, because NanoDroid automatically grants Signature spoofing to every app that wants to.
	* Download Signature Spoofing Checker and start it. If it says enabled, you're good to go!
	* If it says disabled, you can install a patch. You can try [Needle](https://github.com/moosd/Needle), [haystack](https://github.com/Lanchon/haystack) or the [NanoDroid-Patcher](https://github.com/Nanolx/NanoDroid). I took NanoDroid, because you just need to flash a zip file, which you should already be familiar with. **Installing NanoDroid takes 10-15 minutes. Be patient.**

## Install
For an simple tutorial, see "My way".
1. In F-Droid, go to Settings -> Repositories and add [microg.org/fdroid/repo](https://microg.org/fdroid/repo?fingerprint=9BD06727E62796C0130EB6DAB39B73157451582CBD138E86C468ACC395D14165) and activate it. Just copy&paste this link. It has the correct fingerprint within it.
2. Update Repositories.
3. Install:
	* **(needed)** GMScore
	* GsfProxy (if you need Google Cloud messaging. For me, it worked without that app installed)
	* **(needed)** PlayStore APK **(choose one)**
		* BlankStore, which is basically just a blank store.
		* FakeStore, which is basically a dummy.
		* You can also install the original PlayStore.apk, you can get it from [APKmirror](apkmirror.com). I haven't tested it.
	* UnifiedNlp (if you want location services. You will need a location and address lookup backend. Some apps, like OSMand (OpenStreetMaps client) work without it.)
4. Open microG settings
	1. Allow missing permissions (you can still revoke them with XPrivacy or LineageOS's PrivacyGuard)
	2. Enable the Google Services you need (You don't even have to check any)
	3. Open Self-Check **(don't activate Battery Optimization yet)**
		* Try enabling everything under "Signature Spoofing support". Here is a known issue where you can't activate "System grants Signature Spoofing permission", please read the section (Known problems) below. Everything works when the first 4 marks in "Installed Packages" are set.
		* Make sure the GSF and/or Location checkboxes are set, if you installed those features.
5. **Reboot**
6. Open microG settings again
	* Self-Check (**Enable Battery optimizations**)
### Done

8. Additional: Install the Framework Proxy. I don't really know if it does something besides the checkmark in the microG settings, but you're free to do it.

## How can I access the Play Store?
* Aurora Store (based on Yalp)
* Yalp
* install an apk of the official PlayStore **(not tested)**

I recommend Aurora, as it's looking better than Yalp (or even PlayStore) and has more features. It also has an anonymous account that you can log into. There's a privileged extension (install apps without having to accept them in the package installer) that you can get [here](https://gitlab.com/AuroraOSS/AuroraServices).

**Note:** Google might not like those apps. You're responsible if something happens to your Google Account. Happily no one has heard of a terminated account.

## My way (pretty straightforward and easy to understand)
You can get every app you need to install from F-Droid. This is what we're going to do.
1. Install Signature Spoofing Checker from F-Droid and run it
2. If it says disabled, flash [NanoDroid-Patcher](https://github.com/Nanolx/NanoDroid) (again, it takes 10-15min)
3. Add the repo [microg.org/fdroid/repo](https://microg.org/fdroid/repo?fingerprint=9BD06727E62796C0130EB6DAB39B73157451582CBD138E86C468ACC395D14165) to F-Droid
4. Update Repositories
5. Install MicroG Services Core (gms)
6. Install FakeStore
7. Open microG settings **(don't enable optimize battery yet)**
	1. Allow missing permissions
	2. In Self-Check, try to enable as much points under "Signature Spoofing support" as possible.
	3. If "System spoofs signature" and the two "has correct signature" points in "installed packages" are checked, everthing's fine
8. Reboot
9. microG settings -> Self-Check -> enable "Battery Optimization"
9. Install Aurora Store
10. **Done**

## Known Problems

### Nothing happens when I click on "System grants Signature Spoofing permission"
Normally, when you click on "System grants Signature Spoofing permission" in Self-Check under "Signature Spoofing support", you should get a Dialog where you need to allow the app to use that. I installed my ROM a couple of times and every time I got no dialog. But according to microG settings, everything has the correct signature. So everything's fine.

EDIT: I didn't know that my ROM had an option to enable Signature Spoofing. I flashed NanoDroid, which gives any app Signature Spoofing that wants it, that's why this scenario happened.

### My SmartWatch can't finish setup
Yes, and **I** don't know how to fix it. I don't own a smartwatch.

### Phonesky and NanoDroid
Pointed out by a [Reddit user](https://www.reddit.com/r/MicroG/comments/gfszih/found_an_error_in_the_wiki/fpvl7rq/), if you use NanoDroid, you have to use the following command for Phonesky to spoof signature:

`pm grant com.android.vending android.permission.FAKE_PACKAGE_SIGNATURE`

If you want to do it via adb, put `adb shell` in front.

#### Why does it happen?

To quote [TestsubjectNr1](https://www.reddit.com/user/TestsubjectNr1):

"... it isn't being prompted to. Nor does it show up as an app in the section
 where you can see what apps have spoofing rights (and give the rights 
to apps manually)."

His problem was on CarbonRom.
