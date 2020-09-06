---
title: This Website, and How To Build Your Own
date: 2020-09-01
---

## Origins
This website is just a bunch of little files living on a tiny computer that sits on my living room bookcase. It plugs into the wall and my router, and all it does all day is serve up these website files to whoever requests them. For most servers out there (shared hosting, virtual private servers, and the like), it is a thankless job. But I try to give my little Lime2 single-board computer some attention every so often. A little bit of gratitude can go a long way.

Over the years, I've built a few different personal websites. First, there was the college résumé site, [nathanhewitt.net](https://natehn.com/posts/this-website/#origins). Then there were other short-lived iterations: the music-focused [auohm.us](https://natehn.com/posts/this-website/#origins) (before I stopped using the moniker AUOHM), the simplistic [nthnh.co](https://natehn.com/posts/this-website/#origins), and the Web 1.0 [omg.lol/nathan](https://natehn.com/posts/this-website/#origins). On the backend, I tried Wordpress, Squarespace, Wix, and others. I also put together plenty of simple, WYSIWYG websites when I was doing freelance graphic design in college. 

For this website, I originally wanted to self-host in order to learn *how*. As I built the site, however, I started to come up with other reasons. Over time, a constellation of motivations started to form:

- My desire to learn basic Linux programming (`bash`) and related technology
- Trying to get away from corporate-owned social media platforms
- Finding my written voice again
- Experimenting with solar power
- Sharing what I have learned; sharing what I am learning
- Having a home on the web

