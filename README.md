<p align="center">
  <img src="svg/banner.svg" width="100%" alt="GodotBuildTogether — coming soon. The first release for Linux and Windows is on its way.">
</p>

<p align="center">
  <b>Build Godot games together with your friends — live, in the same project.</b><br>
  <sub>Not affiliated with or endorsed by the Godot Foundation.</sub>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/licence-GPL--3.0-E95420?style=flat-square" alt="Licence: GPL-3.0"></a>
  <img src="https://img.shields.io/badge/Godot-4.7-3D3D3D?style=flat-square" alt="Godot 4.7">
  <img src="https://img.shields.io/badge/Linux%20%7C%20Windows-3D3D3D?style=flat-square" alt="Linux and Windows">
  <img src="https://img.shields.io/badge/status-in%20development-0E8420?style=flat-square" alt="Status: in development">
</p>

---

## What is it?

GodotBuildTogether lets you and your friends work on **the same Godot game at the
same time**. Your friend moves a tree — you see the tree move. You change a
script — they see the change as you type.

If you've used **Team Create in Roblox Studio**, you already know the idea: one
person opens up the game, the others join, and everybody builds in the same
world together. GodotBuildTogether brings that to Godot.

It's made to be simple. No servers of your own to set up, no files to send back and forth,
no zips. **Download it, start it, and begin.**

## How it works

<p align="center">
  <img src="svg/steps.svg" width="100%" alt="1. Host your game: press Open it up and the app makes a strong password. 2. Your friend joins: they type your address and password, you let them in. 3. Build together: the app copies your game, opens Godot and you see each other work live.">
</p>

There are two parts, and you get both in one download:

- **The app** — a small window that does the heavy lifting: it lets people in,
  copies the project to your friend, and keeps the connection running.
- **The Godot add-on** — lives inside the Godot editor and sends every change you
  make to the others, and theirs to you.

Your friend doesn't need to install the add-on by hand. The app brings it along
with the project, and keeps it up to date.

## What you can do

<p align="center">
  <img src="svg/features.svg" width="100%" alt="Live scenes, code together, no clashes, see each other, you decide who joins, fast and encrypted.">
</p>

- **Live scenes** — adding, moving, deleting and changing nodes shows up for
  everybody right away.
- **Code together** — two people can type in the same script at once without
  wiping out each other's work.
- **No clashes** — a node someone is working on gets their colour and a lock.
- **See each other** — the others show up as figures in your 3D view.
- **You decide who joins** — every session gets a fresh, strong password, and
  nobody gets in until you say so. You get a notification when someone knocks.
- **One copy, then only changes** — your friend receives the whole project
  the first time. After that only what changed is sent.
- **Error codes that help** — if something goes wrong you get a four-digit code
  and a plain explanation, instead of just "it doesn't work".
- **Speaks your language** — English, Dutch, German and French, picked
  automatically from your computer.

## What you need

- **Godot 4.7** — everybody needs it installed.
- **Linux or Windows.**
- **To play over the internet:** the person who hosts uses
  [playit.gg](https://playit.gg) (free) with a **UDP** tunnel. No port
  forwarding needed. On the same network you don't need it at all.

## Status

GodotBuildTogether is **not released yet**. It's being built and tested right now
by a small group of friends making a horror game with it.

- [x] Joining with a password and letting people in
- [x] Copying the project to your friend, encrypted
- [x] Live scene and script changes
- [x] Locks, colours and figures in the 3D view
- [x] Notifications on Linux (Windows is still being tested)
- [ ] First public release
- [ ] **History** — rewind the project to how it was earlier
- [ ] Block list for people you never want to let in
- [ ] When you rejoin: see what changed and choose what to keep

Want to know when it's out? Press **Watch → Custom → Releases** at the top of
this page.

<details>
<summary><b>For techies</b></summary>

<br>

- Everything runs over **one UDP port** (default `7654`) using ENet with
  **DTLS** encryption. Channel 0 carries the live session, channel 1 carries
  files, so a big download never holds up an edit.
- Files are pulled in chunks of 1 MB over several parallel connections. Every
  chunk is checked with SHA-256 and compressed with zstd when that makes it
  smaller.
- The host's certificate is currently self-signed and not yet pinned by the
  joiner. The connection is encrypted, but it doesn't yet prove *who* is on the
  other end. Pinning is planned.
- Network data is decoded without objects (`bytes_to_var`), and every path that
  comes in is checked so it can never point outside the project folder.
- Script co-editing uses a CRDT, so edits from two people merge instead of
  overwriting each other.
- Written in GDScript only. No GDExtension, nothing to compile.

</details>

## Credits

The Godot add-on started as a fork of
**[GodotWithU](https://github.com/Airyshtoteles/GodotWithU)** by
**Airyshtoteles**. His work laid the foundation for the live scene sync, the
shared script editing and the node locks. A lot has been rewritten and added
since, but parts of his code are still in there — thank you!

The app and everything added to the add-on after the fork are made by
**[Linux Ginger](https://github.com/Linux-Ginger)**.

## Licence

GodotBuildTogether is free and open source under the
**[GNU GPL v3.0 or later](LICENSE)**. You may use it, change it and share it —
as long as whoever gets your version also gets the source, under the same
licence.

The parts that come from Airyshtoteles's original remain available under the
MIT licence, see [LICENSE.MIT](LICENSE.MIT). [NOTICE.md](NOTICE.md) explains
exactly who made what.

## Trademarks

Linux Ginger is not affiliated with or endorsed by the Godot Foundation.
Linux Ginger uses the GODOT® name under a permissive license granted by the
Godot Foundation. The Godot name and logo are trademarks of the Godot
Foundation; the logo is not used in this project.

Roblox and Roblox Studio are trademarks of Roblox Corporation. GodotBuildTogether
is not affiliated with Roblox; the comparison is only there to explain the idea.

<p align="center"><sub>Made with ❤ by Linux Ginger</sub></p>
