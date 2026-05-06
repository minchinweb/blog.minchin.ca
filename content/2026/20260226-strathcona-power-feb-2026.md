title: Building Strathcona Power -- February 2026
date: 2026-02-26 14:38:25-0700
category: Strathcona Power
tags: build in public, Strathcona Power


This is a continuation of series of posts on building up Strathcona Power.
(Read [last month's update]({filename}20260114-strathcona-power-jan-2026.md)
here.)

To recap, I'm building a boutique energy retailer ([Strathcona
Power](https://strathconapower.ca)) to provide a human touch, and that
reinvests back in to the community by being a part of it. Be a part of it!

## Pricing Update

This section is general notes on electricity and natural gas pricing in Alberta.

Pricing has been up and down over the last month, but the biggest changes have
been a drop in the 5 year electricity hedges.

Personally, I'm still a fan of floating prices for both power and gas.

Our pricing for February:

| Term                  |     Electricity | Trend                                   | Natural Gas | Trend                                   |
| --------------------- | --------------: | :-------------------------------------- | ----------: | :-------------------------------------- |
| Floating[^2026022501] | ~5.1 &cent;/kWh | <i class="fa-solid fa-arrow-right"></i> |   ~$3.24/GJ | <i class="fa-solid fa-arrow-down"></i>  |
| 1 year Fixed          | 8.19 &cent;/kWh | <i class="fa-solid fa-arrow-up"></i>    |    $3.69/GJ | <i class="fa-solid fa-arrow-up"></i>    |
| 2 year Fixed          | 8.39 &cent;/kWh | <i class="fa-solid fa-arrow-down"></i>  |    $3.99/GJ | <i class="fa-solid fa-arrow-right"></i> |
| 3 year Fixed          | 9.69 &cent;/kWh | <i class="fa-solid fa-arrow-up"></i>    |    $3.99/GJ | <i class="fa-solid fa-arrow-right"></i> |
| 5 year Fixed          | 9.69 &cent;/kWh | <i class="fa-solid fa-arrow-down"></i>  |    $3.99/GJ | <i class="fa-solid fa-arrow-right"></i> |

One of the more interesting developments in the broader industry (although not
directly related to retail pricing, yet anyway), is a multi-million dollar sale
of a "connection allotment".[^2026022502] When you want to connect a big
project (like an AI data center) to the grid, there's an approval process (that
can take years in "normal" times). However, with the current AI-driven boom,
there's demand for permission to connect 21,100 MW of new load to the grid
(compare with the current max provincial demand of ~11,000 MW), so AESO,
responsible for grid stability, announced that there was space for 1,200 MW on
the existing grid, but anything more than that would have to wait till they
figure out how to support that much new load. Thus, anyone with an existing
connection allotment has something precious that might not otherwise be
available for years to come.

I think for those dealing with this, the Bitcoin craze of a few years back is
still top of mind. The concern with Bitcoin mines, like AI data centers, are
looking for huge amounts of power, which require a serious build out of
transmission infrastructure. Traditionally, that infrastructure has been paid
for by the wire companies,[^2026022503] and they collect fees over the next ~20
years to get paid back. But are the Bitcoin mines and the AI data centers going
to be here for 20+ years? or will they evaporate when their hardware is
obsolete is 4 years? and who gets stuck with the bill then?

<a id="datacenter-generation"></a>

Also floating around is the question of where 21,100 MW of new power
generation going to come from? The approval process and building of new plants
is measured in years, and we're talking about more than doubling the current
generation fleet.[^2026022504]


<a id="retailing-progress"></a>

## Retailing Progress

The retailing business is growing slowly, up five sites to a total of 86. This
is much slower than I'd like, but also probably faster than I have a right to
do to how limited time I've been able to put towards it.

The Backend's service agreement is now live. They took long enough on their
side getting it signed that they decided to push back the start date, and thus
all following deadlines (for site counts) by a month, for which I'm grateful.
Also because of this, I completely reworked the admin fee pricing. Previously,
the admin fee was a combination of a "monthly fee" (through prorated daily)
plus "daily fees"; the new agreement added a "tax" on daily fees, and so I've
moved it all into the *monthly fee*, which isn't similarly "taxed", plus I hope
this is clearer pricing all around. The pricing is the same overall (after the
20% hike in my fees from the new service agreement), but presented
differently.[^2026022505] I wonder if people look much at the monthly fees, or
just the per kWh and per GJ pricing.

I also undertook work to gather my historical averages for my floating prices;
why the Backend doesn't provide these is beyond me (in theory, they already
have the data!). I was surprised to discover that the vast majority of
customers are on fixed prices. Historic pricing for electricity came in at
6.2&cent;/kWh[^2026022506] and for natural gas at $2.87/GJ.[^2026022507]

I sadly haven been able to launch any new marketing efforts, as my time has
been spent with generation paperwork, and haven't even figured out where best
to crosspost these updates. Hopefully, that is something that can change this
month.

## Generation Progress

A secondary line of the business I've been focused on is building my own
generation capacity, to complement the retail sales.

<!-- PELICAN_BEGIN_SUMMARY -->
Most of this past month has been spent working on getting more generation
online. It is a frustratingly long process, with far too much
paperwork.<!-- read more -->[^2026022508]

For my first 10 kW of generation, I have the connection and purchase agreements
in place, and am now waiting for the loan agreement to come through (hopefully)
in this coming month, and then construction can start at the tail end of March
if temperatures are up. I got the upgraded gas meter install yesterday, which
is exciting as it's first physical piece of this project to have happened. I
expect income to start flowing eight to ten weeks after construction completes
(so mid-June?).

