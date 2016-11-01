Headless Android Device (Based on branch: android-7.0.0_r5)
====================================================================

Previous versions of Android had the prop/option for running without display 
(headless). But since JellyBean (e63f6f7c8d0094bdea3fe031a178490b273162cd) 
this prop is obsolete.

So inspired from commit e63f6f7c8d0094bdea3fe031a178490b273162cd and according
to the new android version, this is intended to be non-production ready headless
android.


Side effects:
No SurfaceFlinger process
No InputReader service
Modified WindowManagerService
Graphics allocations changed to not use vendors gralloc/hwcomposer

Pros:
Useful for no-display-devices (Embedded devices, bringing up boards and so on)
Services, Brodcast receivers, Providers are still working properly

Cons:
Can't run activities in apps

Tested on Nexus 6P (angler) (android-7.0.0_r5)

You should define:

setprop ro.config.headless 1

in [system|default].prop or in some .rc file

References:
https://events.linuxfoundation.org/images/stories/pdf/lf_abs12_yaghmour_headless.pdf
http://elinux.org/images/7/7d/Headless_android_strikes_back--gbisson.pdf
https://github.com/gibsson/headless-android
