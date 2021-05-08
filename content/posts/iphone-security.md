---
title: Activist iPhone Security Guide
date: 2021-03-13
tags:
- security
- activism
- tech
---

{{< figure src="/phones.png" caption="Three protesters hold their phones up above a crowd." >}}

*(as of iOS 12)*

When you attend a protest, particularly one which which might garner the attention of the authorities, it's a good practice to limit the amount of data being sent out by your phone as much as possible. To start, here are things you should have set up in your phone at all times:

1. **Limit ad tracking:** open the `Settings` app; `Privacy`; scroll down to the bottom of the Privacy settings; `Advertising`; toggle ON `Limit Ad Tracking` (you can also hit `Reset Advertising Identifier` every once in a while)
2. **Block analytics tracking:** `Settings` app; `Privacy`; scroll down to the bottom of the Privacy settings; `Analytics & Improvements`; toggle OFF `Share iPhone Analytics`,`Improve Sire & Dictation`, and `Share iCloud Analytics`
3. **Block location-based analytics:** `Settings` app; `Privacy`; `Location Services`; `System Services`; toggle OFF `iPhone Analytics`, `Popular Near Me`, and `Routing & Traffic` (also feel free to toggle OFF as many of the things in this list and the `Location Services` app list as you feel comfortable with)
4. **Change your iPhone name**: `Settings` app; `General`; `About`; `Name`; change to something that provides no identifying information (including names, iPhone model, phone number, etc.)
5. **Use a strong passcode:** `Settings` app; `Touch ID & Passcode`; `Change Passcode` (I recommend [using a strong passphrase](https://www.useapassphrase.com/) as your passcode to ensure that it is memorable but resistant to brute force attacks. You passcode should be alphanumeric at *least* 10 digits long)
6. **Turn off Siri:** `Settings` app; `Siri & Search`; toggle OFF all options
7. **Turn off dictation:** `Settings` app; `General`; `Keyboards`; toggle OFF `Enable Dictation`
8. **Turn off background app refresh for most apps:** `Settings` app; `General`; `Background App Refresh`; toggle OFF all apps that are not secure/necessary
9. **Turn off Game Center's location access:** `Settings` app; `Game Center`; toggle OFF `Game Center`, or at least toggle OFF `Nearby Players`
10. **Audit your apps' access:** `Settings` app; `Privacy`; check through this list and ensure that apps have no more access to your data than they need
11. **Harden  the default Safari browser:** `Settings` app; `Safari`; set `Search Engine` to `DuckDuckGo`, toggle OFF `Search Engine Suggestions`, `Safari Suggestions`, `Preload Top Hit`, and `Frequently Visited Sites`; toggle ON `Block Pop-ups`, `Prevent Cross-Site Tracking`, `Block All Cookies`, and `Fraudulent Website Warning`; toggle OFF `Camera & Microphone Access` and `Check for Apple Pay`; select `Advanced`; toggle OFF `Javascript`
12. **Limit your message storage to 30 days:** `Settings` app; `Messages`; select `Keep Messages` and choose `30 Days`

You should also keep your phone updated at all times (check in the `Settings` app; `General`; `Software Update`)

Before you head out to a protest, do the following:

1. **Back up your phone:** `Settings` app; your name at the top; `iCloud`; `iCloud Backup`; toggle it ON if not on already; select `Back Up Now`
2. **Turn on Low Power Mode:** `Settings` app; `Battery`; toggle ON `Low Power Mode`
3. **Turn off Touch ID and access to phone functions while locked:** `Settings` app; `Touch ID & Passcode`; type passcode; toggle `iPhone Unlock` to OFF (you can be coerced into putting your thumb on your phone); set `Require Passcode` to `Immediately`; toggle `Voice Dial` OFF; toggle all options under `Allow access while locked` to OFF; at the bottom, toggle ON wiping your phone after 10 failed attempts
4. **Set a quicker auto-lock:** `Settings` app; `Display & Brightness`; `Auto-Lock`; `30 seconds`
5. **Turn off methods for connecting to your device:** open the `Settings` app; `General`; set `Airdrop` to `Receiving off`; set `Handoff` to OFF
6. **Turn off Wi-Fi**: `Settings` app; `Wi-Fi`; toggle OFF
7. **Turn off your GPS:** `Settings` app; `Privacy`; `Location Services`; toggle OFF at the top - if you cannot to this, then at least turn it off for most apps and toggle OFF `Share My Location`
8. **Turn off fitness tracking:** `Settings` app; `Privacy`; `Motion & Fitness`; toggle OFF `Fitness Tracking`
9. **Turn off Bluetooth:** `Settings` app; `Bluetooth`; set to OFF (unless you need it for what you are doing)
10. **Turn off notification previews**: `Settings` app; `Notifications`; `Show Previews`; select `Never`; then go through each app in the list and toggle OFF `Show on Lock Screen`
11. **Turn off automatic (non-encrypted) SMS messages:** `Settings` app; `Messages`; toggle `Send as SMS` OFF (*note*: this doesn't completely turn off SMS, so you'll still need to use [Signal](https://signal.org/))

Keep in mind that turning off your phone is an option, as is turning it to airplane mode, or even leaving it at home - but communication is key when you are out on the streets, so I don't recommend it.

While you are out and about, use [Signal](https://signal.org/) for your communications and [Firefox Focus](https://apps.apple.com/us/app/firefox-focus-privacy-browser/id1055677337) or [Brave](https://apps.apple.com/us/app/brave-private-web-browser-vpn/id1052879175) for browsing. I recommend using [ProtonVPN](https://apps.apple.com/us/app/protonvpn-fast-secure-vpn/id1437005085) on a regular basis. Another good idea is to download maps onto your phone ahead of time so that you don't need to use location services on your GPS/maps app. 

When livestreaming, avoid showing fellow protesters' faces, particularly if they are doing something that would garner the authorities' attention. If you post videos or photos afterward, make sure to blur out faces and potentially identifying details of fellow activists.

Missing something? [Let me know](https://natehn.com/connect/). I'll be following up soon with [an article on digital security more generally](https://natehn.com/posts/digital-security/).
