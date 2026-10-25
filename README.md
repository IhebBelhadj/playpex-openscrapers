# OpenScrapers

A source plugin for [Playpex Media Server](https://github.com/IhebBelhadj/Playpex): a port of the Kodi add-on [OpenScrapers](https://github.com/a4k-openproject/script.module.openscrapers) (GPL-3.0) to a Playpex plugin, keeping the scrapers that still work and give something Playpex plays.

| Source | Gives | Default |
|---|---|---|
| BnW Movies | direct MP4 files (public-domain black-and-white films) | on |
| netzkino | direct MP4 files (free German films; plays only from Germany, Austria and Switzerland) | off |
| LimeTorrents | movie and TV torrents | on |
| TorrentDownload | torrents of every kind | on |
| Nyaa | anime torrents | on |

Its sources show in a title's **Play**, in the dashboard's **Search** and in **Find releases**. Each one is a switch in the plugin's settings (dashboard › Plugins › OpenScrapers › Settings). The plugin asks only for these sites' hosts, and for direct files and magnet sources.

## Add it to a server

On the server's dashboard: **Plugins › Repositories › Add repository**, then

```
https://ihebbelhadj.github.io/playpex-openscrapers/index.json
```

Check that the key fingerprint shown is `31c9 c96c da0d 0557 52ff 9e5e 6cca a8d1`, then **Trust and add**, and install OpenScrapers from **Browse**.

Without the repository: trust the publisher key `ed25519:H32tbULm2xtiwke9LH852pXC99vKppMPScXlNYUfs60=` under **Plugins** (trusted publisher keys) and upload the `.ppx` file: the package is signed with it too.

## What is here

The repository's signed index (`index.json`, its signature `index.json.sig`) and the package it lists, built from `plugins/openscrapers/` of the Playpex repository with

```
npm run pack:repository -- plugins/openscrapers \
  --out ../playpex-plugins/openscrapers --key ../playpex-keys/openscrapers.json --id openscrapers --name "OpenScrapers" \
  --base-url https://ihebbelhadj.github.io/playpex-openscrapers/ --sign-packages
```

Servers check the index against the key they trusted, and the package against its sha256. Use the same key for every new version (raise the plugin's `version` first): servers that trusted it refuse an index signed by another.

## License and note

The plugin is GPL-3.0, like OpenScrapers it derives from (its `LICENSE` is inside the package). An educational project: streaming copyrighted content may be illegal where you live.
