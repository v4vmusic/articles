---
title: Self Host Your v4v Music, a Definitive Guide
description: This guide is intended to walk you through setting up your own hosted music and website for your band.
date: 2023-10-24T00:13:58.829Z
preview: ""
draft: true
tags:
    - music
    - v4v
    - organization
categories:
    - Tutorials
keywords:
    - v4v

---

Make this entire series a screencast video.


Warning, this is a very long and detailed tutorial it is intended to be a complete walk through of the entire process. It's for those who aren't afraid of technology, who want to understand every aspect of v4v music. It is not for the faint of heart and you will likely bang your head a few times but when you succeed you will feel like the master of your world.

There are much, much easier ways to do this. See [How You and Your Band Can Get Paid From Streaming Bitcoin Boosts and Boostagrams]({{< ref "how-you-and-your-band-can-get-paid-from-streaming-bitcoin-boosts-and-boostagrams">}})

This guide is intended to walk you through setting up your own hosted music and website for your band.

If you're not very familiar with this kind of thing then budget at least a day and have a friend that you can ask questions to. Also Google is your friend when it comes to error messages.

This article assumes that you are comfortable using the command line and are not afraid to troubleshoot things should they go wrong.

**A familiarity with Linux is very useful.**

> **Important Note** I will be using "The Biloxi Barn Burners" as an example throughout this tutorial REPLACE all references to "The Biloxi Barn Burners" with your band's info.


## Convert all Your Songs to the mp3 Format

Many musicians have their songs recorded in wav format for quality purposes. It is a very bad idea to publish your songs in this format as the wav file sizes are HUGE and will bog down servers, waste bandwidth and give a general poor experience for your listeners.

Make sure your songs are in mp3 format and are encoded at a reasonable bit rate.

