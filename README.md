<a id="readme-top"></a>

<!-- Structure adapted from othneildrew/Best-README-Template, credited in Acknowledgments. -->

[![Release][release-shield]][release-url]
[![Platforms][platform-shield]](#prerequisites)
[![Code signing][signing-shield]](#installation)
[![Tauri][tauri-shield]][tauri-url]

<br />
<div align="center">
  <h3 align="center">Meander releases</h3>

  <p align="center">
    Installers and update files for Meander, on Windows and macOS.
    <br />
    <a href="https://github.com/cdelog/meander-releases/releases/latest"><strong>Download the latest release</strong></a>
  </p>
</div>

<details>
  <summary>Table of contents</summary>
  <ol>
    <li><a href="#about-the-project">About the project</a>
      <ul>
        <li><a href="#built-with">Built with</a></li>
      </ul>
    </li>
    <li><a href="#getting-started">Getting started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>

## About the project

Meander is a desktop app for Windows and macOS, and its source is private. This is how it describes itself:

<!-- lexicon:product-copy -->
> Notices claims worth checking in a live conversation, gathers evidence, and speaks a handful of times per meeting, or not at all.
> It shows you what it found and where it came from. It does not decide whether a claim is true.
<!-- /lexicon:product-copy -->

This repository holds Meander's tagged release files and nothing else. It has no source, no history and no issues.

It exists because release assets on a private repository need authentication, and the in-app updater has no credentials to offer. Publishing binaries here makes the update endpoint readable by an installed copy, and makes a download link something that can be handed to a person rather than a collaborator.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Built with

- Rust and [Tauri v2](https://v2.tauri.app/). Tauri's bundler builds the installers.
- Tauri's updater plugin, which makes the `latest.json` and `.sig` files and checks them in the installed app.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Getting started

### Prerequisites

- Windows on x64, or macOS on Apple Silicon. There's no build for Intel Macs or for Linux.

### Installation

Take the [newest release](https://github.com/cdelog/meander-releases/releases/latest), and download the file for your system.

| System               | File                                                                     |
| -------------------- | ------------------------------------------------------------------------ |
| Windows x64          | `Meander_<version>_x64-setup.exe`, or `Meander_<version>_x64_en-US.msi` |
| macOS, Apple Silicon | `Meander_<version>_aarch64.dmg`                                          |

Builds are **not code signed**, so the operating system will warn you the first time.

- **Windows.** Choose More info, then Run anyway.
- **macOS.** Open it once and let it fail. Then go to System Settings, Privacy and Security, scroll to the bottom, and choose Open Anyway. If macOS calls the app damaged, run this:

  ```sh
  xattr -dr com.apple.quarantine /Applications/Meander.app
  ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Usage

Once it's installed, Meander updates itself from this repository. You don't need to download the update files yourself.

Each release also carries `latest.json`, and a `.sig` for each file the updater can install. Those are for the updater, which verifies a signature before it writes anything. It checks the signature against a public key built into the app.

| File                                                                   | What it is                                                                                                     |
| ---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `latest.json`                                                          | The update manifest. It lists the version, the release notes, the publish date, and a download URL and signature for each platform |
| `Meander_<version>_x64-setup.exe.sig`, `Meander_<version>_x64_en-US.msi.sig` | Signatures for the two Windows installers                                                                |
| `Meander_<version>_aarch64.app.tar.gz`, and its `.sig`                 | The macOS app as an update bundle, with its signature. The updater installs this, not the `.dmg`              |

The installed app reads `https://github.com/cdelog/meander-releases/releases/latest/download/latest.json`. GitHub serves that file from the release marked Latest, so that's the version an installed copy updates to.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Roadmap

The latest release is **v0.2.2**, published on 2 September 2026. [Releases](https://github.com/cdelog/meander-releases/releases) lists every build with its notes.

- [x] Windows x64 installers, `.exe` and `.msi`
- [x] macOS Apple Silicon `.dmg`
- [x] Signed update files in every release, for the in-app updater
- [ ] Code signing, deferred to a trigger rather than scheduled

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Contributing

This repository doesn't take issues or pull requests. It holds release files only, and Meander's source is private.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## License

No license file. All rights reserved by default.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Contact

Christopher Deloglos - [@cdelog](https://github.com/cdelog)

Project link: [https://github.com/cdelog/meander-releases](https://github.com/cdelog/meander-releases)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Acknowledgments

- [Tauri](https://v2.tauri.app/), for the installers, and its updater plugin for the signature checks.
- [Best-README-Template](https://github.com/othneildrew/Best-README-Template) by othneildrew, for this README's structure.
- [Shields.io](https://shields.io) for the badges.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

[release-shield]: https://img.shields.io/github/v/release/cdelog/meander-releases?style=for-the-badge
[release-url]: https://github.com/cdelog/meander-releases/releases/latest
[platform-shield]: https://img.shields.io/badge/platforms-windows_x64_|_macos_arm64-lightgrey?style=for-the-badge
[signing-shield]: https://img.shields.io/badge/code_signing-none-orange?style=for-the-badge
[tauri-shield]: https://img.shields.io/badge/tauri-v2-24C8D8?style=for-the-badge&logo=tauri&logoColor=white
[tauri-url]: https://v2.tauri.app/
