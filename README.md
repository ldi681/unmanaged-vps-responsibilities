# Unmanaged VPS: What You're Responsible For, What "24/7 Support" Really Covers, and How Much Server You Actually Need

Unmanaged VPS means you own everything above the operating system: OS updates, security patches, monitoring, backups, and every application you install. The provider owns the hardware, power, network, and the data centre underneath it. Root access comes with the unmanaged tier, and managed plans typically take it away from you in exchange for someone else doing the patching.

What follows is the part most plan pages skip: where the responsibility line actually sits, what a support ticket gets you on an unmanaged plan, how to size a server without overpaying, and the specific limits worth checking before you pay. SpinServers is used as the working example because its plan page publishes enough detail to talk about concretely.

> **Short version:** if you already administer Linux boxes, an unmanaged KVM plan is the cheapest route to dedicated vCPU and root. SpinServers sells KVM plans from 6 to 32 vCPU on RAID-10 SSD with a 1 Gbps port plus IPv4 and IPv6, and lists the 16 vCPU / 16 GB tier from $74.00 USD monthly. If a failed upgrade at 2 a.m. would cost more than a management fee, buy managed. 👉 [See SpinServers' unmanaged KVM VPS plans and current pricing](https://bit.ly/Spinservers)

## SpinServers' unmanaged VPS lineup

SpinServers splits its KVM virtual servers into two families: Simple Application Servers at the low end and Advanced Application Servers for heavier workloads. Everything runs on KVM virtualisation with RAID-10 SSD storage, a 1 Gbps network port, one IPv4 and one IPv6 address, and a monthly bandwidth allowance that scales with the plan.

| Plan | vCPU / RAM / Storage | Monthly transfer | Price | Order |
| --- | --- | --- | --- | --- |
| Simple Application Server | 6 vCPU / 8 GB DDR4 / 120 GB RAID-10 SSD | 8 TB | Priced at order step | [View plan](https://bit.ly/Spinservers) |
| Simple Application Server | 8 vCPU / 8 GB DDR4 / 160 GB RAID-10 SSD | 10 TB | Priced at order step | [View plan](https://bit.ly/Spinservers) |
| Advanced KVM 12 | 12 vCPU / 12 GB DDR4 / 160 GB SSD | 10 TB | Priced at order step | [View plan](https://bit.ly/Spinservers) |
| Advanced KVM 16 (featured) | 16 vCPU / 16 GB DDR4 / 320 GB RAID-10 SSD | 15 TB | From $74.00 USD monthly | [View plan](https://bit.ly/Spinservers) |
| Advanced Application Server | 32 vCPU / 32 GB RAM / 500 GB SSD | 20 TB | Priced at order step | [View plan](https://bit.ly/Spinservers) |

The plan page only publishes a starting figure for the featured 16 vCPU tier; the smaller and larger configurations show their price when you open them, so confirm the monthly number on the tier you actually want before you commit. Nothing here is annual-only, which matters if you would rather test a host for a month than sign a year.

**One limit that is buried on the page:** port 25 is closed by default on every SpinServers VPS to limit IP abuse. If you plan to run a mail server, you have to open a ticket with a justification, and the company reserves the right to refuse. Anyone migrating an existing mail setup should ask before paying, not after.

## The dividing line: what you manage, what they manage

The split is the same at every host that sells both flavours. The provider keeps the physical layer alive; you keep the software layer alive.

| Job | Unmanaged | Managed |
| --- | --- | --- |
| Root access | Yours | Usually withheld |
| Choice of Linux distribution | Yours | Limited or fixed |
| OS and control panel updates | You | Provider |
| Security patching | You | Provider |
| Monitoring (CPU, disk, uptime) | You | Provider |
| Backups | Optional add-on or your own script | Daily, included |
| Hardware and network SLA | Lower tier | Higher tier |

hosting.com, which sells both, publishes 99.9% for power and network on unmanaged VPS and 99.95% or better on managed, with backups listed as optional on one side and daily on the other. That backup row is the most expensive difference in practice. A nightly image you configure yourself is not the same product as a restore someone else performs for you, and a corrupted database is a bad time to discover which one you bought.

Root access sits on the unmanaged side only. hosting.com states it directly: both tiers get dedicated resources, but full root is available only on unmanaged VPS. If your reason for wanting unmanaged is a kernel module, a custom init system, or a control panel you install yourself, that is the tier you need.

## "24/7 support" on an unmanaged plan: what the ticket actually covers

This is the most misread line in VPS marketing, so here is the plain version from Hostwinds' own FAQ: "Unmanaged VPS services do not come with any technical, management, or administrative support." What the plan guarantees is that the server starts up and stays functional at the level of power, networking, and the connection back to the provider's infrastructure.

The same company also runs real-time monitoring on all VPS plans, opens a support ticket automatically when something looks wrong, staffs chat around the clock, and maintains a documentation library covering common admin tasks. Those two facts sit next to each other without contradiction. Monitoring and infrastructure tickets cover "your node is unreachable" or "the host is down." They do not cover "nginx won't start" or "please configure my firewall." A reasonable test before buying: if the answer to your problem would start with `systemctl`, expect to solve it yourself.

The exit is cheap, which takes pressure off the decision. Hostwinds lets you move from unmanaged to managed with a button in its Cloud Control panel, and after the switch its team handles the technical and administrative work. hosting.com recommends managed VPS for anyone upgrading from shared hosting who wants to keep cPanel, and throws in free migration. Buying unmanaged is not a permanent bet on your own competence.

If you are already comfortable on the command line, the specs matter more than the support tier. 👉 [Compare SpinServers' KVM plans and pick a tier](https://bit.ly/Spinservers)

## How much server do you actually need?

Published ranges across the market give a sense of scale. Hostwinds sells unmanaged VPS from 1 to 16 vCPU and 1 to 96 GB of RAM. Liquid Web's own line runs 2 to 16 vCPU and 2 to 16 GB. InMotion spans 1 to 32 vCPU and 1 to 32 GB. SpinServers starts higher, at 6 vCPU and 8 GB, and tops out at 32 vCPU and 32 GB. Those competitor figures come from a Liquid Web roundup published in August 2025, so treat them as magnitudes rather than today's configurations.

Sizing advice that holds across all of them: buy the tier that fits your workload this week, not the one you might need after a growth spurt. Watch memory and CPU for a fortnight. If usage sits near the ceiling consistently, you sized wrong; if it idles at 15%, you paid for headroom you never touched.

Upgrades are usually less painful than people fear. one.com says plan changes take effect within minutes from its control panel, with no migration and no downtime. hosting.com says resources scale on demand without a rebuild. SpinServers does not publish its upgrade mechanics on the plan page, so ask support how a resize is handled before you pick a small tier as a stepping stone.

Disk is the spec buyers underestimate. A 120 GB RAID-10 array is generous for a web app and tight for anything storing media, logs, or database snapshots. Bandwidth is the other one: 8 TB to 20 TB per month covers most application workloads, and if you expect to push video or run backups off-site, do that arithmetic before ordering.

## When to leave shared hosting, and when to stay

Stay on shared hosting while your site still runs well on it. That is one.com's guidance and it is correct. Moving to a VPS to "get serious" while traffic is flat buys you a maintenance job with no performance payoff.

Two signals justify the move. The first is neighbours: on shared hosting, another site's traffic spike eats into the memory and CPU your pages get. The second is control you cannot get otherwise, either a choice of operating system or server software that shared plans do not permit.

Typical unmanaged customers are developers, SaaS operators, systems administrators, and businesses that already have an IT team. Hostwinds also pitches it as a learning route for people entering IT who want administrator-level experience on a real box. If you want VPS performance without the sysadmin work, managed is the honest answer, and hosting.com says as much on its own unmanaged page.

## Where the money goes

A VPS costs less than a dedicated server and more than shared hosting, and the unmanaged version is cheaper than managed because the provider puts fewer people-hours into it. That gap is the whole business model: you trade your time for their fee.

The comparison worth running is not between two hosts' headline prices, it is between an unmanaged plan and the managed equivalent plus your hourly rate for the hours you will spend on patching, monitoring, and recovery. For a developer already maintaining servers, the unmanaged side wins easily. For a shop owner who would be learning as they go, the arithmetic usually flips within the first incident.

## Before you order

- **Which distributions are available.** Ubuntu 22.04 LTS, Debian 12, and AlmaLinux 9 are the common trio, and hosting.com lists exactly those with reinstall and OS switching from the panel. Confirm your distro before paying.
- **Backups.** Self-managed, an add-on, or included. Hostwinds offers automated nightly backups to object storage with configurable retention and single-file restore, but you configure all of it. That is the unmanaged pattern, not a substitute for managed backup service.
- **Uptime numbers, read carefully.** Hostwinds advertises 99.9999% uptime, hosting.com commits to 99.9% for power and network, Liquid Web's SLA covers 100% network uptime only. Network uptime and whole-machine uptime are different promises, and none of these guarantee your application stays up.
- **Location and data handling.** Where the node physically sits, and whether your data passes through a third-party cloud. one.com, for instance, keeps VPS data in its own ISO 27001-certified European data centres and states it never routes through another provider.
- **Contract length and upgrade path.** Monthly billing with a documented upgrade route beats a discounted annual lock-in for a first VPS.
- **Port 25 and IPv6.** On SpinServers, mail requires a ticket and IPv6 is included by default. Both are worth knowing before you plan a migration.

Final rule by reader type. Running a side project or a single app with modest traffic: take the smallest SpinServers plan (6 vCPU / 8 GB / 120 GB) and watch the graphs for a month. Running production workloads or several services: the 16 vCPU / 16 GB tier at $74.00 monthly is the one with a published price and 320 GB of RAID-10 storage, and it is the sane default for a multi-service box. If you cannot name what you would do with root access, none of these are your plan yet.

👉 [View SpinServers' unmanaged VPS lineup and current tiers](https://bit.ly/Spinservers)
