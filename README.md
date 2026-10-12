# Fix Universal Clipboard between iPhone and Mac

Use these steps when text copied on your iPhone will not paste on your Mac. Test after each step and stop when it works.

## 1. Check the basics

- Keep both devices nearby, with Wi-Fi and Bluetooth on.
- Use the same Apple Account on both devices and enable Handoff.
- Copy a fresh sentence in iPhone Notes and immediately paste it into Mac TextEdit. Test the reverse direction too.

## 2. Refresh Handoff on the affected iPhone

1. Open **Settings → General → AirPlay & Continuity** (or **AirPlay & Handoff**).
2. Turn **Handoff off**.
3. Restart the iPhone.
4. Turn **Handoff on** and test again.

If another iPhone already works both ways with your Mac, start here with the affected phone.

## 3. If it still fails, restart the Mac

Save your work, restart normally, and test with freshly copied text. Check Software Update on both devices for available fixes.

## 4. Optional: check the Mac setting we found disabled

Open **Terminal** on the Mac and run:

```sh
defaults read com.apple.coreservices.useractivityd ClipboardSharingEnabled
```

- **`1`:** Sharing is enabled; leave this setting alone.
- **`0`:** Run the two commands below to enable it and restart Handoff.
- **“Does not exist” or “not found”:** This does not mean it is disabled; skip the commands below.

```sh
defaults write com.apple.coreservices.useractivityd ClipboardSharingEnabled -bool true
killall useractivityd
```

Copy fresh text and test again. This is the targeted preference change used in our case, not an Apple-documented universal fix.

## What worked in our case

We enabled the Mac setting and restarted its Handoff, clipboard, and sharing services. The final success report followed the iPhone 17 Handoff refresh instructions. Copying then worked both ways across the Mac, iPhone 17, and iPhone 13—without formatting. We could not isolate a single cause or guarantee it would never recur.

If these steps fail, contact Apple Support with the failing transfer direction and both software versions before considering an erase.

[Apple’s Universal Clipboard guidance](https://support.apple.com/en-us/102430)
