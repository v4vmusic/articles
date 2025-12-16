---
title: How You and Your Band Can Get Paid From Streaming Bitcoin Boosts and Boostagrams
author: Kolomona Myer - Sir Libre
date: '2023-09-08T21:05:28-07:00'
categories:
  - Tutorials
tags:
  - music
  - v4v
toc: true
thumbnail: /img/v4v-dark01.png
---
## How you and your band can get paid from streaming bitcoin, boosts and boostagrams
![](/img/v4v-dark01.png)

Using modern podcasting technology and bitcoin on the lightning network there is now a way for musicians get paid in real time for their art.
 
## TLDR: The Easiest Way
- Get a bitcoin lightning wallet from [Alby](https://getalby.com) - [Quick Alby How to Video](https://odysee.com/@Lightning-Thashes:c/How-to-Get-an-Alby-Bitcoin-Lightning-Address-in-Less-than-2-Minutes:7)
- (optional) Get an Alby wallet for each person in your band / organization
- Contact Boo-Bury at [Thunder Road Music](https://thunderroad.media/) and he'll walk you through the rest thunderroadmusic@proton.me
- Market your music to your fans

## Monetizing Your Music
All this stuff can seem overwhelming at first but it only needs to be done once and if you take it one step at a time you'll get through it with minimal trauma.

Also it's easier than enslaving yourself to a record contract that even though you read it you didn't understand it.

## Quick Definitions

- **Bitcoin** (BTC) - An online peer to peer cash system created by Satoshi Nakamoto [Bitcoin FAQ](https://bitcoin.org/en/faq)
- **Satoshi / sat** - The smallest unit of a bitcoin 1/100,000,000 BTC = 1 satoshi (sat)
- **Lightning Network** - A bitcoin payment network that allows nearly instantaneous bitcoin payments. [Lightning Info](https://lightning.network/)
- **Streaming sats** - bitcoin sent to the artists as the listener listens to a song.
- **Boost** - The listener can choose to send extra BTC to the artist in any amount
- **Boostagram** - Same as a boost but with a message that the artist can read.


## Things You Need

1. Music that you own all copyrights to. [More on copyrights](https://www.tunecore.com/guides/copyrights-101)
    1. (Optional but highly recommended) Art for your albums and art for each track.
2. A Podcasting 2.0 RSS Feed.
3. A place to host your music and RSS feed online.
4. A bitcoin lightning wallet capable of receiving keysend payments
    1. (Optional but highly recommended) The lightning wallet addresses from those that you want to share your earnings with.
 
## Music & Artwork

- A high quality recording of the music that you want to share with the world in mp3 format.
- Art for your albums and art for each track. Must be square and no less than 500 pixels. (Optional but highly recommended)

## A Place to Host Your Music Online

There are plenty of ways that you can get your mp3s and RSS feed onto the Internet. Some of them are free others cost money.

- [Thunder Road Music](https://thunderroad.media/) (Easy) Boo-Bury is providing a hosting service. He will do all the heavy lifting for you, you just need music and wallet addresses.
- [Archive.org](https://help.archive.org/help/uploading-a-basic-guide/) (Easy-ish) is free
- A shared web host such as [wordpress.com](https://wordpress.com), Host Gator, [Go Daddy](https://godaddy.com), etc. (Easy to Advanced)
- [Blubrry.com]
- [DigitalOcean](https://www.digitalocean.com/pricing/droplets) (Advanced) for as little as $4 / month you can get 10gb plus you can setup your website / podcast on it, but you'll need to know how to be your own sys admin.

## A Bitcoin Lightning Wallet

Each person who wishes to receive streaming bitcoin, boosts and boostagrams must have a Bitcoin lightning wallet that's capable of receiving keysend payments.

Bitcoin Lightning wallets capable of receiving keysend

- **Custodial** (Easy - Not your wallet but you have access to it, much like your bank account)
    - [Alby](https://getalby.com)
    - [Fountain](https://fountain.fm)
- **Non-Custodial** (Easy but there be dragons - Owned by you and if you loose it it's gone, much like the cash in your wallet)
    - [Muun](https://muun.com/)
    - [Breeze](https://breez.technology/)
- **Lightning Nodes** (Advanced, big dragons - Most Sovereign Non-Custodial)
    - [Raspiblitz](https://raspiblitz.org/)
    - [Umbrel](https://umbrel.com/)
    - [Start9](https://start9.com/)
    - [MyNode](https://mynodebtc.com/)

  Once you have your lightning wallet you will need your keysend address. Consult the documentation of the wallet you are using to obtain this.

## A Podcasting 2.0 Rock Solid Signal ([RSS](https://vimeo.com/870858439/d700d7abc2)) Feed

- Learn about Podcasting 2.0 at [Podcast Namespace](https://github.com/Podcastindex-org/podcast-namespace) (Advanced)
- Learn about RSS at [Wikipedia](https://en.wikipedia.org/wiki/RSS) (Advanced)


### Creating Your Feed

If you think about your music album as it's own podcast this will make more sense to you.

You need to create an RSS feed for your Album.

- (Easiest) [Thunder Road Music](https://thunderroad.media/)

- (Advanced and sovereign) [MusicSideProject.com](https://musicsideproject.com/) -  If you want to be in control of your music and be more sovereign then [Steven Bell](https://podcastindex.social/@StevenB) has created [MusicSideProject.com](https://musicsideproject.com/) which will walk you through creating your RSS feed for your album.

- (Advanced and sovereign) [Sir Spencer's DeMu RSS Template](https://github.com/de-mu/demu-feed-template/blob/master/README.md) Sir Spencer of [Able and the wolf](https://ableandthewolf.com) and [Bowl after Bowl](https://bowlafterbowl.com/) has created an RSS template file with tons of comments explaining all the important bits. All you need to do is use your favorite text editor and fill it in.


**Important** Make sure that the medium tag in the RSS feed says "music" not "podcast" (If using [MusicSideProject.com](https://musicsideproject.com/) then it's done for you)

Example: `<podcast:medium>music</podcast:medium>`

## Publishing Your Work

Upload your music, art and RSS files to your server. Depending on your choice of host this process can differ.

I self host my files on my own server and [Filezilla](https://filezilla-project.org/) works well for this.

### Self Hosting Recommendations

I recommend that you back up your RSS file each time you update it just in case something goes wrong.

Use [IPFS Podcasting](https://ipfspodcasting.net/) to help host your files. Be sure to include IPFS podcasting in your split as it's a valuable service.

Use [OP3](https://op3.dev) redirects for basic download stats. Here are [Lightning Thrashes op3 stats](https://op3.dev/show/ebebbf711998472b86b9114fe3aba3d3)

I also recommend storing your files in some sort of folder structure for easy organization. (optional but makes things much easier to troubleshoot)

- Each album in it's own folder with album art and it's RSS feed

- Each song in it's own folder with it's song art, lyrics and chapter files

## Resources

- A list of [Modern Podcast Apps](https://podcastindex.org/apps?appTypes=app&elements=Value%2CBoostagrams)
- [Adam Curry's Speech on the history of podcasting](https://vimeo.com/870858439/d700d7abc2) and the importance of Rock Solid Signal (RSS)
- Information on [Copyrights](https://www.tunecore.com/guides/copyrights-101)
- [Bitcoin FAQ](https://bitcoin.org/en/faq)
- [Bitcoin Lightning Network Info](https://lightning.network/)
- [IPFS Podcasting](https://ipfspodcasting.net/) for help spreading the bandwith
- [OP3](https://op3.dev) redirects for basic download stats.
- [podcastindex.social](https://podcastindex.social/deck/@thedude33@noagendasocial.com) If you run into any problems there are a ton of people who would love to help you.

# Go Podcasting!