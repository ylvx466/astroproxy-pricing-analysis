# astroproxy review: real per-GB and per-port costs, KYC and expiry catches, and a per-IP pricing model worth testing first

Most people searching for an astroproxy review aren't curious about the company. They saw a "$3.65/GB" headline somewhere, they have a scraping job or a batch of accounts to keep separate, and they want to know whether the invoice matches the marketing page. The honest answer is that AstroProxy's pricing is more granular than most of its competitors and more layered than most of its competitors, and the layers are where the money goes.

Here's what it actually charges, what it does unusually well, what third-party evidence says, and how a per-IP model like 9Proxy compares on the same jobs.

## What AstroProxy actually is

Armenia-based, running since 2018 out of Yerevan, with a domain registered in July 2018. The network is advertised at 50M+ IPs across 100+ countries, covering three rotating proxy types: residential, mobile (real carrier 4G/5G addresses), and datacenter. HTTP(S) and SOCKS5 are both supported, there's an API, and authentication is either IP whitelist or username/password.

Two things shape every purchase decision here. The billing unit is a **port**, not an account. And new buyers have to clear KYC/AML verification, because Astro sells whitelisted IPs only.

## The rate card, both models at once

| Proxy type | Prepaid traffic | Pay-as-you-go | Port fee |
| --- | --- | --- | --- |
| Residential | from $7.30/GB | from $7.87/GB | $0.30 prepaid / $0.10 PAYG |
| Mobile | from $13.14/GB | from $14.17/GB | same |
| Datacenter | from $3.65/GB | from $3.94/GB | same |

Minimum order is 100 MB, which is genuinely unusual — most providers in this bracket won't sell you less than a gigabyte. Prepaid ports are rented for 30 days and can be extended; leftover traffic is combined when a refill extends the port. Pay-as-you-go charges in 10 MB increments and needs about $0.13 per port sitting on the balance as a minimum.

The two models aren't interchangeable, and the crossover point is lower than most people assume. At low per-port consumption — backup capacity, test configurations, irregular jobs — PAYG wins. Once a port is moving meaningful traffic every month, prepaid is cheaper. Third-party breakdowns put that break-even in the hundreds of megabytes per port per month, which most active workloads blow past in a day.

## Four line items that never fit in a per-GB headline

**Ports are charged on top of traffic.** Ten ports at $0.30 is $3 a month before a single byte moves. The port is the gateway that handles IP rotation, so you pay for concurrency, not consumption.

**City targeting multiplies the base rate by roughly 1.5x.** Country-level targeting doesn't. If your job needs a specific city, budget for that before you build the pipeline around it.

**Prepaid traffic is tied to the port term.** The stated rule is that prepaid service lasts until traffic is used up or the one-month port period ends, with the remainder carried over only if a refill extends the port. On PAYG, ports with no requests for 45 days get archived, and then deleted 14 days later if nobody restores them. Neither of those is a scam — they're standard hygiene — but they change what "I bought 100 GB" means a few months later.

**Discounts go deep, but only for people who commit.** Volume discounts of 2–20% apply at checkout and scale with total traffic or port count, regardless of proxy type or region. On top of that, cumulative top-up discounts kick in based on 30-day top-up totals: 10% above $188, 15% above $1,000, 20% above $1,500, 25% above $2,000. Stack them and the published ceiling is 45% off. The catch is obvious: the attractive headline rates in Astro's own discount guide describe the top of that ladder, not the entry price you'll see on day one.

One detail that works in your favor: Astro bills only the heavier of your two traffic directions, upload or download, instead of summing both. That's an outlier in this market and it can be worth a real percentage depending on traffic shape.

## Where AstroProxy is genuinely strong

Low-commitment testing is the standout. There's a $3 credit for trying any proxy configuration, requested from support, with no time limit on it. Combined with the 100 MB minimum, you can validate a target without a subscription.

Rotation doesn't cost extra — changing your IP via timer, per request, or through the API isn't a billable event. Datacenter access sits at $3.65/GB prepaid, which is cheap for a pool that supports city-level targeting, and mobile IPs are drawn from real carrier ranges rather than being relabelled datacenter blocks.

Public ratings are decent rather than glowing: a 4.4 average across roughly 1,141 reviews on Reviews.io, and 4.8 from 21 reviews on Product Hunt. Independent directory data puts success rates around 97% with an average response time near 1,100 ms — respectable for rotating residential, though your own target sites are the only benchmark that matters.

## Where it gets irritating

**Re-verification.** This is the consistent complaint theme. One Reviews.io reviewer described passing verification, using the service normally, and then losing access to parts of a project for days after a re-verification request that was announced only through a small banner on a dashboard he rarely opened and an email that landed in spam. Product Hunt's AI summary of the product's reviews flags the same pattern — "disruptive re-verification and weak communication." If you're running production traffic through an account, that failure mode deserves a plan.

