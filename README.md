# Fresh Music Desktop updates

Distribution channel for the optional **Fresh Music** Windows helper by **Necoma**.
Fresh Music controls music on **YouTube and YouTube Music** in Chrome and Opera.

## Install

[Download FreshMusicDesktopSetup.exe (Windows x64, 0.2.14)](releases/0.2.14/FreshMusicDesktopSetup.exe)

1. Close the separate Fresh Music Windows panels.
2. Run the installer and choose Install / Update. Existing browser connections are preserved.
3. Reload Fresh Music in the browser, refresh YouTube tabs, and reopen the panel.

The optional helper needs Microsoft WebView2 Runtime. The installer does not download that runtime automatically.

## Version 0.2.14

Updates the shared panel to follow the latest actually playing source during use, with a matching vector chevron for Open in browser. Extension 1.12.0.17 includes fixes for manual YouTube navigation, stale personal queues and completing explicit track navigation with playback.

The extension now requires the owner-approved debugger permission for temporary, scoped control of a selected YouTube/Music tab. Explicit playback and camera requests can be forwarded without focusing the browser or opening our confirmation popup. Chrome/Opera may show their standard debugging notice during the short connection; this notice is not hidden. Grant the new extension permission yourself when the browser requests it. The helper update does not grant browser permissions.

Repeated original-video opening and playback passed with the actual extension debugger API in isolated Opera, and with the underlying CDP media operations in isolated Chrome/Opera. A full discarded-tab test in the automated Opera profile did not complete; actual discarded-tab behavior and the personal profile still need validation after enabling the extension update. This is a test release, not a guarantee for unavailable, protected or offline videos or conflicts with DevTools.

## Version 0.2.13

Opening the extension menu or a general panel connects it to the currently playing YouTube/Music source across windows of the same browser profile. Reopening drops a stale manual source choice when music is playing elsewhere. An explicit choice remains while the panel is open; dedicated video controls stay tied to their video. Discovery is refreshed on opening and limited to YouTube/Music tabs, without tab/window focus or playback changes.

Requires extension 1.12.0.14. Includes the extension-side Favorites/Open tracks startup fix: prepare the selected receiver, song and queue context, then send Play without waiting for prebuffered frames. Already loaded matching standalone tabs can be reused instead of creating a cold duplicate. Previous music pauses only after successful playback. Actual browser autoplay restrictions still apply; no security settings are changed.

## Version 0.2.12

Selecting a playlist automatically resumes its last saved track. Playback seconds are not stored or restored. There is no question popup or extra Resume button on the panel. Automatic continuation and remembering can be disabled in extension settings (Last playlist track).

An explicitly selected song takes priority. Previous/Next keep moving normally. Blacklisted tracks are excluded, except inside the explicitly enabled Blacklist playlist. Disabled continuation stays disabled when updating. This replaces the passive Resume button introduced in 0.2.11.

Includes 0.2.11 background-only tab recovery, white selected heart/Like/Dislike icons and direct original-video requests without our automatic confirmation popup. Genuine browser autoplay/Picture-in-Picture activation restrictions still apply.

## Version 0.2.11

Selected heart, Like and Dislike icons fill white in every panel size. Unselected icons stay outlined.

Recovering a selected sleeping or outdated YouTube/Music tab now happens in the background, without selecting the tab or focusing its browser window. Interrupted loading is retried once; genuine autoplay denials remain visible. This supersedes the focus-activation behavior described for 0.2.10.

Playlist memory stores the last playing track and playlist, without a playback time. A passive Continue from button appears inside that playlist list; there are no recurring questions or automatic jumps. Existing Ask/Auto preferences become manual continuation.

Video requests go directly to the original source video. The automatic browser confirmation popup is no longer opened. Browser Picture-in-Picture activation rules can still require a click on YouTube; the helper does not bypass those rules or bring the browser forward.

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
