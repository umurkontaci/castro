# castro
Your own Netflix, it's even better

> -Is it on Netflix?  
> -It's a good movie, so no.

# What is it?

This is a set of software that allows you to run a media server in the cloud very easily.
It's bundled with wonderful software like Plex and uTorrent (and nginx) via Docker.

Plex manages your archive, downloads cover arts, subtitles, ratings etc. and handles serving and transcoding content 
on really wide series of devices, uTorrent is responsible for getting the content in your archive.

# Getting Started

> The default password is admin:admin. You should change it.

## Installation

1. Get a server
2. Set up 2 DNS records to server's IP. (For torrent and plex, each) (Do this now so you'll wait less for propagation)
3. Install Docker and Docker Compose
3. Clone the repo
4. Edit `docker-compose.yml` and replace `TORRENT_DOMAIN` and `PLEX_DOMAIN` for the domains you picked.
5. Run docker-compose build && docker-compose start

## Setting up Plex

1. Head over to your http://PLEX_DOMAIN/web
2. Accept ToS, give your server a name and play around
3. Add two libraries from the + icon above your server on the left hand side of the page. (Movies and TV Shows). 
uTorrent puts all downloads to `/plex/` folder, so choose that folder for both.
5. Create a plex account, connect your account with the server (from server settings).
6. Check port forwarding, the default port is 32400. If Plex can't connect, set that port manually (even if it says it's set to 32400 by default)
7. Start downloading content