**Support routes.** Third-party write-ups note that Astro's team responds through Telegram-style messengers rather than a formal ticket queue. Faster when someone's online, worse when you need a paper trail for a billing dispute.

**Volume economics.** Directory analysis of the pricing page says the per-GB rates sit above the cheapest market leaders once you need bulk traffic. The flexibility at the low end is real; the scaling curve isn't aggressive.

**Refund terms.** Some directories list a 72-hour money-back window for Astro. Confirm the current wording at checkout rather than trusting a comparison site's table.

## The sourcing claim deserves its own paragraph

Astro's pitch rests on ethical, consent-based IP acquisition, and it publishes compliance material around that. So a security audit published after the fact is worth reading before you pay a premium on that basis.

Silent Push enumerated AstroProxy's pools over a 72-hour window and observed 117,224 unique IPs: 60,247 residential, 38,762 datacenter, 18,215 mobile. The residential pool was dominated by Russia and Vietnam, which together accounted for over 40% of observed addresses. More to the point, the audit traced the inventory to Peer2Profit, a bandwidth-sharing application that pays participants around $0.28/GB for residential traffic while AstroProxy lists residential at roughly $7.60/GB. The report also states that requests could reach internal network resources, a finding disclosed to the provider before publication.

None of that makes KYC theatre. It does mean the gap between "ethically sourced" as a positioning claim and "ethically sourced" as a verified property of the supply chain is something you should price in yourself rather than take on faith.

## The pricing model question nobody asks first

Everything above is per-gigabyte pricing. That meter is right for some jobs and wrong for others, and the split is predictable: if your requests are small, high-frequency, and rotate constantly — SERP checks, ad verification, geo spot-checks — per-GB is efficient because you consume very little data per request. If you're holding sessions open, pushing bulk payloads, or maintaining hundreds of profiles with unpredictable traffic, per-GB billing punishes the exact behaviour you're paying for.

9Proxy meters the other way. Its core residential product is priced per IP with unlimited bandwidth, IPs you buy never expire, and a separate GB-based line exists for teams that think in traffic instead.

## 9Proxy packages, all of them

| Package | Model | What you get | Price | Validity / notes |
| --- | --- | --- | --- | --- |
| 100 IPs | IP-based | 100 residential IPs, unlimited bandwidth | $24 total ($0.24/IP) | IPs never expire |
| 500 IPs | IP-based | 500 residential IPs, unlimited bandwidth | $72 ($0.144/IP) | IPs never expire |
| 1,000 + 500 bonus IPs | IP-based | 1,500 residential IPs, unlimited bandwidth | $126 ($0.084/IP) | IPs never expire |
| 2,500 IPs | IP-based | 2,500 residential IPs, unlimited bandwidth | $210 ($0.084/IP) | IPs never expire |
| 5,000 IPs | IP-based | 5,000 residential IPs, unlimited bandwidth | $360 ($0.072/IP) | IPs never expire |
| 15,000 IPs | IP-based | 15,000 residential IPs, unlimited bandwidth | $720 ($0.048/IP) | IPs never expire |
| 25,000 IPs | IP-based | 25,000 residential IPs, unlimited bandwidth | $863 ($0.035/IP) | IPs never expire |
| 50,000 IPs | IP-based | 50,000 residential IPs, unlimited bandwidth | $1,438 ($0.029/IP) | IPs never expire |
| 100,000 IPs | Business IP | High-volume IP allocation | $2,300 ($0.023/IP) | IPs never expire |
| 200,000 IPs | Business IP | High-volume IP allocation | $4,140 ($0.021/IP) | IPs never expire |
| 500,000 IPs | Business IP | High-volume IP allocation | $8,625 ($0.018/IP) | IPs never expire |
| 5 GB | GB-based | Pay per GB, unlimited endpoints | $15 ($3.00/GB) | 180-day validity |
| 50 GB + 5 GB bonus | GB-based | Pay per GB, unlimited endpoints | $105 ($2.10/GB) | 180-day validity |
| 100 GB | GB-based | Pay per GB, unlimited endpoints | $150 ($1.50/GB) | 180-day validity |
| 200 GB | GB-based | Pay per GB, unlimited endpoints | $200 ($1.00/GB) | 180-day validity |
| 1,000 GB | GB-based | Pay per GB, unlimited endpoints | $800 ($0.80/GB) | 180-day validity |
| 2,000 GB | GB-based | Pay per GB, unlimited endpoints | $1,500 ($0.75/GB) | 180-day validity |
| 3,000 GB | Enterprise GB | Always-on, no expiry pressure | $2,160 ($0.72/GB) | Never expires |
| 6,000 GB | Enterprise GB | Always-on, no expiry pressure | $4,200 ($0.70/GB) | Never expires |
| 10,000 GB | Enterprise GB | Always-on, no expiry pressure | $6,800 ($0.68/GB) | Never expires |
| Starter bundle | Bundle | 100 IPs + 5 GB | $30 | 180-day traffic validity |
| Popular bundle | Bundle | 1,500 IPs + 50 GB | $180 | 180-day traffic validity |
| Pro bundle | Bundle | 5,000 IPs + 500 GB | $720 | 180-day traffic validity |