[FFmpeg](https://ffmpeg.org/) is an excellent command lint tool for converting pretty much anything audio and video
{{< highlight bash  >}}
ffmpeg -i song.wav -vn -ar 44100 -ac 2 -b:a 128k song.mp3
{{< / highlight >}}
See [Convert audio files to mp3 using ffmpeg](https://stackoverflow.com/questions/3255674/convert-audio-files-to-mp3-using-ffmpeg) for more info about the above command

This is entirely optional but I like to encode the mp3s in the same manner that I would like them stored in my computer's music library. I like to set all the id3 tags including cover image and name the file something like 

{{< highlight text >}}
01-I_got_The_Not_Your_Keys_Not_Your_Bitcoin_Rug_Pull_Blues-the-biloxi-barn-burners.mp3
{{< / highlight >}}

It doesn't really matter how you name your mp3 file. You just should name it something meaningful. NOT [79812530-0803-45db-82e5-1e6de36f55d9.mp3](https://www.wavlake.com/track/79812530-0803-45db-82e5-1e6de36f55d9) This is totally bad form and there is a special place in hell for you if you do this.


## Gather Album Art & Info

In order for you album art to display correctly in music players it **must be square**, no smaller than 500px and no larger than 1000px (this is debatable, some like larger images but no smaller than 500px)

Each song can have it's own art. This is recommended but optional. If you do not have artwork for each song most players will display the album's art in it's place

### Have a brief description of your album

This can be simple like:

{{< highlight text >}}The Biloxi Barn Burners are: 
Alice - Vocals
Bob - Keyboards
Charlie - Drums
David - Bass and Kazoo
Erin - Guitar

The Biloxi Barn Burners are a blues band out of Birmingham Alabama.
Mastered by Jim-Bob Jones
Album art by Johnny Johnson
With special thanks to Bill's Backyard Brewery for all the fine beers consumed during recording🍻
{{< / highlight >}}

Each song can also have a description associated with it. Like where it was recorded, guest musicians, lyrics and anything else you would like to share with the listeners.

## Get a Bitcoin Lightning wallet
There are many ways to do this but we're going to pick Alby for this tutorial.
Go to getalby.com and get a lightning wallet. Have each of your band members and anyone else that you want to send splits to do the same.
Watch this video to see how easy it is. [Easily Get Your Alby Wallet](https://odysee.com/@Lightning-Thashes:c/How-to-Get-an-Alby-Bitcoin-Lightning-Address-in-Less-than-2-Minutes:7)

## Get a domain name for your band
There are many ways to do this but we're going to pick Hover for this tutorial.
Go to hover.com and purchase you domain name.

Change the dns settings to
{{< highlight text >}}
ns1.digitalocean.com
ns2.digitalocean.com
ns3.digitalocean.com
{{< / highlight >}}


## Create a Digitialocean Droplet

It's likely that the cheapest Ubuntu droplet that [Digitalocean](https://m.do.co/c/c74aaeacb851) (Referral Link) has will be plenty sufficient for your needs. You can always upgrade it if you outgrow it.

Name your droplet something meaningful like "biloxibarnburners"

## Setup DNS on Digitalocean
set the DOs dns settings to point your domain to your droplet

TODO:Image

Create a subdomain and point your sub domain to your droplet
thebiloxubarnburners.com

TODO:Image

music.thebiloxubarnburners.com

TODO:Image

Follow the instructions in this tutorial.
[ Initial Server Setup with Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-22-04)

## Install Apache and Mysql
Follow the instructions in this tutorial.
[How To Install Linux, Apache, MySQL, PHP (LAMP) Stack on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-22-04)

## Setup Apache for 2 domains (websites)

Connect to your droplet through an SSH termininal. 

We are going to create 2 separate websites one for your band's website and one for where you host your music files.

Execute the following commands **one at a time** in your terminal

> Remember to replace biloxibarnburners.com with your domain name

Create the directories where your Band's website will live
{{< highlight bash >}}
mkdir ~/public_html/biloxibarnburners.com
mkdir ~/public_html/biloxibarnburners.com/public
mkdir ~/public_html/biloxibarnburners.com/private
mkdir ~/public_html/biloxibarnburners.com/logs
mkdir ~/public_html/biloxibarnburners.com/backups
{{< / highlight >}}


Create the directories where your music files will live
{{< highlight bash >}}
mkdir ~/public_html/music.biloxibarnburners.com
mkdir ~/public_html/music.biloxibarnburners.com/public
mkdir ~/public_html/music.biloxibarnburners.com/private
mkdir ~/public_html/music.biloxibarnburners.com/logs
mkdir ~/public_html/music.biloxibarnburners.com/backups
{{< / highlight >}}

Create a test page on each site
{{< highlight bash >}}
echo "Future site of my band" > ~/public_html/biloxibarnburners/public/index.html
echo "Future storage place for my band's music" > ~/public_html/music.biloxibarnburners/public/index.html
{{< / highlight >}}

We'll be using nano as our text editor.

Create Apache configuration file for your band's website

{{< highlight bash >}}
sudo nano /etc/apache2/sites-available/biloxibarnburners.com.conf
{{< / highlight >}}

paste the following text into nano REMEMBER to change where indicated then ctrl-x and y then Enter to save and exit

{{< highlight apacheconf "linenos=inline" >}}
<VirtualHost *:80>
        ServerAdmin bob@biloxibarnburners.com
        ServerName music.biloxibarnburners.com

        DocumentRoot /home/bob/public_html/music.biloxibarnburners.com/public
        <Directory "/home/bob/public_html/music.biloxibarnburners.com/public">
            Require all granted
            AllowOverride all
        </Directory>

        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /home/bob/public_html/music.biloxibarnburners.com/log/error.log
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
        CustomLog /home/bob/public_html/music.biloxibarnburners.com/log/access.log combined
</VirtualHost>
{{< / highlight >}}

Run the following command to make sure there are no errors. If there are errors reopen the file using nano and check it
{{< highlight bash >}}
sudo apache2ctl configtest
{{< / highlight >}}


Create Apache configuration file for your music storage website

{{< highlight bash >}}
sudo nano /etc/apache2/sites-available/biloxibarnburners.com.conf
{{< / highlight >}}

paste the following text into nano REMEMBER to change where indicated then ctrl-x and y then Enter to save and exit

{{< highlight apacheconf "linenos=inline" >}}
<VirtualHost *:80>
        ServerAdmin bob@biloxibarnburners.com
        ServerName biloxibarnburners.com

        DocumentRoot /home/bob/public_html/biloxibarnburners.com/public
        <Directory "/home/bob/public_html/biloxibarnburners.com/public">
            Require all granted
            AllowOverride all
        </Directory>

        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /home/bob/public_html/biloxibarnburners.com/log/error.log
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
        CustomLog /home/bob/public_html/biloxibarnburners.com/log/access.log combined
</VirtualHost>
{{< / highlight >}}
Run the following command to make sure there are no errors. If there are errors reopen the file using nano and check it
{{< highlight bash >}}
sudo apache2ctl configtest
{{< / highlight >}}

enable the newly created sites
{{< highlight bash >}}
sudo a2ensite biloxibarnburners.com.conf
sudo a2ensite music biloxibarnburners.com.conf
{{< / highlight >}}


Restart the Apache webserver
{{< highlight bash >}}
sudo systemctl restart apache2.service
{{< / highlight >}}

curl is a command line tool that allows you to download the contents of a web page. We'll use curl to see if our sites are working.

Test your band's website
{{< highlight bash >}}
curl http://biloxibarnburners.com
{{< / highlight >}}

You should see
> Future site of my band

Test your music storage website
{{< highlight bash >}}
curl http://biloxibarnburners.com
{{< / highlight >}}

You should see
> Future storage place for my band's music

## Enable SSL on Our Domains

Use certbot from [Let's Encrypt](https://letsencrypt.org/) to get ssl certificates

{{< highlight bash >}}
sudo apt install certbot python3-certbot-apache
{{< / highlight >}}

Allow SSL connections through the firewall
{{< highlight bash >}}
sudo ufw allow 'Apache Full'
{{< / highlight >}}

Obtain the SSL certificates from Let's Encrypt
{{< highlight bash >}}
sudo certbot --apache
{{< / highlight >}}

Follow the onscreen instructions

For more info about the above command see [How To Secure Apache with Let's Encrypt on Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-20-04)


## Organize Your Music Files and Artwork on Your Local Machine

Create a folder on your local machine.

Create your directories with the following naming conventions in mind
- Use lowercase letters only
- Only use letters a-z and numbers 0-9
- The only special characters that are allowed in the file name are - and _ and . only before the extension
- Do NOT use spaces!

We are going to be creating the following file / folder structure for our music.
I recommend copying (not moving) your music files and artwork into these locations that way if anything goes wrong we can just delete and start over.

{{< highlight bash >}}
.
└── v4vmusic
    └── band-name
        ├── album-name-1
        │   ├── 01-song_name-band_name.mp3
        │   ├── 02-song_name-band_name.mp3
        │   └── 03-song_name-band_name.mp3
        ├── album-name-2
        │   ├── 01-song_name-band_name.mp3
        │   ├── 02-song_name-band_name.mp3
        │   └── 03-song_name-band_name.mp3
        └── album-name-3
            ├── 01-song_name-band_name.mp3
            ├── 02-song_name-band_name.mp3
            └── 03-song_name-band_name.mp3
{{< / highlight >}}


Example file / folder structure
{{< highlight bash >}}
v4vmusic
└── biloxi-barn-burners
    ├── biloxi-barn-burners.jpg
    ├── bitterswet-bitcoin-blues
    │   ├── 01-i_got_the_not_your_keys_not_your_bitcoin_rug_pull_blues-biloxi_barn_burners.jpg
    │   ├── 01-i_got_the_not_your_keys_not_your_bitcoin_rug_pull_blues-biloxi_barn_burners.mp3
    │   ├── 02-her_heart_may_be_cold_but_my_cold_card_is_colder-biloxi_barn_burners.jpg
    │   ├── 02-her_heart_may_be_cold_but_my_cold_card_is_colder-biloxi_barn_burners.mp3
    │   ├── 03-five_dollar_wench-attack-biloxi_barn_burners..jpg
    │   ├── 03-five_dollar_wench-attack-biloxi_barn_burners.mp3
    │   └── bitterswet-bitcoin-blues.jpg
    ├── inflation-nation-bringing-me-down
    │   ├── 01-she_forced_closed_on_me_again-biloxi_barn_burners.jpg
    │   ├── 01-she_forced_closed_on_me_again-biloxi_barn_burners.mp3
    │   ├── 02-splittin_sats_under_the_old_merkle_tree-biloxi_barn_burners.jpg
    │   ├── 02-splittin_sats_under_the_old_merkle_tree-biloxi_barn_burners.mp3
    │   ├── 03-she_doesnt_trust_me_she_verifies-biloxi_barn_burners.jpg
    │   ├── 03-she_doesnt_trust_me_she_verifies-biloxi_barn_burners.mp3
    │   └── inflation-nation-bringing-me-down.jpg
    ├── rise-up-and-be-soverign
    │   ├── 01-shes_down_with_btc-biloxi_barn_burners.jpg
    │   ├── 01-shes_down_with_btc-biloxi_barn_burners.mp3
    │   ├── 02-if_she_knew_the_v_i_have_for_her_v-biloxi_barn_burners.jpg
    │   ├── 02-if_she_knew_the_v_i_have_for_her_v-biloxi_barn_burners.mp3
    │   ├── 03-she_drowned_me_in_the_wavy_lake-biloxi_barn_burners.jpg
    │   ├── 03-she_drowned_me_in_the_wavy_lake-biloxi_barn_burners.mp3
    │   └── rise-up-and-be-soverign.jpg
    └── singles
        ├── 01-i_got_the_not_your_keys_not_your_bitcoin_rug_pull_blues-biloxi_barn_burners.mp3
        ├── 02-five_dollar_wench-attack-biloxi_barn_burners.mp3
        └── 03-she_doesnt_trust_me_she_verifies-biloxi_barn_burners.mp3
{{< / highlight >}}

## Setup Filezilla for SSH Uploading
We'll be using Filezilla to upload our music files from our home computer to our newly created websites

Follow this tutorial. Remember to install Filezilla on your home PC not your server

## Upload Your Music to Your Server
Connect to your site with Filezilla
Navigate your local directory to your v4vmusic folder

Navigate your remote directory to /home/user/public_html/music.biloxibarnburners.com/public

Upload the the entire contents of your v4vmusic folder /home/user/public_html/music.biloxibarnburners.com/public/

# Test That Your Files Are Available on the Internet
Open a web browser and navigate to https://music.biloxibarnburners.com/v4v/music/bitterswet-bitcoin-blues/01-i_got_the_not_your_keys_not_your_bitcoin_rug_pull_blues-biloxi_barn_burners.mp3

If you cannot access the file in your web browser then something went wrong.


# Create Your Album's RSS Feeds
The Rock Solid Signal Feed ([RSS](https://en.wikipedia.org/wiki/RSS)) feed is the "source of truth" for your music. It's what all the music and podcast apps use to present all information about your music to your listeners.

An RSS feed is just a text file written in a markup language called Extensible Markup Language ([XML](https://en.wikipedia.org/wiki/XML)).

You can use your favorite text editor to create your own RSS feed. 

Sir Spencer has created an excellent and very informative RSS [template with comments](https://github.com/de-mu/demu-feed-template/blob/master/feed-with-comments.xml) I recommend studying it if you want to understand what's all going on [behind the sch3m3s](https://behindthesch3m3s.com/)

However we will be using Steven Bell's "Music Side Project" website to create our RSS feeds for us.

Go to [musicsideproject.com](https://musicsideproject.com)




# Create WordPress site

Mkdir ~/tmp
Cd ~/tmp

wget WordPress.com/latest.tar.gz

Untar

Cp -r WordPress/* to public folder

Create MySQL database

Go to website and finish WordPress installation

At your leisure you will need to set up your wordpress site. There are tons of good tutorials for this online.










