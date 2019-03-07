# Navigation Bar Show/Hide

Android has a boolean for showing navigation bar or not. In ``frameworks/base/services/core/java/com/android/server/policy/PhoneWindowManager.java`` from AOSP, ``mHasNavigationBar`` got config from `com.android.internal.R.bool.config_showNavigationBar` and can be overwrited by property `qemu.hw.mainkeys`.

In the past, all tours tells people using ``qemu.hw.mainkeys`` to show/hide navbar, but I found that some apps/games will not hide the bar while in fullscreen mode. So I think using this way is better. 

This overlay will overwrite ``config_showNavigationBar`` from framework.

## Instructions
- Installer will detect if your device has navbar or not. If you has that then it will install the hidden one.
- The detect script can be found [here](https://gist.github.com/null4n/dd52b2890b60ddbb315de158cc72ef5e).
- I only test in 8.0/8.1, but RRO should work after 7.0.
- If it didn't effect, that means your rom didn't support it or it add a whitelist for overlay apps.
- If you want to disable hardware key (HOME, BACK, APP_SWITCH), copy your keylayout config from ``/vendor/usr/keylayout`` to ``$MODDIR/system/vendor/usr/keylayout`` and delete the line has `HOME`, `BACK`, `APP_SWITCH`.

## Changelog
- R1: Remove ``qemu.hw.mainkeys`` if OEM used it.
- R2: fix detect script.
- R3: fix cert issue.
