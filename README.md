# Meander releases

Binary releases for Meander. This repository holds tagged artifacts and nothing
else: no source, no history, no issues.

It exists because release assets on a private repository need authentication, and
the in-app updater has no credentials to offer. Publishing binaries here makes the
update endpoint readable by an installed copy, and makes a download link something
that can be handed to a person rather than a collaborator.

## Installing

Take the newest release. Builds are **not code signed**, so the operating system
will warn you the first time.

- Windows: More info, then Run anyway.
- macOS: open it once, let it fail, then System Settings, Privacy and Security,
  scroll to the bottom, Open Anyway. If macOS calls the app damaged, run
  `xattr -dr com.apple.quarantine /Applications/Meander.app`.

Each release also carries `latest.json` and a `.sig` per installer. Those are for
the updater, which verifies a signature before it writes anything.