I've also started the process for the next tranche of ~70 kW of generation. This
involved visiting each site three times over two weeks, and didn't leave time
for much else. I have financing applications in for half of them, and have
started on the connection agreements for all these sites (yeah, more
paperwork?? /s).

I've also been looking as some possible larger sites, with 50 to 150 kW at a
single site, but possible future projects are starting to be seriously
constrained by available financing. These would bring down the per kW upfront
costs, but they are much less straightforward, likely requiring a tenant
partner to make them work. The income possibilities are tempting so I keep
coming back, but they are a play that will take longer to get set up, with a
different financial model than what I've been using for the 10 kW sites....

## Current KPI's

| KPI               | Status             | Trend                                      | Target Date      |
| ----------------- | ------------------ | ------------------------------------------ | ---------------- |
| Site Count        | 86 / 120           | <i class="fa-solid fa-arrow-up"></i> 5 / 7 | end of July 2026 |
| Generation Online | 0 / 50 kW          | <i class="fa-solid fa-arrow-right"></i>    |                  |
| ARR[^2026022509]  | (negative) / $100k | <i class="fa-solid fa-arrow-down"></i>     |                  |

To hit the initial site count KPI, I only need to add an additional ~7
sites/month. Future targets will be more demanding, but for now, this is my
focus.

For generation, I'm still waiting for the ground to thaw for the first
installation.

ARR is particularly low at this point because I'm paying onboarding costs for
new retailing sites, and on the generation side, I'm paying interest on upfront
installation costs, but it isn't generated any income yet.

## Review of Last Month's Plans

- **finish rolling out our new logo** -- incomplete. I've updated the website
  and email footers, but need to push it to the bills, UCA Helps, and our
  sign-up portal.
- continue working on my **personal sales efforts**. -- I went to one networking event, so progress!
- **submit my funding application for generation Site 1**. -- Done!
- **review my list of additional sites for generation**. -- Done!
- look into **automation for the business**. -- tinkered a little, but nothing has been launched yet.
- **review the Company's online presence** -- haven't started yet.

## Plans for the Coming Month

- (continue) roll out of new logo. The billing platform, UCA Helps, and the
  signup portal.
- (start) review of the Company's online presence. I have several drafts of
  pieces I want to add to the website.
- complete funding and connection agreements for the next tranche
  of generation sites.

I would like to do more, but also looking at what I actually got done last
month, I need to be circumspect to not burn myself out.

## How You Can Help

I'm grateful for your help in growing the [Strathcona
Power](https://strathconapower.ca). If you live in Alberta, please [sign
up](https://strathconapower.ca/signup) for electricity and natural gas, or send
me your bill (to
[William@StrathconaPower.ca](mailto:william@strathconapower.ca)) and I can run
a bill comparison.

Till next month,  
-- William, *El Presidente* of Strathcona Power


[^2026022501]: This is approximate January retail pricing. Floating prices can
    and do change month to month, and vary slightly between wire areas.
[^2026022502]: CBC has [some
    coverage](https://www.cbc.ca/news/canada/calgary/albertas-ai-data-centre-boom-unleashes-gold-rush-for-electricity-allotments-9.7089179),
    but all the companies involved have super generic sounding names, so it's
    hard to know that the final project will actually look like.
[^2026022503]: Fortis and Atco are the biggest two, but also Epcor, Enmax, etc.
[^2026022504]: currently ~16,000 MW
[^2026022505]: There is a whole tangent here about pricing clarity. Matt
    Stoller's BIG newsletter, which focuses on the economic harms of
    monopolies, did a [recent
    article](https://www.thebignewsletter.com/p/the-one-simple-thing-that-makes-the)
    on the seemly simple question of "How much does it cost?" and how monopoly
    providers have made that question very had to answer.

    A big part of the issue is that if a company is making its money off of
    junk fees (rather than the list price), their list price is lower and so
    they can advertise this lower price and win business off the back of this
    "lower price". Then all the competitors are forced into the same game, as
    "bad pricing drives out good [pricing]" (hat tip to
    [Gresham](https://en.wikipedia.org/wiki/Gresham%27s_law)).

    One place where this has already appeared in this industry is the other
    major backend has rolled their backend transaction charge (untransparently)
    into the "wholesale price" for power and gas. So they are able to advertise
    a floating price of "wholesale + 0.37&cent;/kwh" which is, at the end of
    the day, the same final price as my "wholesale + 1&cent;/kWh" rate.
    Considering that lots of times pricing is all within 1/10 &cent;/kWh....

    Have we gotten to the point where posting a straightforward price is now a
    *political* statement??

    It sucks all around, and it's not obvious what to do about it. In theory,
    UCA Helps is supposed to provide something here, but two months ago when I
    was reviewing prices, the cheapest gas price was *negative*, so please
    forgive me my hesitancy that they'll be the ones to resolve this.
[^2026022506]: over the last nine months, which is all the history I have.
[^2026022507]: over the last three years.
[^2026022508]: and I remind myself, I picked these projects for how
    comparatively straightforward their paperwork is. I expect the process to
    take ~12 weeks, compared to 5 years for a "traditional" generation
    connection process.
[^2026022509]: *Annualized Recurring Revenue*. Basically an assumption of annual
    revenue, based on last month's topline income. This combines both the
    retailing and the generation arms of the Company.
