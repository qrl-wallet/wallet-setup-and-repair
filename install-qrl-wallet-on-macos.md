![QRL article banner](assets/banner-article.png)

# Install QRL Wallet on macOS

**Short answer.** The release publishes one macOS disk image. Download it, open it, move the application to your Applications folder, check the hash, and clear Gatekeeper's challenge once. The wallet then writes its keys locally and syncs with the network.

## One disk image, not a per-chip choice

The release carries a single macOS asset rather than a separate file for each processor, so there is no build to choose between and no architecture to match. That removes the mistake most people expect to make: there is nothing to get wrong at download time.

What remains is the file itself. Take the disk image from the project's GitHub releases page, as [Download the Official QRL Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/download-the-official-qrl-wallet.md) describes, and check its hash before you open it. The download is large, so a truncated copy is a real possibility on a slow connection, and a truncated disk image mounts badly or refuses to mount at all.

If a page offers you a macOS build from anywhere other than the release page, treat it as a different file. There is no published digest for it, which means there is nothing to compare.

## Opening the disk image

Double-clicking mounts the image, and a Finder window appears with the application inside.

Drag the application to Applications, then eject the mounted image. Running it from inside the mounted image works once and then fails after a restart, which is why the move matters.

Nothing installs a service, a helper or a login item. The application lives in Applications, its data lives in your user library, and removing the application leaves the wallet file alone.

That separation is the thing to remember at backup time. Copying the application does not copy your keys, and deleting the application does not delete them. The wallet file and the mnemonic are the backup.

## Gatekeeper and the first launch

macOS will refuse to launch an application it cannot identify the developer of, and the dialog offers to move it to the bin. That refusal is a policy check, not a scan result, and it appears for any build that is not notarised under an identified developer account.

Verify first. Compare the hash of the downloaded asset with the value the project publishes for that asset; [Verify the QRL Installer](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/verify-the-qrl-installer.md) gives the command. Once the hash matches, you know the file is the one the project published, and the remaining step is to allow it.

Use the Open command from the context menu, or the Privacy and Security panel's allow button, rather than disabling Gatekeeper system-wide. The single-application override is reversible and keeps the protection in place for everything else.

What you should not do is remove quarantine attributes from a file you have not verified, or add a blanket exception for a whole folder. Both turn a policy check into a habit of ignoring it.

## First launch and sync

On first launch the wallet connects to QRL nodes and catches up with the chain. That is a real download and it takes time, especially on a fresh machine with no cached data.

Progress is visible in the window. If it stalls at zero, the wallet is not reaching a node, and the connection checks described in [QRL Wallet Not Syncing Fix](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/qrl-wallet-not-syncing-fix.md) apply exactly as they do on other platforms.

When sync completes, create an address. No account is needed, no email address is requested, and nothing is registered anywhere. The wallet asks for a password, writes a wallet file, and shows an address beginning with Q.

Before funding it, back up the mnemonic offline and store the wallet file with its password. The mnemonic is the only recovery path if the machine is lost, and it is the one thing an attacker needs.

## If it will not open

Three failures account for most reports, and the first two are the ones to rule out before you suspect the build. A disk image that did not finish downloading, which mounts with an error or not at all. A bundle run from the mounted image rather than from Applications, which works once and then stops. And a Gatekeeper block that was dismissed once but not cleared in Privacy and Security.

Work through them in that order and re-check the hash before assuming the application is faulty. If it opens and the window stays empty, the problem has moved from installation to networking, and the sync page is the next read.

If you migrated from an older Mac and the wallet opens with an empty address list, you may have launched without your wallet file. Restoring the file, not reinstalling the application, is the fix.

## After the install

Keep the application in Applications and update by replacing the bundle when a new release appears. Keep the wallet file in a location your backup covers, and keep the mnemonic out of any backup that reaches the internet.

If you have not decided between the desktop client and a browser wallet, [QRL Desktop Wallet vs Web Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/qrl-desktop-vs-web-wallet.md) compares where keys live in each. If the next question is where to start, [Create Your First QRL Address](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/create-your-first-qrl-address.md) walks through the first address and its backup.

Linux users follow the same logic with a different container, and [Run QRL Wallet on Linux](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/run-qrl-wallet-on-linux.md) covers that path.

## FAQ

### Which build do I need on an M-series Mac?

The same one everybody else downloads. The release publishes a single macOS disk image rather than one file per chip, so there is no separate build to pick.

### Why does macOS say the application cannot be opened?

Because it is not notarised under an identified developer account, which applies to many open-source builds. Verify the hash, then allow that one application in Privacy and Security.

### Is dragging to Applications an installation?

Practically, yes. It places the bundle where macOS expects applications to live, and it avoids running from a mounted image that disappears at restart.

### Does the Mac build hold my keys differently?

No. Keys live in a local wallet file you control, exactly as on Windows and Linux. The platform changes the packaging, not the key model.

<!-- answers: none -->
