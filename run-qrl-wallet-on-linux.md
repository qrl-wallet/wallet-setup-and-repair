![QRL article banner](assets/banner-article.png)

# Run QRL Wallet on Linux

**Short answer.** The Linux release is a zip archive holding two packages: a `.deb` for Debian-based distributions and a `.pacman` package for Arch-based ones. Extract the archive, install the package your distribution uses, verify the file first, and the wallet writes its keys to your home directory on first run.

## What the Linux download contains

The release publishes one Linux asset, and it is an archive rather than a package. Extracting it gives you a `.deb` and a `.pacman` file, which are two packagings of the same build. You install one of them; the other is not needed and can be deleted.

That is worth knowing before you start, because the file you download is not the thing you install. Hashing the archive proves the download arrived intact; installing a package out of it is a second step, and the two are easy to confuse if you have only used distributions that ship a single package per download.

Take the archive from the project's GitHub releases page rather than from a mirror or a search advertisement. [Download the Official QRL Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/download-the-official-qrl-wallet.md) covers which release is current and why the releases page is the only place where the file and its hash come from the same source.

## Choosing the package

Debian, Ubuntu and their derivatives use the `.deb`. Arch and its derivatives use the `.pacman` package. If your distribution uses neither, a source build is the route, and it is covered below.

The release does not split Linux by processor architecture, so there is no arm64 file to look for and no 32-bit build to worry about. The archive you download is the one the project publishes, and the choice is the package format rather than a filename suffix.

Extract the archive somewhere you can find again, and install from there rather than running anything directly out of the compressed file.

## Installing the deb

Install with your package manager so that dependencies are resolved, rather than unpacking the package by hand. `sudo apt install ./` followed by the file you extracted handles a local package and pulls in what it declares.

A graphical package manager does the same job if you prefer one. What matters is that the package is installed rather than extracted somewhere and run from there.

Verify first. Compute the hash of the archive and compare it with the value published for it before you install anything; [Verify the QRL Installer](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/verify-the-qrl-installer.md) gives the command and explains what a mismatch means. Installing an unverified package with administrator rights is the one mistake in this flow that reaches beyond your user account.

Do not work around a dependency error by forcing the install. A package that will not resolve its dependencies is telling you something about the system it is being installed on, and the wallet needs those libraries to start.

## Installing the pacman package

Arch-based systems install a local package with `sudo pacman -U` followed by the extracted `.pacman` file. The same rules apply: verify the archive first, read the output rather than scrolling past it, and do not force an install over a dependency complaint.

The package installs the application and leaves your wallet data in your home directory. Replacing it with a newer release does not touch that data, which is the property worth knowing before an update.

If your system is a derivative with its own package tooling, use that tooling for a local file. The format is what matters, not the command name.

## First run and where the wallet file lives

Launching the wallet begins a chain download. That takes time on a fresh machine and is not a hang unless the progress indicator never moves at all.

When sync finishes, create an address. No account and no email address are involved: the wallet asks for a password, writes a wallet file, and shows an address beginning with Q.

On Linux the wallet file sits in a hidden directory in your home folder. That has two consequences worth planning for. It is easy to miss when you build a backup by clicking through visible folders, and it is easy to include by accident in a folder that syncs to a cloud service.

Decide which of those you want before the address holds anything. A backup that reaches your own storage is useful; one that reaches a service you would not trust with the file is a copy you no longer control.

If the wallet starts but never syncs, the fault is in the network path rather than the install. [Fix QRL Wallet Connection Error](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/fix-qrl-wallet-connection-error.md) covers node settings, ports, proxies and VPNs, and it applies to Linux exactly as it does elsewhere.

## No AppImage in this release

Readers arrive expecting an AppImage, because older material describes one and the format is common for Linux desktop applications. The current release does not ship one: the Linux asset is an archive containing a `.deb` and a `.pacman`.

An AppImage has been requested, and the request is visible in the project's issue tracker. A request is not an asset, and a page that offers you an AppImage for the current version is either describing an older release or not describing this one.

If you find a single-file build elsewhere, treat it as unverified by definition: there is no published digest for a file the project did not upload. The archive from the releases page, checked against its published value, is the route the project supports.

## Building from source instead

The wallet is MIT-licensed and the source is public, so building it is a legitimate route on a distribution that uses neither package format. [QRL Wallet Source Code and Licence](https://github.com/qrl-wallet/signatures-and-comparisons/blob/main/qrl-wallet-source-code-licence.md) covers what the licence permits and what a source build does not change: your keys, the network and the release process stay the same.

A build you compile is your build. The project does not review every fork, and a build that has been altered is a different program from the one the release describes.

For most readers the package is the shorter path. Build from source when you have a reason, not as a default.

## After the install

Update by installing the newer package over the old one, keeping the wallet file where it is. Keep that file inside your backup, and keep the mnemonic out of anything that reaches the internet.

If you are still choosing a platform, [Download the Official QRL Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/download-the-official-qrl-wallet.md) lists the assets for all three systems, and [Install QRL Wallet on macOS](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/install-qrl-wallet-on-macos.md) covers the macOS path if you also work on a Mac.

## FAQ

### Is there an AppImage for the current release?

No. The Linux asset is a zip containing a `.deb` and a `.pacman` package. An AppImage has been requested but is not among the published files.

### Which file do I install on Ubuntu?

The `.deb` from inside the archive. Extract the zip first, then install that package with your package manager.

### Where is the wallet file on Linux?

In a hidden directory in your home folder, created on first run. Include it in your backup with its password, and keep the mnemonic separate and offline.

### Can I run a 32-bit build?

No. There is no 32-bit asset on any platform, and the Linux release is not split by architecture.

<!-- answers: none -->
