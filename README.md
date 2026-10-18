# Vultr GPU Pricing: Current Rates for Every GPU (from $0.06/hr), Plus Storage, Bandwidth and Discount Rules That Change Your Real Bill

Vultr GPU pricing is unusually public for the neocloud market — published rates, bookable without a "contact sales" form. The short version: single-GPU VMs run from $0.06/hr (a fractional slice of an NVIDIA A16) up to $2.40/hr for an A100 PCIe, the GH200 costs $1.99/hr, and the 8-GPU HGX H100 bare-metal node runs about $23.92/hr, roughly $2.99 per GPU. Everything is billed hourly in USD with no minimum commitment.

Sticker rates are only half the answer, though. The same GPU can cost 30%+ more depending on region, the headline "$0.06/hr" is a 2 GB slice of a card rather than a full GPU, and the H100 mostly sells as an entire 8-GPU node whether you need eight GPUs or not. This guide walks through the full rate card, the fees that don't show up in comparison tables, every discount on offer, and where Vultr lands against RunPod, Lambda, Vast.AI and the hyperscalers.

> **Fast take:** for most AI work, the **L40S at $1.67/hr** is Vultr's best-value full GPU for inference, the **GH200 at $1.99/hr** wins on memory-bound LLM inference, and the **A100 PCIe at $2.40/hr** covers most fine-tuning jobs. New accounts get up to $300 in credits valid for 30 days.
>
> 👉 [Check current Vultr GPU rates and start with the free credit](https://bit.ly/VulTR)

## What Vultr charges for every GPU right now

Vultr's lineup splits into two families: single-GPU virtual machines (with fractional slices available on the A16 and A40) and multi-GPU bare-metal nodes for training. All rates below are on-demand, in USD, billed per hour, cross-checked across tracker snapshots from August–September 2026. Vultr adjusts prices with availability, so treat these as planning numbers and confirm the live figure in the console.

### Single-GPU VMs and slices

| GPU | VRAM | On-demand rate | Best for | Book |
| --- | --- | --- | --- | --- |
| NVIDIA A16 | 16 GB | from $0.06 (2 GB slice); $0.47 full card | VDI, light rendering, tiny workloads | [ Book this GPU](https://bit.ly/VulTR) |
| NVIDIA A40 | 48 GB | slices from $0.07; $1.71 full card | Rendering, VDI, media pipelines | [ Book this GPU](https://bit.ly/VulTR) |
| NVIDIA L40S | 48 GB | $1.67 | Image/video generation, general inference | [ Book this GPU](https://bit.ly/VulTR) |
| NVIDIA A100 PCIe | 80 GB | $2.40 (24 vCPUs, 80 GB RAM) | Fine-tuning, heavier inference | [ Book this GPU](https://bit.ly/VulTR) |
| NVIDIA GH200 | 96 GB | $1.99 | Large-model inference on unified memory | [ Book this GPU](https://bit.ly/VulTR) |
| NVIDIA T4 | 16 GB | $0.90 (about $0.68/hr on annual billing) | Light inference, testing | [ Book this GPU](https://bit.ly/VulTR) |

About that $0.06 entry point: it's a 2 GB slice of an A16, not a whole card. Vultr sells fractional GPU slices on the A16 and A40 lines, which is why the cheapest tracked configuration costs less than a coffee per week. The full 16 GB A16 runs $0.47/hr, and A40 slices climb from $0.07 (2 GB) to $0.86 (24 GB) before you reach the full 48 GB card at $1.71. Fine for VDI and small models; useless for anything that needs real VRAM.

### Multi-GPU and bare-metal nodes

| Node | GPUs | Per-GPU rate | Node rate/hr | Book |
| --- | --- | --- | --- | --- |
| A100 bare metal | 4× | ~$2.40 | $9.59 | [ Book this node](https://bit.ly/VulTR) |
| A100 bare metal (spot) | 8× | ~$1.49 | $11.92 | [ Book this node](https://bit.ly/VulTR) |
| HGX A100 SXM | 8× | $2.80 | ~$22.40 | [ Book this node](https://bit.ly/VulTR) |
| HGX H100 | 8× | $2.99 | $23.92 | [ Book this node](https://bit.ly/VulTR) |
| HGX B200 | 8× | ~$3.50* | ~$28.00 | [ Book this node](https://bit.ly/VulTR) |
| AMD MI300X | 8× | $1.85 | ~$14.80 | [ Book this node](https://bit.ly/VulTR) |
| AMD MI325X | 8× | $2.00 | $16.00 | [ Book this node](https://bit.ly/VulTR) |
| AMD MI355X | 8× | $2.59 | $20.72 | [ Book this node](https://bit.ly/VulTR) |

*B200 was tracked at $3.50/GPU-hr in late September 2026; an earlier 2026 review listed $2.99. The rate has moved, so check the console before budgeting.

## The packaging catch most price lists skip

Vultr's self-serve H100 product is, in practice, an 8-GPU HGX bare-metal server at about $23.92/hr — that's your floor whether you use one GPU or all eight. Several sites quote "$2.30–2.99 per H100 hour" without mentioning this, which makes the card look more accessible than it may be.

Here's where the confusion comes from. DeployBase tracks the full node at $23.92/hr (~$2.99 per GPU). ComputePrices separately lists an "H100 SXM" line at $2.30 per GPU-hour on a per-GPU VM basis. If that config is actually available in your region, it's the cheaper way in; if the console only offers the full chassis, $23.92/hr is what you'll pay. Check before you plan a run around a single card.

👉 [See which H100 configurations are bookable right now](https://bit.ly/VulTR)

The A100 tells a cleaner story: the PCIe version costs $2.40/hr while the SXM-based HGX node runs $2.80 per GPU-hour, and that ~40-cent gap is the NVLink premium — you pay more for the higher inter-GPU bandwidth that multi-GPU training actually needs. The B200 is the volatile one, moving between roughly $2.99 and $3.50 per GPU-hour across 2026 tracker snapshots.

## What a Vultr GPU actually costs per month

At 24/7 usage (about 730 hours a month), the sticker rates translate to:

- **L40S:** ~$1,220/month
- **GH200:** ~$1,453/month
- **A100 PCIe:** ~$1,750/month
- **8× H100 node:** ~$17,460/month

Then the add-ons. GPU instances include NVMe storage (350 GB up to 61 TB depending on plan), and extra Block Storage runs $0.10/GB/month — roughly $100 per TB per year, which sits on the high side among cloud providers. Ingress is free; one recent review lists 2 TB of free monthly egress, and outbound traffic beyond included allowances has been tracked at about $0.01/GB. That's cheap by cloud standards — AWS charges around $0.09/GB for the same thing — but downloading large datasets repeatedly still adds up.

Region matters more than most comparison tables admit. New Jersey is the pricing baseline; tracked spreads put Los Angeles at +5–10%, London at +15–20%, Singapore at +25–30% and Sydney at +30–35%. The same A100 PCIe that costs $2.40 in the US runs about $3.20 in Sydney. Unless you're serving users in a specific region, the US data centers are where the value is.

One small mercy: stopped instances stop billing for compute. Storage charges continue, which is worth remembering if you park a box mid-project.

## Every way to pay less than the sticker rate

Four levers, in order of savings: reserved terms, annual prepayment, spot instances, and region choice. Reserved pricing is the big one and the least-discussed:

| GPU | Term | Reserved $/GPU-hr | On-demand | Savings |
| --- | --- | --- | --- | --- |
| L40S | 36 months | $0.848 | $1.671 | ~49% |
| A100 PCIe | 36 months | $1.290 | $2.397 | ~46% |
| HGX A100 | 36 months | $1.490 | $2.800 | ~47% |
| HGX H100 | 36 months | $2.300 | $2.990 | ~23% |
| MI355X | 48 months | $2.290 | $2.590 | ~12% |
| MI300X | 24 months | $1.850 | $1.850 | 0% |

Two things jump out. The L40S reserved deal at $0.848/hr is the single best discount on the board — less than half price for a 36-month commitment. And the MI300X reserved rate matches its on-demand price exactly, so there is no reason to lock that one in; stay hourly.

Annual prepayment works out to roughly 25% off per DeployBase's estimate: an A100 PCIe running 24/7 drops from ~$20,998/year at $2.397/hr to about $15,768 at ~$1.80/hr, saving around $5,230.

Spot pricing exists, mainly on the AMD side. The MI300X, MI325X and MI355X all come as preemptible plans (added in December 2025), and trackers show spot rates on bare-metal nodes too — MI325X at $16.00/node, MI355X at $20.72/node, and an 8× A100 bare-metal spot node at $11.92/hr. That last one works out to about $1.49 per A100-hour, the cheapest A100 access anywhere on Vultr. Don't expect spot on the NVIDIA VMs; the L40S, A100 and GH200 show no spot option in tracked data.

Before signing any of this, burn the $300 credit on hourly billing and see whether the workload actually holds up.

👉 [Compare on-demand and committed rates for your GPU](https://bit.ly/VulTR)

## Vultr GPU pricing vs RunPod, Lambda, Vast.AI and the big clouds

Vultr sits in the middle of the market: cheaper than AWS and Google Cloud on A100 capacity, pricier than RunPod, Lambda or Vast.AI, and competitive on H100 nodes against CoreWeave. Tracked per-GPU rates from DeployBase's comparison:

| GPU (per GPU) | Vultr | RunPod | Lambda | Vast.AI | AWS | Google Cloud |
| --- | --- | --- | --- | --- | --- | --- |
| A100 PCIe 80 GB | $2.40 | $1.39 | $1.48 | $0.80–1.50 | ~$3.00–4.00 | ~$3.67 |
| H100 SXM | $2.99 (8-GPU node) | — | $3.78 | — | — | — |
| T4 16 GB | $0.90 | — | — | $0.15–0.30 | $0.35 | $0.35 |

CoreWeave's 8× H100 node tracked at $49.24/hr, more than double Vultr's $23.92. DigitalOcean's MI300X at $1.99/hr matches the GH200's price exactly, if you'd rather take the AMD route.

So what does the premium over RunPod and Lambda buy? Thirty-two regions across six continents, VM and bare-metal deployment, a managed Kubernetes engine, serverless inference at $0.55 per million input tokens, preinstalled PyTorch/TensorFlow/CUDA/ROCm stacks, an advertised 100% uptime SLA, compliance certifications including SOC 2 with HIPAA, PCI DSS and the ISO 27001 family, NVIDIA Preferred Cloud Partner status, and payment options most neoclouds don't bother with — PayPal, crypto via BitPay, Alipay, UnionPay, wire transfer.

If raw cost is the only criterion, Vast.AI wins by a wide margin, especially on T4s where it runs 3–6× cheaper. RunPod and Lambda undercut Vultr by roughly a dollar an hour on the A100. What you're paying extra for at Vultr is fixed published rates, a global footprint bigger than most budget clouds, and compliance paperwork that peer-to-peer marketplaces can't provide. Regulated industries and production teams tend to care about that; hobbyists usually don't.

## Prices are public. Capacity is another matter

A published rate card guarantees a number, not a GPU. One availability tracker's 30-day history from mid-August 2026 showed A16 plans with the strongest supply — up to 100% availability — while the L40S was bookable only around 8% of the covered time, A40 stock was effectively absent, and several bare-metal nodes including the A100, B200 and MI325X/MI355X showed out of capacity at the last check.

The GH200 helps Vultr's case here: it launched across the entire 32-location global footprint rather than a few flagship regions, which is rare for top-tier accelerators. Bare metal is the opposite — check stock for your specific region before building a training plan around a node, because the cheap spot listings tend to disappear first.

## Which Vultr GPU to rent, by workload

- **Light inference and testing:** T4 at $0.90/hr, or an A16 slice from $0.06 if 2 GB of VRAM is genuinely enough. It usually isn't for modern diffusion models.
- **Image/video generation and everyday inference:** L40S at $1.67/hr — 48 GB of VRAM at the best full-GPU price on the platform. [👉 Rent the L40S](https://bit.ly/VulTR) and you're paying less per hour than an A100 costs almost anywhere.
- **Memory-bound LLM inference:** GH200 at $1.99/hr. The Grace Hopper superchip pairs HBM with 480 GB of LPDDR5X unified memory, which is why it punches above its price class for big-context inference.
- **Fine-tuning on a single GPU:** A100 PCIe at $2.40/hr, with 24 vCPUs and 80 GB of system RAM alongside.
- **Distributed training:** the 8× H100 node at $23.92/hr; if your workload tolerates interruptions, the 8× A100 spot node at $11.92/hr cuts the bill in half.
- **Maximum VRAM per dollar:** the MI300X node at ~$14.80/hr gives you 1,536 GB of aggregate VRAM — nothing else on the board comes close.
- **Running 24/7 for a year or more:** reserved terms, where the L40S at $0.848/hr is the standout.

## Vultr GPU pricing FAQ

**Is Vultr GPU billing hourly or monthly?**
Hourly, with no minimum commitment. There's no separate cheaper monthly price — a month is just 24/7 hourly usage, about 730 hours. The real monthly discount lives in annual prepayment (~25%) or reserved terms.

**What is the cheapest GPU on Vultr?**
A 2 GB slice of an A16 at $0.06/hr. The cheapest full GPU for real AI work is the L40S at $1.67/hr; the T4 at $0.90/hr handles light inference but is an older card.

**Does Vultr offer a free trial for GPU instances?**
There's no time-limited trial as such, but recent reviews confirm new accounts get up to $300 in credits valid for 30 days — enough to test most single-GPU setups before spending anything.

**Can I rent a single H100 on Vultr?**
The reliably tracked self-serve product is the full 8-GPU HGX node at about $23.92/hr. ComputePrices lists a per-GPU H100 SXM line at $2.30/hr, so single-GPU access may exist in some regions — verify in the console, and if only the node is offered, that $23.92/hr is your floor.

**Does Vultr have spot GPU pricing?**
Yes, mainly on AMD: MI300X, MI325X and MI355X come as preemptible plans, and bare-metal spot nodes include the 8× A100 at $11.92/hr and B200 at $25.60/hr. NVIDIA VMs like the L40S and GH200 show no spot option in tracked data.

**How much do storage and bandwidth cost?**
Instances include NVMe storage; extra Block Storage is $0.10/GB/month. Ingress is free, a recent review lists 2 TB of free monthly egress, and outbound traffic beyond allowances has been tracked at about $0.01/GB.

## Before you click buy

Four things to confirm, in order:

1. The live rate for your region in the console — the same card can cost 5–35% more outside the US.
2. Actual stock for the node you want, especially bare metal and spot listings.
3. Whether the $300 credit covers your test plan before you commit to reserved or annual terms.
4. That you've budgeted for storage, which keeps billing even when a stopped instance sits idle.

If you want a second opinion on any number before committing, DeployBase, ComputePrices and GPUFinder all track Vultr and mostly agree within a few cents. When the workload is picked, [👉 open Vultr's GPU pricing page, pick a US region, and start on the free credit](https://bit.ly/VulTR).