"Natehn" is a new online moniker that mixes three letters of my first and last names. I feel that, as my public engagement with the Internet begins to change, a new name will help to separate the new from the old. (The similarity to [Brian Crabtree's moniker](https://github.com/tehn) is purely coincidental.)

## Building Your Own
If you're interested in building and hosting your own website the way I did, I would be [happy to help](mailto:nthnhwtt@gmail.com). Some basic directions are below. As you go, be sure to also check in on the core documentation for [Armbian](https://docs.armbian.com/) and [Hugo](https://gohugo.io/getting-started/quick-start/). You may also want to learn the basics of [the command line](https://techlearningcollective.com/foundations/) and [bash](https://www.youtube.com/watch?v=4d77bxpgB5c). Finally, I recommend checking out the guides at [the homebrewserver.club](https://homebrewserver.club/).

I made a lot of mistakes along the way - mistakes that hopefully you can avoid. Because of various unforced errors, I ended up trying out three different web server programs (Nginx and Apache, before settling on Caddy) and three different static website builders (Pelican and Jekyll, settling on Hugo). When I was at my wit's end, all I had to do was [ask for help](https://stackoverflow.com/questions/63351978/css-not-loading-for-self-hosted-nginx-with-jekyll-hugo-site/63359674). (Thank you @randomsock!)

### The Physical Server
Remember: there's no such thing as "the cloud." There are just a bunch of computers that someone else owns. This one, however, is owned by me. Following the lead of Low←Tech Magazine, I used an [Olimex Lime2](https://www.olimex.com/wiki/A20-OLinuXino-LIME2)[^board info] running on a variant of Debian (itself a distribution of [Linux](https://en.wikipedia.org/wiki/Linux_distribution)) called Armbian. Following Armbian's instructions, I used Balena Etcher to "flash" [the image](https://www.armbian.com/olimex-lime-2/) onto a MicroSD card.

{{< figure src="/server.png" title="My small Olimex server sits amidst my partner's Buddha collection on a bookcase with a LiPo battery zip-tied to the top." >}}

[^board info]: I chose this board based on the recommendation of Low←Tech Magazine and, as they mention, because of all the advantages related to how it is powered. It can provide additional information and can connect directly to a LiPo battery. Along with the board itself, I purchased the case they make for the board and the correct power supply. Separately, I also purchased a 3.7V 6600mAh Lithium Ion battery pack with a JST 2-pin cable attached. Although they say it is a genuine JST connector, I still have trouble disconnecting it sometimes. Not a big deal - I  don't plan to disconnect it often.

Insert the MicroSD card, plug in your power adapter, connect it your router with an ethernet cable, connect mouse, keyboard, and HDMI, and you're up and running! After my initial configuration (see below) I always connected to the server via SSH, so there was no need to keep it connected to mouse, keyboard, or monitor.[^ssh]

[^ssh]: On my Windows machine, I use Putty and WinSCP to connect to the Lime2 wirelessly from my computer.

My basic configuration of the server included logging in as root (pw: 1234) and updating its password, creating a username and password for myself with `sudo` admin permissions, logging in, and then making sure everything was up to date via `sudo apt-get update && sudo apt-get upgrade`. I then went ahead and [set a Static IP (LAN) address](https://linuxconfig.org/how-to-setup-a-static-ip-address-on-debian-linux) for the Lime2's ethernet port so that it would always be accessible at the same address. I also installed a firewall called UFW and configured it to allow SSH, HTTP, and HTTPS through (`sudo ufw allow 22 80 443`). We'll get into more of the networking stuff a little bit later. 

### The Static Website
Setting up Hugo was simple as could be. I followed [their directions](https://gohugo.io/getting-started/installing#debian-and-ubuntu) to install (`sudo apt-get install hugo`). Then I used the Quick Start documentation, creating a directory for my site (`mkdir`), `cd`-ed into that directory, and created the site using [`hugo new site quickstart`](https://gohugo.io/getting-started/quick-start/#step-2-create-a-new-site). 

For a theme, I am using a [lightly-modified](https://github.com/natehn/blog-theme) version of [Cactus](https://github.com/monkeyWzr/hugo-theme-cactus). Hugo has [plenty of themes available](https://themes.gohugo.io/), as well as information on [how to install them](https://gohugo.io/getting-started/quick-start/#step-3-add-a-theme). All my modifications were done in true amateur fashion - trial and error.[^theme]

[^theme]: It is just simple stuff like changing the copyright line to allow for a Creative Commons license and changing the favicon and logo.

Hugo has plenty more information in their Quick Start guide. Once the site was ready, I ran `hugo` in the main directory to build the site in a directory called `public`. If you've been following along, your root directory will probably something like `home/user/blogfolder/public`. You'll need that info when you set up your webserver.

### Networking
To make sure that you are ready to receive external traffic, you will need to set up a DCHP reservation and port forwarding (ports 80 and 443) in your router. This basically ensures that folks who connect to your router for the purpose of getting to your website will be directed by the router to your server. The specific process for this will depend on your router and Internet Service Provider.

While doing this, go ahead and make a note of the WAN IP Address for your router. You will need this when pointing your domain name at your server. Be aware, unless you set a Static WAN IP address through your Internet Service Provider, it is possible for your WAN address to change. If your website goes down, that could be one of the first things to check. 

### Your Domain Name
First, of course, you should buy a domain name. Then with your domain name registrar, or wherever you manage the DNS records for your domain, make an A record (a.k.a. "address" record) pointing to the WAN IP address of your router. The process for doing this depends on your provider. It can then take 24-48 hours for your new DNS settings to "propogate" and go into effect.

### The Webserver
Caddy will be our webserver. To set up Caddy, we will follow the installation directions for Debian put together by [TecMint](https://www.tecmint.com/install-caddy-web-server-in-centos-ubuntu/).

**Install Caddy:**

```
echo "deb [trusted=yes] https://apt.fury.io/caddy/ /" \
    | sudo tee -a /etc/apt/sources.list.d/caddy-fury.list
sudo apt update
sudo apt install caddy
```

**Start Caddy:**

```
systemctl start caddy
systemctl enable caddy
systemctl status caddy
```

**Configure Caddy:**

Open up the configuration file at `/etc/caddy/Caddyfile` with your favorite text editor (e.g., vim, nano). Change `:80` to your domain (`natehn.com` for example) and the root to the root of your public site, such as `home/user/blogfolder/public`.

**Restart Caddy**

Restart Caddy with this new configuration via `systemctl reload caddy`. Your website should be up and running!

**Note Regarding SSL Certificates**

Caddy should take care of your SSL certificate, which is used for HTTPS, automatically on your behalf. If you have trouble with it, check out [these instructions from Certbot](https://certbot.eff.org/lets-encrypt/debianbuster-other). (I did this out of order and got a certificate back when I was using Nginx as my webserver.)

## Writing

For putting posts together, I recommend learning a simple plaintext syntax called Markdown. Hugo uses Markdown to turn plaintext into html.[^support] It makes writing up an article so much easier. Posts composed using [Markdown's easy syntax](https://www.markdownguide.org/basic-syntax/) and dropped into blog's directory will become low-weight html pages on your static website. Hugo also has a handy [`figure` shortcode](https://gohugo.io/content-management/shortcodes/) to help you insert images.

[^support]: [Hugo Markdown Support](https://www.markdownguide.org/tools/hugo/)

{{< figure src="/tasman.png" title="A beautiful sunrise at a campground near Abel Tasman National Park." >}}

For focused writing, I use a lightweight plaintext editor called [Left](https://hundredrabbits.itch.io/left), by the awesome sailboatin' folks at HundredRabbits. I also use [FocusWriter](https://gottcode.org/focuswriter/) on occasion. But any plaintext editor will do.

Once you have a website up and running, you're at the last step: content. In our modern capitalist internet, the content mills never stop running. Blog posts of a certain length, with certain keywords (and questionable value), are used to optimize companies' search engine position (the proverbial neverending scramble for "SEO"). And in this side-hustle culture, it sometimes feels like you have to compete to survive. (I've certainly felt the pressure before!) 

It doesn't have to be like this. This site is a start. It is a forum: not content, but discussion - even if it is one-way. A place that is open and honest, especially about imperfections and mistakes. Let's see where it leads.
