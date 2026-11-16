# Fresh Music Desktop updates

Distribution channel for the optional **Fresh Music** Windows helper by **Necoma**.
Fresh Music controls music on **YouTube and YouTube Music** in Chrome and Opera.

## Install

[Download FreshMusicDesktopSetup.exe (Windows x64, 0.2.6)](releases/0.2.6/FreshMusicDesktopSetup.exe)

1. Close the separate Fresh Music Windows panels.
2. Run the installer and choose Install / Update. Existing browser connections are preserved.
3. Reload Fresh Music in the browser, refresh YouTube tabs, and reopen the panel.

The optional helper needs Microsoft WebView2 Runtime. The installer does not download that runtime automatically.

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
