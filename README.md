# Fresh Music Desktop updates

Distribution channel for the optional **Fresh Music** Windows helper by **Necoma**.
Fresh Music controls music on **YouTube and YouTube Music** in Chrome and Opera.

## Install

[Download FreshMusicDesktopSetup.exe (Windows x64, 0.2.10)](releases/0.2.10/FreshMusicDesktopSetup.exe)

1. Close the separate Fresh Music Windows panels.
2. Run the installer and choose Install / Update. Existing browser connections are preserved.
3. Reload Fresh Music in the browser, refresh YouTube tabs, and reopen the panel.

The optional helper needs Microsoft WebView2 Runtime. The installer does not download that runtime automatically.

## Version 0.2.10

Open tracks is always the first chooser entry. The Open in browser section can be collapsed; the preference is remembered without changing the New/All track filter.

Playback commands keep a fast path for ready tabs. When a selected YouTube tab is asleep or its receiver is outdated, an explicit playback request can activate that tab/window, wait for readiness, reload that tab once if necessary, and retry playback once. No idle recovery timer, preloading of all tabs or changes to memory-saving settings. On modern browsers, playlist reads exclude stored watch-history values.

## Version 0.2.9

Fixes remote mute toggling back when the page audio guard applies the preference synchronously across extension/page worlds. The requested mute state is captured once before dispatch. Mute/unmute preserves the chosen volume, including zero.

## Version 0.2.8

Fixes playlist selection when a playlist page retains an old player or a watch page is still loading a different video. The selected video and playlist are checked before playing; stale panel refreshes cannot overwrite the selection. Loading may be dismissed and playback errors stay readable. Standalone YouTube/Music tabs form a temporary Open tracks queue: browse it without playback, then select the exact song. Favorites and saved lists remain unchanged.

## Version 0.2.7

The panel first offers a playlist chooser, then the selected playlist tracks. Clicking the playlist heading switches back to the chooser. Open YouTube/Music playlist pages are discovered across browser windows, including unplayed and sleeping tabs. Sleeping pages load only when selected; playback stays in the original background tab.

## Version 0.2.6

The panel playlist selector now offers open browser queues, Favorites, personal and saved playlists, and the optional Blacklist playlist. It is available in all three panel sizes in Chrome, Opera and the Windows panel. Playlist starts keep the working tab in place.

## Future updates

Starting with helper 0.2.5, Fresh Music can check this signed channel and download/install a newer helper after you click **Update helper** in the extension menu.
Checks use a cache of up to 12 hours; the manual check requests fresh metadata. There is no continuously running updater or autostart service.
The source YouTube tab remains open and keeps playing music. The panel can be reopened after updating.

Update metadata is verified with a pinned RSA-SHA256 public key. Downloads must match their signed SHA256, exact URL, size and version. The extension scripts are updated separately through the browser store or local reload.
This update signature is separate from Windows Authenticode; Windows security protections are not changed.

## Public files

- `stable.json`: signed current-version manifest.
- `releases/<version>/FreshMusicDesktopSetup.exe`: versioned installer.
- `update-public-key.xml`: public verification key.

The signing private key is not hosted here. No listening history, track titles, playlist positions or collections are uploaded by the update check; GitHub receives ordinary HTTP request information.

New releases are published by updating the signed manifest and versioned installer together. Previously published version files must not be replaced.
