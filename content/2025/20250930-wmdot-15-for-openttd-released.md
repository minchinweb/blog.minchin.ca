Title: WmDOT v15 (and MetaLibrary v11) for OpenTTD released
Date: 2025-09-30 20:08 -0600
Author: Wm. Minchin
Tags: WmDOT, MetaLibrary, NoAI, OpenTTD, Releases
Category: MetaLibrary
image: images/2025/wmdot-15-streetcars.png

After over a dozen years, I'm releasing an update to *WmDOT* (to v15). This
update brings lots of bug fixers[^2025093001], improved ship
selection[^2025093002], and introduces basic streetcar operations[^2025093003]
(although off by default). I'm also releasing an update to my related
*MetaLibrary* (to v11) at the same time.

WmDOT is an AI for [OpenTTD](http://www.openttd.org/), a game in the genre of
classic tycoon games. It was a project I started back in 2010, but hasn't seen
many updates since 2013. When I originally stated this, my plan was to build a
competitive AI, but the task -- particularly rail pathfinding -- proved to be
more involved that I expected, and so WmDOT ended up as a sort of "highway"
department to build road between towns. I had added ship building previously to
provide a bit of income, and also to start building the code needed for
actually managing money-making routes. Every so often, I still think about
releasing a competitive AI (tentatively named the "Edmonton, Yukon & Pacific",
after a "real" railway that went effectively nowhere), but the nut I haven't
cracked yet remains (bidirectional) railroad pathfinding.

I hadn't played OpenTTD in a while when I started this update, so I was
delighted to see the games has continued to improve! One of the interesting
directions is it seems that the player base (or at least those that create the
trainsets) are in favour of maintaining (relatively) low speed cargo networks
(capped at ~160 km/h) separate from higher speed "express" networks (carrying
passengers, mail, and valuables). Personally, my play style was to build one
single network, tieing all the industries (and towns) together and then slowly
upgrading the interchanges to support increading networks speeds. The monorail
and maglev systems also seems slightly hokey to certain players; maybe (someday)
I'll have to realease a trainset that revolves around this "always a faster
network" gameplay.

As for *MetaLibrary*, it is a collection support functions for WmDOT, and so
many of the above mentioned updates are actual through updates to *MetaLibrary*
code. The [documentation for
MetaLibrary](http://minchin.ca/openttd-metalibrary/) has also been updated.

Another fun tidbit with this release was that the original was mostly written
while I was on a working holidays of sorts in a French coastal town; this
update was written while I was again back in that same town on vacation. Maybe
I need to visit France more often? :)

[^2025093001]: In particular:

    - (Attempt to) fix crash where the Ship Pathfinder returned `null` for buoy
      count (see [Issues
      #15](https://github.com/minchinweb/openttd-wmdot/issues/15) and
      [#17](https://github.com/minchinweb/openttd-wmdot/issues/17)).
    - Fix logging crash in OpHibernia if one of the depots was unbuilt (see [Issue
      #18](https://github.com/minchinweb/openttd-wmdot/issues/18)).
    - Fix the Freeway builder so it is consistently right-handed (see [Issue
      #10](https://github.com/minchinweb/openttd-wmdot/issues/10)).
    - Fix a crash if the HQ Town had too small a population.

[^2025093002]: unprofitable routes should be skipped, and ships should be
better sized to their route.

[^2025093003]: Currently, it only builds in the "Headquarters Town", and so the
resulting routes are too short to generate meaningful profits. You can turn it
on in the AI settings if you want to see it in action.

    The header image shows this in action!
