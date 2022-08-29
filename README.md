# Balena Plex Seedbox

Quickest and easiest way to get [Plex](https://www.plex.tv) and friends (Radarr, Sonarr, Prowlarr, Bazarr and Transmission with a secure VPN) running on a Raspberry Pi 4, NUC and many more.

| Service                                                                    | URL                                                                                                                                                                                                  |
| -------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Plex](https://plex.tv)                                                    | Stream Movies and TV shows, from your library and theirs.                                                                                                                                            |
| [Radarr](https://radarr.video/#home)                                       | A movie collection manager for Usenet and BitTorrent users. It can monitor multiple RSS feeds for new movies and will interface with clients and indexers to grab, sort, and rename them.            |
| [Sonarr](https://sonarr.tv)                                                | A PVR for Usenet and BitTorrent users. It can monitor multiple RSS feeds for new episodes of your favorite shows and will grab, sort and rename them.                                                |
| [Prowlarr](https://prowlarr.com)                                           | An indexer manager/proxy built on the popular \*arr .net/reactjs base stack to integrate with your various PVR apps. Prowlarr supports management of both Torrent Trackers and Usenet Indexers.      |
| [Bazarr](https://www.bazarr.media)                                         | A companion application to Sonarr and Radarr. It manages and downloads subtitles based on your requirements.                                                                                         |
| [Transmission VPN](https://github.com/haugene/docker-transmission-openvpn) | OpenVPN and Transmission with a configuration where Transmission is running only when OpenVPN has an active tunnel. It has built in support for many popular VPN providers to make the setup easier. |

## Getting started

1. Click the deploy with balena button below:

[![balena deploy button](https://www.balena.io/deploy.svg)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/maggie0002/balena-plex-seedbox)

2. Select your device and name for your fleet

3. Click the advanced toggle and `Add an item` under the `Fleet environment variables` section.

4. Configure each of your required variables for Transmission VPN with your VPN provider details. A list of supported VPN providers is available [here](https://haugene.github.io/docker-transmission-openvpn/supported-providers/):

   | Name             | Value                |
   | ---------------- | -------------------- |
   | OPENVPN_PROVIDER | name-of-VPN-provider |
   | OPENVPN_USERNAME | your-username        |
   | OPENVPN_PASSWORD | the-password         |

5. Click `Create and Deploy`.

6. In the next screen, click `Add device` and configure your WiFi details if you intend to use WiFi instead of ethernet.

7. Hit the `Flash` button, put your SD card in to your device and wait for it to load!

## Usage

Give your device some time to setup all the required components. When it is ready the services will be available on your local network through the following URLs:

| Service          | URL                                                         |
| ---------------- | ----------------------------------------------------------- |
| Plex             | `http://plex.local/web` where you can begin your Plex setup |
| Radarr           | `http://plex.local:7878`                                    |
| Sonarr           | `http://plex.local:8989`                                    |
| Prowlarr         | `http://plex.local:9696`                                    |
| Bazarr           | `http://plex.local:6767`                                    |
| Transmission-VPN | `http://plex.local:9091`                                    |

There is a Caddy service running to allow you to access all of these services without the need for port numbers, although it is completely optional. To use it, you will need to access each service through the URLs above and configure the `base URL`. This configuration is usually in Settings -> General. Set the base URL of each to the following:

| Service          | BaseURL         |
| ---------------- | --------------- |
| Radarr           | `/radarr`       |
| Sonarr           | `/sonarr`       |
| Prowlarr         | `/prowlarr`     |
| Bazarr           | `/bazarr`       |
| Transmission-VPN | `/transmission` |

You are now ready to go! Access each of the control panels and start configuring your settings referring to the documentation of each service.

## Contributing

Contributions are very welcome, both in terms of fixes and improvements. Ideas are also welcome in the [discussions](https://github.com/maggie0002/balena-plex-seedbox/discussions) section.
