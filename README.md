Continuity Activation Tool
==========================

This tool makes the necessary changes to enable OS X 10.10 Continuity features on compatible hardware. Continuity features activated by this tool include Handoff, Instant Hotspot, and New Airdrop. 

## News - 2014.12.14

**Continuity Activation Tool 2.0 released** : Adds compatibility with Bluetooth 4.0 USB dongles, allowing many Macs from 2008 and later to easily upgrade to Continuity. See the chart below to verify available upgrade options. 

**[Download link](https://github.com/dokterdok/Continuity-Activation-Tool/archive/master.zip)**

This tool took a lot of research and coding. A small PayPal donation would be much appreciated to support the maintenance and evolution of the app. Thanks! [![Donate](https://www.paypalobjects.com/webstatic/en_US/btn/btn_donate_92x26.png)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=dokterdok%40gmail%2ecom&lc=CH&item_name=Continuity%20Activation%20Tool&currency_code=USD&bn=PP%2dDonationsBF%3abtn_donate_LG%2egif%3aNonHosted)

## Features
* Activate Continuity: Does a Continuity compatibility check, makes a backup of the Systems kexts before and after patching, applies patches relevant to the current configuration.
* System Diagnostic: Produces a report of the current system parameters influencing Continuity.
* Uninstall: Rolls back any changes applied by the tool. It firsts looks for previous backups made with the tool, and if it can't find any, kexts from the OS X Recovery Disk are reinstalled. It will only reactivate OS kext signature protection if it is sure that all system kexts installed are signed and valid, to prevent potential boot time issues with 3rd party tools or hardware.

## Warning
* You should exercise caution when using the Continuity Activation Tool, as it moves around low level files and there's a possibility it could cause problems. Using this tool is at your own risk. Always use the latest version of the tool to avoid issues.
* The tool disables the verification of original Apple drivers in order to work, which lowers the overall system security.

## Compatibility list
Your Mac might require a hardware upgrade to be able to work with Continuity. See the chart below to understand what your Mac supports, and use the System Diagnostic feature of the Continuity Activation Tool for a compatibility check of your Mac.

![Compatibility Chart](https://github.com/dokterdok/Continuity-Activation-Tool/blob/beta/CompatibilityChart-13.12.2014.png)

**Chart data sources**: Feedback from >150 CAT 2.0 beta testers, feedback reported on this GitHub site, UncleSchnitty's [guide](http://forums.macrumors.com/showpost.php?p=20124161).

**Pros of using USB BT4.0 dongles**: low cost, easy to install, easy to find on the market

**Pros of using AirPort Extreme cards**: authentic Apple hardware, better support for Continuity features, doesn't occupy a USB slot

### Bluetooth 4.0 USB dongles
A few important notes about using CAT with USB Bluetooth 4.0 dongles:
* Bluetooth 4.0 dongles based on the Cambridge Silicon Radio CSR8510 A10 chip (e.g. Inatek Nano) are not compatible with CAT.
* The recommendation is to look for dongles based on the Broadcom BCM20702 chip, which are similar to the ones used by Apple in their Continuity compatible Macs. A few examples: Asus BT400, IOGEAR GBU521, GMYLE, and many others. Compatibility with CSR dongles is not guaranteed.
* Instant Hotspot currently doesn't work reliably when using a dongle. This is a known issue, no workarounds have been identified yet.
* Atheros Wi-Fi AirPort cards will prevent Continuity from working even when adding a Bluetooth 4.0 dongle. The System Diagnostic feature of CAT tells which Wi-Fi brand is active. There are no workarounds and no patch is expected to change this, an AirPort card upgrade is required.

### AirPort Extreme card upgrades

The table below is based on this [guide (forum thread)](http://forums.macrumors.com/showpost.php?p=20124161). If you notice inaccuracies, please report them to the guide author and open an issue.

Mac Model | Hardware change required | Software patch required (e.g. via this tool)
:---|:---|:---
MacBook Air late 2010 | Yes, new wireless card BCM94360CS2, see [here](https://github.com/dokterdok/Continuity-Activation-Tool/issues/41#issuecomment-66827305) | No
MacBook Air mid 2011 | No | Yes
MacBook Air 2012-2014 | No (works OTB) | No (works OTB)
MacBook Pro early 2008 (15" only) | Yes, new wireless card BCM94360CD + adapter | Yes
MacBook Pro mid 2010 (15" only) | Yes, new wireless card BCM94331PCIEBT4CAX, see [guide](http://forums.macrumors.com/showpost.php?p=20269421&postcount=639) | Yes
MacBook Pro early 2011 to late 2011 (all models) | Yes, new wireless card BCM94331PCIEBT4CAX | Yes
MacBook Pro mid 2012 (non-retina) | No (works OTB)| No (works OTB)
MacBook Pro Retina (all models) | No (works OTB) | No (works OTB)
Mac mini mid 2011 | No | Yes
Mac mini 2012-2014 | No (works OTB) | No (works OTB)
Mac Pro early 2008-2012 | Yes, new wireless card BCM94360CD + adapter | No
Mac Pro 2013-2014 | No (works OTB) | No (works OTB)
iMac 2007-2011 | Yes, new wireless card BCM94360CD + adapter | No
iMac 2012-2014 | No (works OTB) | No (works OTB)

## How to use it

**From Finder**

1. Download the zip (link on the right) and extract it.
2. Double-click on the app.
3. Follow instructions on the screen. Ignore or deny any "Access to accessibility features" prompt.

**From the command line**

Script location: ```Continuity Activation Tool.app/Contents/Resources/contitool.sh```

Usage: ```contitool.sh -a | -d | -f | -h | -r | -z```

Options:
```
-a               run the compatibility checks and activation procedure
-d               run the system diagnostic procedure and quit
-f               force the activation procedure without compatibility checks
-h               display a help message and quit
-r               uninstall Continuity mods by directly using OS X recovery disk files
-z               uninstall Continuity mods
```

### Sources
* [Get help using Continuity with iOS 8 and OS X (Apple Support KB)](http://support.apple.com/kb/TS5458)
* [Guide to enable Continuity manually (MacRumors Forum Thread)](http://forums.macrumors.com/showpost.php?p=20124161)
* [Article on the disabling OS security features and related risks (Cindori.org)](http://www.cindori.org/trim-enabler-and-yosemite)

### Changelog

**v.2.0.0 - 2014.12.14**
* Added compatibility with many older Macs when using a USB Bluetooth 4.0 dongle (see chart).
* Added the ability to choose the admin user executing the tool ([#14](https://github.com/dokterdok/Continuity-Activation-Tool/issues/14))
* Added new diagnostics, including a system wide Continuity activation check.
* Added the ability to run the System Diagnostic from the command line without admin privileges.
* Improved the command line execution with new options.
* Improved the diagnostic messages accuracy.
* Fixed Gatekeeper issues preventing the app to be launched, by codesigning the app
* Fixed an issue where OS X kext protection wasn’t disabled is some cases, leading to a loss of Wi-Fi / Bluetooth connectivity.
* Optimisations and bug fixes.

**v.1.1.2 - 2014.11.16**
* Improved uninstallation reliability. It fixes a bug where the uninstaller could in some cases re-activate OS kext signature protection even if unsigned kexts are installed. Trim Enabler users should not use the uninstallation feature from prior versions to avoid risks of issues at boot-time.

**v.1.1.1 - 2014.11.12**
* Further improved reliability with systems that can't find utilities due to an irregular PATH ([#9](https://github.com/dokterdok/Continuity-Activation-Tool/issues/9))

**v.1.1.0 - 2014.11.11**

* **New uninstallation feature**: new option to rollback all system changes applied by the tool. It firsts looks for previous backups made with the tool, and if it can't find any, kexts from the OS X Recovery Disk are used. It will only reactivate OS kext signature protection if it is sure that all system kexts installed are signed. The uninstallation can be also be called from the command line. ([#15](https://github.com/dokterdok/Continuity-Activation-Tool/issues/15), [#21](https://github.com/dokterdok/Continuity-Activation-Tool/issues/21), [#36](https://github.com/dokterdok/Continuity-Activation-Tool/issues/36), [#40](https://github.com/dokterdok/Continuity-Activation-Tool/issues/40), [#45](https://github.com/dokterdok/Continuity-Activation-Tool/issues/45))
* **Speed improvements**: activating Continuity is now twice as fast compared to the last version: only 1 reboot at the end and 1 permissions repair are necessary.
* **Reliability improvements:**
* The diagnostic no longer applies boot-args changes ([#1](https://github.com/dokterdok/Continuity-Activation-Tool/issues/1))
* Fewer risks of issues with systems that use third party utilities ([#9](https://github.com/dokterdok/Continuity-Activation-Tool/issues/9))
* Activation will now abort if 1 of the two mandatory kexts are missing
* Incorrect or inaccurate messages
* Many other small optimizations


**v.1.0.2 - 2014.10.27**

* Fixed a bug that prevented Handoff to be enabled in the System Preferences, even after a successful patch ([#21](https://github.com/dokterdok/Continuity-Activation-Tool/issues/21), [#22](https://github.com/dokterdok/Continuity-Activation-Tool/issues/22), [#31](https://github.com/dokterdok/Continuity-Activation-Tool/issues/31))
* Added a backup step for freshly patched drivers, potentially useful if a future OS X update disables the patching methods ([#16](https://github.com/dokterdok/Continuity-Activation-Tool/issues/16))
* Added a prompt in case existing backups are found, asking whether to overwrite the files or skip. Previous behavior was to silently overwrite.
* Removed the 13" MacBook Pro 2010 from the compatibility list ([#28](https://github.com/dokterdok/Continuity-Activation-Tool/issues/28), pull [#29](https://github.com/dokterdok/Continuity-Activation-Tool/pull/29))
* Minor optimisations


**v.1.0.1 -  2014.10.24**

* Fixed a boot arguments overwriting bug, that could lead to a system failure in specific cases ([#1](https://github.com/dokterdok/Continuity-Activation-Tool/issues/1), [#15](https://github.com/dokterdok/Continuity-Activation-Tool/issues/15))
* Fixed a kext-dev-mode bug that prevented the OS to disable its drivers protection
* Fixed the strings utility presence check when the script is run from the command line
* Added a disk reparation step at the start of the patching procedure, lowering failure risks on disks with permissions issues
* Added a verification that sudo is still active before patching

**v.1.0.0 - 2014.10.23**

* Initial release

### Thanks
* To the >150 CAT 2.0 beta testers
* Skvo
* toleda
* Lem3ssie (LAUTRU Mehdi)
* UncleSchnitty
* TealShark
* Manic Harmonic
* rob3r7o
