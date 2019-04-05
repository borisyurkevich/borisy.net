---
layout: post
title:  "Running 1Password 7 in Stand-alone Vault Mode."
date:  2019-02-18T22:47+0000
---

### Be warned.

Having lived with this setup, I found out that I have to perform this steps every time the app is updated. I also have to disable Safari extension.

### 1Password 7 and local mode.

Although I'm paying for 1Password Family Subscription, I was experimenting with ways to run it locally. It wasn't obvious but I got it into stand-alone mode accidentally after restoring from backup.

It's easy with 1Password 6.

1. Buy the app.
2. Disable iCloud sync.
3. Create a local vault and use it.

With 1Password 7 subscription model you can download the app for free but in order to use it, you have to sign-in into your 1Password account. After that, you can create a vault outside of your cloud managed account but you'l still have a local copy of all of your 1Password account items. You can hide cloud vaults, but there's no obvious way to sign-out and stop 1Password 7 from fetching your data from the cloud.

### How to run 1Password 7 in local mode.

You will need a 1Password backup file. I have tested this with 1Password 7 and 6 backups.

1. Download 1Password 7 from [Mac App Store](https://itunes.apple.com/gb/app/1password-7-password-manager/id1333542190?mt=12) or [AgileBits website.](https://1password.com/downloads/mac/)
2. Sign-in into your 1Password account.
3. Open 1Password 7 > Preferences... > Advanced and enable local vaults.
4. Click File > Restore... > Find Backup.
5. Find it and click Add Backup.
6. Select a backup and click Restore.

This will prompt a warning that all your local data is going to be replaced. If you restore, 1Password quits itself and you will have only the vault from your backup. 1Password account is gone for good. You will have only 1 vault and it would look like you have signed out.

### Don't forget to backup.

1Password makes automatic backups but it's your duty to copy them to some place which is not your Mac. Time Machine can do it automatically.
