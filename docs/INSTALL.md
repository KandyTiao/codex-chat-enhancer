# Codex Chat Enhancer｜Codex 聊天增强软件 · Setup

[简体中文](INSTALL.zh-CN.md) · [Product overview](../README.md)

## Before you start

Windows, Node.js 24+ and official Codex are required for the tested path. Run node --version in a terminal. Native integration also requires Codex to expose its debug endpoint on localhost; the usual address is http://127.0.0.1:39222/json/list. Keep that endpoint on localhost.

If you already use Codex Sidekick, finish running tasks and open Codex through its enhanced desktop entry when a reopen is needed. This enhancer can then attach to that existing connection. It does not restart Codex to create one.

For a standalone setup, after normally closing an idle Codex window you can start the official desktop GUI with --remote-debugging-address=127.0.0.1 --remote-debugging-port=39222. Use the confirmed GUI executable path from your installation, not the command-line codex program. Windows Store paths vary. This development preview does not supply a standalone Codex launcher. If you cannot establish this connection, use sample-only preview or wait for a future installer.

## Download and run

1. Extract codex-chat-enhancer-v0.1.3.zip. The opened folder must contain package.json, src, web, scripts and the two .cmd entries. Keep it in a writable location.
2. Double-click 启动开发预览.cmd. It starts this tool and opens http://127.0.0.1:19767/.
3. Open the Codex sidebar. The three new groups should appear at the top. Visit http://127.0.0.1:19767/api/health: version must be 0.1.3 and native.available must be true, with native.connected greater than zero. The sample webpage is separate from native integration.
4. Click an unread/attention/long-running entry to open its original chat. Official Codex controls its read state. Right-click a group for theme selection; click its header to collapse it.

The Windows script looks for node.exe on PATH, then the bundled Codex Node runtime if present. If the entry cannot find Node, install Node.js 24+ and reopen the terminal. It does not download dependencies.

## Try only the sample interface

In the extracted folder run:

    node src/server.cjs --preview-only

Then open http://127.0.0.1:19767/. All chats and state controls there are fictional examples. This mode does not attach to Codex. If another instance already uses port 19767, stop that instance normally or choose a different port; do not terminate another program.

## Stop and remove

Double-click 停止开发预览.cmd, or run node scripts/control.cjs in this folder. The tool authenticates its own instance, removes its native UI/timers and leaves Codex and Sidekick running. After it has stopped, remove the extracted folder if you want to uninstall; save your data/preferences.json first if you need those preferences. No system-wide installation or sign-in startup is created.

## Settings and troubleshooting

To use custom ports, copy config.example.json to config.json and edit the supported port/cdpPort values. Default enhancer port: 19767; default debug port: 39222. Port 19766 belongs to Sidekick and cannot be used here. Do not change the software program files. Restart only this enhancer to apply configuration.

If the preview opens but the sidebar does not: check the debug endpoint, native.available, and whether this Codex version still matches the tested internal interfaces. Missing reliable state stays unavailable or unknown; it is not guessed from idle or old history.

If Windows blocks the script, examine the file/source and follow your organization’s policy. Node scripts are not a signed EXE installer. This version has no automatic stuck-task detection or restart.

## Compatibility and permission

Windows Codex 26.1002.7124 was tested. macOS and complete remote/ChatGPT behavior are unverified. [Free-use license](../LICENSE): use and supported configuration are allowed; program modification and redistribution are not.
