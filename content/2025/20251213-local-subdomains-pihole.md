title: Forward All Local Server Subdomains Using Pi-Hole
date: 2025-12-13 10:59 -0700
tags: Pi-Hole, Docker, Traefik, dnsmasq

Locally, I run a Pi-Hole to provide ad blocking on the local
network[^2025121301] but I also run a Docker server to which I want to forward
various subdomains (which are then routed to containers using *Træfik*). I had
this set up, but my upgrade from v5 to v6 of Pi-Hole blew this away (as I
needed a new SD card for the Raspberry Pi it was running on) (see also the [v6
release
notes](https://pi-hole.net/blog/2025/02/21/v6-post-release-fixes-and-findings/)).

In way of background, Pi-Hole is running *dnsmasq* under the hood, and so you
can configure it like any *dnsmasq* instance, and this is what I was doing with
Pi-Hole v5: placing configuration files (with the lines below) in text files in
the `/etc/dnsmasq.d/` folder. But with Pi-Hole v6, they actually expose this
directly on the web interface:[^2025121302], so that's where I (re-)set it up.

To wit:

- log in to your Pi-Hole (likely at <http://pi.hole/admin>)
- click the "Settings" dropdown on the left menu
- click on "System" (or really any of the sub-options)
- in the top right, you will see a green toggle that says "Basic". Click on it,
  and it should now be red and say "Expert"
- click on "All Settings" (a new option under "Settings" in the left menu)
- click on the "Miscellaneous" tab along the top
- scroll down to "misc.dnsmasq_lines". This is the setting we want!

Under "misc.dnsmasq_lines", you can add any configuration for *dnsmasq* you
want. But we want to only add a line like this:

```
address=/cool-server.lan/192.168.1.100
```

![misc.dnsmasq_lines]({static}/images/2025/pihole-dnsmasq-lines.png)

`address=` is telling *dnsmasq* (and thus Pi-Hole) that we're changing how this
particular address (or domain name) is being resolved. `/cool-server.lan` is
the name of our server, **and includes all subdomains** (so
`music.cool-server.lan` gets forwarded to the same place) and `/192.168.1.100`
is the server's IP address[^2025121303] and where the address is forwarded to. This assumes
that your server will be able to make sense of what to do with the domain names
(which is what *Træfik* on the server is for).

I also saw some references to using `server=` in lieu of `address=`, and the
two seemed to work the same in my brief testing. However, (I think) `server` is
meant to point to an upstream DNS server (that would then resolve the addresses
forwarded). (See also the [man page for
*dnsmasq*](https://thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html).)

For reference, I am currently running Pi-Hole Core v6.3, FTL v6.4.1, and Web interface v6.4.

I leave it as an exercise for the reader, but I expect this could be leveraged
to provide split-horizon DNS[^2025121304] if wanted.


[^2025121301]: As a side note, it's amazing how much of a difference this
    makes. The internet seems usable at home and surprisingly unreadable at
    times when I'm on the go....
[^2025121302]: Because this is now part of the Pi-Hole configuration this way,
    it should be included in their *Teleporter* backups.
[^2025121303]: You'll want your server to have a static IP address. DHCP
    reservations have worked for me.
[^2025121304]: *Split Horizon DNS* is where certain "public" domain names
    resolve to point to internal servers inside your network, but on the
    internet they point to (different) public servers (or don't resolve at
    all). This could be useful, for example, if you want an SSL certificate
    through Let's Encrypt, which typically requires that they be able to
    resolve the domain name in question, without you putting the "real" server
    online.
