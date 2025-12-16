---
title: How to Create a Podcast RSS Feed Using The Split Kit and Sovereign Feeds
author: Randy Black
date: 2025-03-27T16:51:41.204Z
categories:
  - Tutorials
tags:
  - self-hosting
  - The Split Kit
  - Sovereign Feeds
  - CDN
toc: true
---
This article was published orginially at [https://randallblack.com/self-hosted-rss/](https://randallblack.com/self-hosted-rss/) and is shared here by it's author.

# How to Create a Podcast RSS Feed Using The Split Kit and Sovereign Feeds

## Self-Hosting Your Podcast with Bunny.net for Maximum Control

Podcasting is evolving, and with tools like **Sovereign Feeds** and **The Split Kit**, independent podcasters can fully control their RSS feed, manage value-for-value splits, and host their own media files without relying on traditional podcast hosts. In this guide, I’ll show you how to:

- Create a podcast RSS feed using **Sovereign Feeds**
- Set up **value-for-value** splits using **The Split Kit**
- Host your media files on **Bunny.net**
- Upload your RSS feed to a web host
- Distribute your podcast across platforms

By the end of this tutorial, you'll have a fully functional podcast feed that you control. Let’s get started!

---

## Step 1: Create Your Podcast RSS Feed with Sovereign Feeds

### 1.1 Sign Up for Sovereign Feeds

- Go to **[Sovereign Feeds](https://sovereignfeeds.com/)**
- Click **Sign in with Alby** (or another authentication method)
- Once logged in, click **New Feed** to start creating your podcast

### 1.2 Fill in Your Podcast Details

- **Podcast Title**: Enter your podcast’s name
- **Description**: Add a summary of your show
- **Artwork**: Upload a podcast cover (min. 1400x1400px)
- **Category**: Choose a category (e.g., Education, Tech, Music)
- **Website**: Enter your podcast’s website (if applicable)
- **Feed URL**: This will be generated for you

### 1.3 Add Episodes

- Click **New Item** to create an episode
- Enter the **Title, Description, and Publish Date**
- Add the **URL** for the media file (we’ll set this up in Bunny.net later)
- Set the **Duration** and **File Type** (MP3, MP4, etc.)

Once done, save the feed. You now have a basic RSS feed ready!

---

## Step 2: Set Up Value-for-Value with The Split Kit

Now, let’s add a **value-for-value** model so you and your contributors (co-hosts, editors, guests) can receive Bitcoin micropayments via Lightning.

### 2.1 Sign Up for The Split Kit

- Go to **[The Split Kit](https://thesplitkit.com/)**
- Sign in using your Lightning-enabled wallet (e.g., **Alby** or **LNbits**)
- Click **New Split**

### 2.2 Create a Split

- **Name Your Split** (e.g., "My Podcast")
- **Add Participants**
  - Enter the Lightning addresses of each person who should receive payments
  - Set their percentage (e.g., Host: 60%, Guest: 20%, Editor: 20%)
- Click **Generate Split**

### 2.3 Add the Split to Sovereign Feeds

- Copy the **Lightning split code** from The Split Kit
- Go back to **Sovereign Feeds** and edit your podcast feed
- In the **Value** section, paste the Split Kit code
- Save the feed

Now, every time someone listens via a **Podcasting 2.0 app** like **Fountain**, payments will be automatically split!

---

## Step 3: Host Your Media Files on Bunny.net

Since you’re self-hosting, you need a reliable **CDN (Content Delivery Network)** to store and serve your audio files.

### 3.1 Sign Up for Bunny.net

- Go to **[Bunny.net](https://bunny.net/)**
- Create an account and log in

### 3.2 Set Up a Storage Zone

- In the **Bunny.net Dashboard**, go to **Storage Zones**
- Click **Create New Storage Zone**
- Name it (e.g., "mypodcast")
- Choose a **region** (Select one closest to your audience)
- Click **Create Storage Zone**

### 3.3 Set Up a CDN for Your Podcast

- In Bunny.net, navigate to **Pull Zones**
- Click **Add Pull Zone**
- Name it (e.g., "mypodcast-cdn")
- Set the **Origin URL** to your newly created Storage Zone
- Choose a caching region that best fits your audience
- Enable **Optimized Caching** for faster delivery
- Click **Create Pull Zone**

### 3.4 Upload Your Podcast Episodes

- Use **FTP or the Bunny.net web interface** to upload your **MP3** files
- Once uploaded, click on a file and **copy the direct URL**

### 3.5 Add the Media File to Your RSS Feed

- Go back to **Sovereign Feeds**
- Edit your episode and paste the **Bunny.net CDN URL** as the media file link
- Save the feed

Your podcast episodes are now hosted on a **fast CDN** and linked to your RSS feed!

---

## Step 4: Upload Your RSS Feed to a Web Host

### 4.1 Choose a Web Host

You need a web host to store and serve your **RSS feed XML file**. Some options include:

- **GitHub Pages** (free for static files)
- **DigitalOcean Spaces**
- **Amazon S3**
- **Self-hosted VPS (e.g., Linode, Vultr)**

### 4.2 Upload the RSS Feed File

- Export your RSS feed from **Sovereign Feeds** (Download the XML file)
- Upload the XML file to your chosen web host
- Copy the **public URL** of your uploaded RSS file

### 4.3 Update Your Feed URL in Sovereign Feeds

- Go back to **Sovereign Feeds** and update your feed’s URL with the new public link
- Save the changes

Now, your RSS feed is live and accessible on the web!

---

## Step 5: Validate and Distribute Your Podcast

### 5.1 Validate Your RSS Feed

- Use a tool like **[CastFeedValidator](https://castfeedvalidator.com/)**
- Enter your **Sovereign Feeds RSS URL** and check for errors

### 5.2 Submit to Podcast Directories

Once your feed is working, submit it to major podcast platforms:

- **Apple Podcasts**: [podcasters.apple.com](https://podcasters.apple.com/)
- **Spotify for Podcasters**: [podcasters.spotify.com](https://podcasters.spotify.com/)
- **Podcast Index**: [podcastindex.org](https://podcastindex.org/) *(supports value-for-value!)*

---

## Final Thoughts

Congratulations! You’ve just set up a **self-hosted podcast RSS feed** using **Sovereign Feeds**, **The Split Kit**, and **Bunny.net**. With this setup:

- You **own your RSS feed** (no dependence on third-party hosts)
- You **control your monetization** via **value-for-value** payments
- Your audio is **hosted on a fast CDN** for smooth streaming
- You can **distribute your podcast freely** across platforms

This method gives you full control and ensures your podcast remains independent.
