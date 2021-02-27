---
layout: post
title:  "iOS Proxy Switcher"
date:   2021-02-20 08:52:16 -0600
categories: ios iphone proxy
---

Switching your iOS proxy profile is, unfortunately, very tedious. The manual way to do this is to go to Settings -> Wi-Fi -> click the information icon on your Wi-Fi connection -> Configure Proxy (at the very bottom) -> Manual -> Type everything in. If you need to change any of that, you'll have to do it all again...

The solution I'm about to offer you is far from perfect, but it's much more automated and requires much less brain power than the manual way.

To do this, we are going to use [Shortcuts][wiki-shortcuts] to install and remove [profiles][apple-docs-profile] that will configure our proxy settings in a stream-lined way. This approach is inspired by [an AskDifferent answer by jcaron][ask-different-answer].

# Enable Supervised Mode

Unfortunately, for this to work, your device has to be [supervised][apple-docs-supervised] (WARNING: which requires factory resetting your phone 😥). Also, this requires access to a mac. What it doesn't require is Jailbreaking!

Before you begin, make sure to [diable Find My Phone][apple-docs-findmyphone] or this will fail.

I won't cover this portion in detail because it's already well-documented elsewhere. See [this article, for example][supervise-device]. But I will show some screenshots of enabling this.

In [Apple Configurator 2][apple-configurator], Right-click your device and choose Prepare. Choose similar options to the following:

![Manage device]({{site.baseurl}}/images/manage_device.png)

Choose "Do not enroll in MDM" on the next screen. 
Choose (or make and choose) an organization. This is just an arbitrary name.

Choose to show all steps on the next screen:

![Prepare]({{site.baseurl}}/images/prepare.png)

Click Prepare. It will likely tell you that you have to erase your phone to do this. Make a backup of your phone, if you have not already, and continue.

# Create the Enable Proxy Shortcut

Now for the fun stuff. The easiest way to create the Enable Proxy shortcut would be to download and modify my version here: [Enable Charles Proxy Shortcut][my-proxy].

The shortcut we're trying to create is shown below on the right:

![shortcuts]({{site.baseurl}}/images/shortcuts.png){: width="300px"}

Here are the steps in case you want to do it manually (This is all of them even though it's slightly cut off):

![proxy steps]({{site.baseurl}}/images/proxy-steps.jpg){: width="300px"}

# Configure Proxy Profile

For this to work, you need to make a [profile][apple-docs-profile] that configures the device's proxy settings. The following is my profile file that configures my iPhone to use [Charles Proxy][charles-proxy] as my device's proxy (which lets me snoop on my iPhone's network traffic):

<script src="https://gist.github.com/jmbeach/8a186134ccca23818e5b40d4f4f90247.js"></script>

You should be able to leave pretty much everything the same and just change the settings you care about (such as ProxyServer).

[charles-proxy]: https://www.charlesproxy.com/
[supervise-device]: https://support.jamfnow.com/s/article/207704656-Supervising-iOS-Devices-with-Apple-Configurator-2-5-or-Later
[wiki-shortcuts]: https://en.wikipedia.org/wiki/Shortcuts_(app)
[apple-docs-profile]: https://developer.apple.com/documentation/appstoreconnectapi/profiles
[apple-docs-supervised]: https://support.apple.com/guide/deployment-reference-ios/enabling-device-supervision-ior7ba06c270/web
[ask-different-answer]: https://apple.stackexchange.com/a/223926/57640
[apple-configurator]: https://support.apple.com/apple-configurator
[apple-docs-findmyphone]: https://support.apple.com/en-us/HT211149
[my-proxy]: https://www.icloud.com/shortcuts/b3027ef26e6144e880c0d48593ad9cbf