Note on timing: 9Proxy raised prices on its IP-based and bundle lines effective June 1, 2026 — the first adjustment since launch — while the GB-based line stayed put. If you're holding a comparison table from early 2026, the IP numbers in it are stale.

Pool size here is 20M+ residential IPs across 90+ locations, with country, city, state, ZIP, and ISP targeting. Protocol support covers HTTP/HTTPS and SOCKS5.

## Running the same job through both meters

Take 500 concurrent, long-lived sessions — the classic multi-account or sustained-scraping profile.

On 9Proxy's IP model, 500 IPs is $72, charged once, with unlimited bandwidth on each and no expiry. Bandwidth spikes cost nothing extra.

On AstroProxy's prepaid residential at $0.30 per port, 500 ports is $150 in port fees per month before a single gigabyte of traffic. Add 200 GB at the list residential rate and you're at roughly $1,610 for the month, less whatever discount tier your top-up volume hits.

Now flip the workload: 5 GB a month spread across thousands of rotating endpoints with almost no data per request. Per-IP pricing is a bad fit there, because you'd be buying IPs you barely touch. Astro's PAYG at $7.87/GB, or a cheaper per-GB specialist, is the sensible purchase. 9Proxy's own 5 GB pack at $15 would also work, but only if you want that specific network.

The useful summary isn't "which provider is better." It's that a per-port plus per-gigabyte bill and a per-IP unlimited-bandwidth bill produce very different totals depending on whether you're buying concurrency or consumption.

## Setting up with either one

AstroProxy: create an account, clear KYC, then message support for the $3 trial credit if you want to test before funding. Larger top-ups in a 30-day window raise your discount tier, so it can pay to batch purchases rather than topping up in small amounts.

9Proxy asks for an account and a package choice, then you pick an access route. There's a Windows desktop app that routes traffic at the OS level, so software without proxy support still works — and that app is also the required path for the IP-based model, which does mean a desktop dependency. Proxy2Web is the no-install option using standard username/password auth, handy for browser checks. ProxyHub and ProxyHub Pro handle mobile device management, and there's a public API for pipelines. SOCKS5 works with anti-detect browsers and proxychains without protocol conversion.

Two operational details are worth knowing before you buy. First, the **Today List**: any proxy used in the previous 24 hours can be reused at no extra cost, which 9Proxy estimates cuts spend by around 30% on recurring tasks. Second, a **60-second replacement policy** credits you for any proxy that fails to connect in its first minute. Reported performance sits around 92–97% success in partner write-ups and closer to 99.5% with roughly 0.6-second average response in one long-run test — treat both as claims until your own target says otherwise.

One honest limitation: IPs on the IP-based plan have natural residential uptime measured in hours up to about 24, not permanent. If your requirement is a fixed address that never moves, neither of these services is what you want. The Auto-Refresh Proxy feature swaps IPs on ports that drop offline, which softens the problem without eliminating it.

👉 [Start with the 100 IP package and check the current invite-code bonus](https://bit.ly/9-Proxy)

## Quick answers

**Is AstroProxy legit?** Yes. It has been trading since 2018, publishes company details, runs real invoicing, and enforces KYC. Legitimate is not the same as well-suited — the friction complaints are about verification interruptions and per-GB rates that don't scale down as fast as rivals'.

**What does AstroProxy cost?** Prepaid rates run $3.65/GB for datacenter, $7.30/GB for residential, and $13.14/GB for mobile, plus $0.30 per port. Pay-as-you-go adds roughly $0.29–$1.03 per GB and drops the port fee to $0.10. City targeting multiplies the base rate by about 1.5x. Discounts stack up to 45% at high volume.

**Does AstroProxy require KYC?** Yes, for access to the residential and mobile pools.

**What's the cheapest way in?** Astro: request the $3 trial credit and test one target. 9Proxy: 100 IPs for $24 with unlimited bandwidth, or 5 GB for $15 if your job is traffic-bound rather than IP-bound.

**Does 9Proxy require documents?** Its own documentation describes access through username/password credentials or an IP whitelist, with no verification step mentioned. That's a description of the documented flow, not a guarantee about every account.

**Which one should you pick?** If you need city- or carrier-level targeting, datacenter inventory, pay-as-you-go metering, or the ability to start at 100 MB, AstroProxy fits. If you need a large number of persistent sessions, unlimited bandwidth per session, and a per-IP bill that doesn't reset every month, 9Proxy's model is the cheaper structure — and at 500 IPs the difference isn't marginal.

The only comparison that settles it is your own batch through both networks in the same hour. Both providers let you get there cheaply enough that guessing isn't necessary.

👉 [Sign up for 9Proxy and lock in the per-IP rate](https://bit.ly/9-Proxy)
