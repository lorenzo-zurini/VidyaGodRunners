# VidyaGodRunners

The default package repository for [VidyaGod](https://github.com/lorenzo-zurini/VidyaGod).

VidyaGod syncs this repository into `~/.VidyaGod/DOWNLOADS` (a shallow `git clone`/`git pull`)
on startup and indexes every package directory here into its catalog. Each subdirectory is a
package: a folder containing a `MANIFEST.json` (plus optional `*.json` fragments).

## Runners

Each runner package is a pure-runner package — `HOST_PLATFORM: "linux64"`, a single `RUNNERS`
entry, no `GAMES` — that the launch resolver discovers like any other package and offers wherever
its `GUEST_PLATFORM` matches a game's `HOST_PLATFORM`.

| Package | Runner | Type | Targets |
| --- | --- | --- | --- |
| `ge-proton10-30` | GE-Proton10-30 (`umu-run`) | wine | win32, win64 |
| `umu-proton` | umu-proton (`umu-run`) | wine | win32, win64 |
| `wine` | wine | wine | win32, win64 |
| `snes9x` | snes9x | emulator | snes |
| `native-passthrough` | Native (passthrough) | native | linux64 |

## Adding packages

Add a directory with a `MANIFEST.json` and push. Clients pick it up on their next sync. Avoid
machine-specific absolute paths (home directories, Steam compat-tool paths) so packages stay
portable across installs.
