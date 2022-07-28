# castro
Your own Netflix, it's even better.

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

1. Install Docker and Docker Compose
2. Clone the repo
3. Run docker-compose build && docker-compose start

## Setting up Plex

1. Head over to `http://SERVER_IP:9021/web`
2. Accept ToS, give your server a name and play around
3. Add two libraries from the + icon above your server on the left-hand side of the page. (Movies and TV Shows). 
uTorrent puts all downloads to `/plex/` folder, so choose that folder for both.
4. Create a plex account, connect your account with the server (from server settings).
5. Check port forwarding, the default port is 32400. If Plex can't connect, set that port manually (even if it says it's set to 32400 by default)
6. After you complete initial set up, create a Plex account and link that account with your server, you can go to https://plex.tv and watch your movies everywhere.

## Downloading content

1. Find a content to download via uTorrent.
2. Copy the `.torrent` URL or the `magnet link`.
3. Head over to `http://SERVER_IP:9022`
4. Paste the link
5. Wait for it to download
6. In about a minute after the download, you should be seeing the content on Plex.

# Troubleshooting

## I can't see downloaded content

Trigger a refresh on Plex manually. If you find yourself doing this everytime you download a content, create an issue.

## Video buffers a lot

Plex handles transcoding on the server which requires a lot of CPU power, the possible solutions are:

- Get a more powerful server
- Download appropriate content which doesn't need to be transcoded
- In server's transcoding options, set quality to "Prefer higher speed encoding"

## TV Shows show up in Movies Library

This is because it is pretty hard with uTorrent to differentiate between TV Shows and Movies and put them into different folders. If you have a suggestion, please create an issue.

My workaround for that is to "merge" the invalid content into one so that it doesn't take a lot of space.


# Advanced

## Domains

Instead of using the IP and the port to access uTorrent or Plex, you can use domain names; edit `docker-compose.yml` and modify domain names and nginx will be listening for those.

## SSL

You shouldn't be sending passwords in cleantext over the net, you can put your certificates in nginx/certs folder, and modify the nginx configuration in nginx/sites folder. I am assuming that if you can get SSL certificates, you can figure the configuration out pretty easily.


