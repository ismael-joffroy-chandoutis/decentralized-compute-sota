## Mutualizing compute: commons, co-ops, and the reciprocity spectrum

> **One-line verdict.** Sharing compute outside a hyperscaler is a *solved problem in the commons* - there are mature, working systems for it. But the clean "earn idle, draw when busy, net-settle on a single balance" **product** only exists inside token economies, and there it reintroduces rent. For a 3–6 person artist-researcher collective, the most reliable virtuous circle is a **self-built** one: pool real hardware, share it internally by a non-monetary fair-use ledger, keep money out of the reciprocity layer, and apply in parallel to free public credits.

### 1. Four governance families (pick by trust radius, not by hype)

| Family | Live example | How reciprocity works | Money? | Free-rider / Sybil defense | Fit for a small collective |
|---|---|---|---|---|---|
| **Non-monetary reciprocity commons** | AI Horde (Haidra/dbzer0) | "Kudos": complete a job → earn its kudos value; idle-but-online → trickle every 10 min. Kudos buy **queue priority, never exclusion** | **No** (selling kudos is a ToS violation) | Negative balance tolerated → just deprioritized; registered users start ≥25 kudos vs 0 anonymous | **Best template** for "lend GPU, get priority back" |
| **Contribute-to-use credit + anti-cheat** | BOINC, Folding@home | Donated work earns credit ("cobblestones"/points) | No | **Replication-by-consensus**: each job on 2+ hosts, credit only on quorum | Lesson to copy, not a product to join |
| **Academic / research federations** | OSG, EGI; "condo" Slurm clusters | Idle cycles preemptible by all; owners keep top priority via fairshare weighted by investment | No | Institutional identity; central scheduler | Realistic via EGI/EOSC + FR/EU routes |
| **Token-incentivized DePIN** | io.net, Akash, Render, Aethir | One token to **both supply and consume**: earn by hosting, spend on your own jobs | **Yes (token)** | Cryptographic: slashing/banning on failed uptime/verification | Only true one-balance circle - but carries price/slashing/rent risk |

Sources: AI Horde [FAQ](https://github.com/Haidra-Org/AI-Horde/blob/main/FAQ.md) and [kudos docs](https://horde-sdk.readthedocs.io/en/latest/haidra-assets/docs/kudos/); [dbzer0 kudos-economy blog](https://dbzer0.com/blog/the-kudos-based-economy-for-the-koboldai-horde/); BOINC [validation](https://boinc.berkeley.edu/trac/wiki/ValidationSimple) and [adaptive replication](https://boinc.berkeley.edu/trac/wiki/AdaptiveReplication); [OSG](https://osg-htc.org/); [EGI 1M-core milestone](https://www.egi.eu/article/the-egi-federation-reaches-1000000-cores/).

### 2. AI Horde - the cleanest reciprocal template (no money, no accounting overhead)

The most directly copyable model. A requester's job is assigned a kudos value; "if the request is allowed and is successfully completed by a worker, that worker is awarded the same number of kudos," and "you will also generate kudos every 10 minutes your worker stays online" - so **being available is itself rewarded** ([FAQ](https://github.com/Haidra-Org/AI-Horde/blob/main/FAQ.md)). The design choices that make it durable:

- **Not a currency.** "Kudos is inherently valueless and we do not allow anyone exchanging kudos for money" - the same rule applies to crypto. "The Kudos is merely a prioritization mechanism, **not a currency**" ([FAQ](https://github.com/Haidra-Org/AI-Horde/blob/main/FAQ.md)). Kudos can be **freely gifted** (`api/v2/transfer`), **never expire**, and a higher balance only buys **higher queue priority**, never exclusive access ([kudos docs](https://horde-sdk.readthedocs.io/en/latest/haidra-assets/docs/kudos/)).
- **Free-riding is deliberately tolerated.** "You can still use this service even if you don't have any Kudos. You simply go negative, which represents your 'debt' to the community"; the shared Anonymous account "simply keeps going more and more in negative Kudos" - which only sorts its requests to the back of the priority queue ([dbzer0 blog](https://dbzer0.com/blog/the-kudos-based-economy-for-the-koboldai-horde/)).
- **Tiny anti-Sybil nudge.** Registered users start with ≥25 kudos, anonymous with 0 ([kudos docs](https://horde-sdk.readthedocs.io/en/latest/haidra-assets/docs/kudos/)).

The recurring **success pattern** across all four families: *priority-not-exclusion* (Horde), *redundant verification* (BOINC), *idle-cycle preemption with weighted fairshare* (condo/OSG).

### 3. The reciprocity spectrum - does a "one-balance virtuous circle" exist?

| Band | Examples | Earn and spend on **one** balance? | Honest status |
|---|---|---|---|
| Pure mutual aid (no money/token) | BOINC, Folding@home, **Petals** | No claim on compute | Real commons, best-effort, **no SLA**. Petals' reward for hosting 10+ blocks is your name on the swarm monitor "as a way to say thanks" |
| Marketplace, shared identity, **no net-settle** | **Vast.ai**, RunPod | No - roles are **separated** | Most practical today, but **DIY** reciprocity |
| Non-crypto points/balance | **Salad**, ShareAI | Largely separate ledgers | Closer to a circle; earn side from "real workloads… not blockchain or mining" |
| **Token DePIN** | io.net, Akash, Render, Aethir | **Yes** - same token both ways | Only true one-balance circle; bundled with price risk, slashing, **rent dynamic** |

- **Vast.ai actively separates the two roles** for payout integrity: "Hosting requires a separate account from your client account," and "if you've ever rented instances or hosted machines on an account, you cannot cash out until your referral earnings exceed your lifetime instance spend" ([referral docs](https://docs.vast.ai/referral-program)). You can self-fund (earn on the host account, top up the client account from the same bank), but there is **no automatic credit netting**.
- **Salad** pays a "Salad Balance" redeemable for gift cards/PayPal/cash from real AI/render/transcription jobs; crypto mining is only the *fallback* workload ([Salad](https://community.salad.com/sell-gpu-power/), [support](https://support.salad.com/article/356-how-does-my-machine-earn-salad-balance)).
- **Akash Homenode** (early access announced 25 Feb 2026) lets consumer **RTX 4090/5090** owners contribute and earn - the closest thing to a turnkey "rent my gaming rig into the network" path ([PR Newswire](https://www.prnewswire.com/news-releases/akash-launches-early-access-for-homenode-bringing-decentralized-compute-to-everyday-devices-302696087.html), [homenode.akash.network](https://homenode.akash.network/)).

### 4. The rent-inside-the-commons risk (the best-documented finding)

Token reciprocity **financializes** the commons. Of **650+ DePIN projects** (combined market cap >\$16B) by late 2024, **fewer than 20 generated meaningful non-token revenue** ([BlockEden](https://blockeden.xyz/blog/2026/03/21/depin-march-2026-reality-check-650-projects-19b-market-cap-revenue/)). io.net showed the failure mode bluntly: in Q1 2025 it reported **327,000 registered GPUs but only ~6,720 verified active daily (~2% utilization)**, because block rewards are paid to every operator passing uptime checks regardless of real jobs; "when token prices fell, so did provider incentives," and networks lacking organic demand saw utilization collapse ([Messari, State of io.net Q1 2025](https://messari.io/report/state-of-io-net-q1-2025)). Emissions are inflationary by design, so early "yield" is partly other holders' dilution - **rent extracted from the token, not earned from compute**.

The 2026 corrective attempts are real but unproven: **Akash's Burn-Mint Equilibrium** went live **23 March 2026** - every on-chain compute payment triggers a market buy-and-burn of AKT and mints a **stable settlement credit (ACT)** at USD pricing, to re-anchor the token to usage ([AEP-76](https://akash.network/roadmap/aep-76/), [Q1 2026 report](https://akash.network/blog/akash-network-q1-2026-report/)); io.net's parallel fix is its Incentive Dynamic Engine.

### 5. The lesson BOINC encodes: anti-cheat by replication

BOINC's durable contribution to any shared pool is **redundancy as the Sybil/free-rider defense**: each work unit is sent to 2+ independent hosts and credit is granted only to results that reach a **quorum/consensus**; the system assumes every node is unreliable or malicious except the central server, with **adaptive replication** skipping re-runs for proven-reliable hosts to save overhead ([validation](https://boinc.berkeley.edu/trac/wiki/ValidationSimple), [adaptive replication](https://boinc.berkeley.edu/trac/wiki/AdaptiveReplication)). Folding@home layers a *Quick Return Bonus* and team competition on top.

### 6. The free public/philanthropic layer a small collective can actually tap

| Program | What it offers | Easy entry? | Note |
|---|---|---|---|
| **NSF ACCESS** (Explore tier) | HPC/cloud allocations | **Abstract only**; grad students can be PI | US-academic-oriented |
| **NAIRR Pilot** | Cloud credits + HPC + datasets | Application | Microsoft \$20M Azure + NVIDIA \$30M support |
| **CZI** | 1,024×H100 DGX SuperPOD | Competitive RFA | 2025 cycle 9 Jan–18 Jun, 96-GPU min request |
| **Empire AI (NY)** | "Alpha" ~200 NVIDIA GPUs | Consortium-gated | Simons/Flatiron gift, nine universities |
| **Massachusetts AI Hub** | \$31M; AICR at MGHPCC | Partner/nonprofit | **≥40% of compute reserved for startups/nonprofits** |

Sources: [ACCESS](https://allocations.access-ci.org/prepare-requests); [NAIRR \$20M/\$30M](https://www.fiercesensors.com/electronics/nairr-pilot-gets-30m-nvidia-20m-azure); [CZI RFA](https://chanzuckerberg.com/rfa/ai-computing-gpu/); [Empire AI Beta](https://www.empireai.edu/2025/06/27/empire-ai-launches-beta-one-of-the-most-powerful-academic-ai-supercomputers-in-the-nation/); [Massachusetts AI Hub](https://www.mghpcc.org/governor-healey-advances-states-ai-leadership-with-major-investments-in-massachusetts-ai-hub/).

**Caveat for a Paris collective:** most of the above is US-academic-gated. The realistic European equivalents are **EGI/EOSC** and French/EU research-infrastructure routes - the federation that served ~116,000 users in 2024 and passed the 1,000,000-core milestone ([EGI](https://www.egi.eu/article/the-egi-federation-reaches-1000000-cores/)).

### 7. Governance is the real bottleneck (and it is cheap to get right)

Every durable system above maps onto **Elinor Ostrom's 8 design principles** for common-pool resources (*Governing the Commons*, 1990): clear boundaries/membership; rules fit to local conditions; collective-choice; monitoring by accountable members; **graduated sanctions**; cheap conflict resolution; recognized right to self-govern; nested layers ([summary](https://wiki.p2pfoundation.net/Eight_Design_Principles_for_Common_Pool_Resource_Systems)). **Mozilla's 2024 practical framework** translates these to digital/data commons in a form a small group can copy almost verbatim ([Mozilla Foundation, 2024](https://www.mozillafoundation.org/en/blog/a-practical-framework-for-applying-ostroms-principles-to-data-commons-governance/)). The recurring **failure mode is governance, not technology**: unmonitored free-riding, missing graduated sanctions, and Sybil identities.

### 8. Recommended stack for 3–6 artists

1. **Reciprocity layer (no money).** A private AI Horde / Petals-style swarm or a simple shared fair-use ledger among trusted peers. Keep money *out* of this layer to avoid fiscal/legal complications.
2. **Co-located hardware (if any).** Slurm **fairshare** or a shared queue with idle-cycle preemption - the "condo" logic: top priority on hardware you contributed, slack preemptible by all.
3. **Overflow.** Vast.ai / RunPod / Salad to rent out idle rigs on the **supply** side and burst on the demand side.
4. **Free credits in parallel.** EGI/EOSC + French/EU routes (and NSF ACCESS / NAIRR / CZI where eligible).
5. **Charter first.** Write a one-page Ostrom-style charter (membership, contribution rule, graduated sanctions, conflict resolution) *before* buying or pooling anything.

> **Fiscal/legal note - confirm with a professional, not settled French law.** If a shared pool ever moves money (rental income from a co-op rig, paid overflow, token rewards), that may create accounting, VAT, or tax obligations and possibly require a legal vehicle (e.g. an *association*, *SCIC/coopérative*, or *GIE*). Token rewards add the question of how French tax treats crypto received for providing compute. These are **options to verify with an accountant/lawyer**, stated here only to flag that the cleanest reciprocity design keeps money out of the loop entirely.

---

**Killed / demoted for rigor.** EGI's "~1.24M cores" → replaced with the publicly verifiable **1,000,000-core** milestone (users ~116,000 *is* confirmed). BOINC's precise "41.58 PFLOPS / 791,443 machines" → stated as approximate/undated (live dashboards could not be retrieved). Akash's "ACT stablecoin" → softened to **"stable settlement credit"** per the primary source. Folding@home participant counts kept only as a general characterization.

---

*Sources for this section are linked inline above. The consolidated, verified source list and the verification method are in [SOURCES.md](../SOURCES.md).*

---

## Mutualizing compute: concretely lending and sharing GPUs

> **Disclaimer.** Everything below about French tax, social-security and liability law describes *general regimes*, not a ruling on any specific compute-sharing arrangement. Treat every fiscal statement as an **option to confirm with an expert-comptable or avocat fiscaliste** before relying on it. Nothing here is settled law as applied to GPU-sharing.

For a small artist-researcher collective that wants to lend each other GPUs, the engineering is the easy part. The hard part is the *legal category* the sharing falls into, because each category triggers different tax, VAT and liability consequences. The single most important finding: **a one-way free loan is clean; an explicit reciprocal exchange probably is not.**

### What is real (and proven)

The technical pattern works and is published. **GPUnion** (Li et al., *GPUnion: Autonomous GPU Sharing on Campus*, HotNets '25, arXiv 2507.18928) demonstrates campus-scale borrowing of idle GPUs with three mechanisms - container-based task dispatch, a *provider-first* architecture (every node decides when to join/pause/leave), and resilient execution with automatic checkpointing and migration. Reported results: **+30% GPU utilization, +40% interactive sessions, 94% successful workload migration** when a provider pulls out ([arXiv](https://arxiv.org/abs/2507.18928), [ACM DL](https://dl.acm.org/doi/abs/10.1145/3772356.3772403)). This is the closest existing template for a trust-based, revocable, reciprocal collective.

At institutional scale, **GENCI / MesoNET** (EquipEx+ PIA3, launched Oct 2021) federates **22 partners** - GENCI plus 21 regional *mésocentres* - into a mutualized HPC/AI/Quantum infrastructure with a single national allocation portal and a pooled engineering team ([mesonet.fr](https://www.mesonet.fr/2_le-projet.html), [GENCI](https://www.genci.fr/en/learn-about-genci/our-ecosystem)). It shows the governance pattern worth copying: **a trusted network plus central allocation**, rather than ad-hoc peer deals.

### What is hype (or simply wrong)

- **"It's reciprocal, so it's free, so there's no tax."** This is the central trap. *Pure one-way* free lending is fiscally clean. But an explicit *"I lend you my 5090 IF you lend me yours"* reads in French doctrine as **troc / échange**, which is taxable even with **no cash changing hands**: VAT can fall due when each invoice is recorded, each leg valued in the taxable base ([Experts et Décideurs](https://www.experts-et-decideurs.fr/vie-entreprise/gestion-entreprise/troc-entre-entreprises-traitement-comptable-fiscal/), [Créer-Gérer-Entreprendre](https://www.creer-gerer-entreprendre.fr/6-la-gestion-de-lentreprise/6-6-la-gestion-commerciale/echange-marchandises/)). *(Confirm with a fiscaliste for your exact setup.)*
- **"Lending raw compute is liability-free."** False once personal data is involved. Running someone's job on your machine makes you a **sous-traitant under GDPR art. 28**: you may only process on documented instruction, cannot reuse the data, and need a written DPA. Reuse on your own initiative reclassifies you as a *responsable de traitement*. Fines reach **€10M / 2% turnover** for art. 28 breaches ([donneespersonnelles.fr](https://www.donneespersonnelles.fr/article-28-rgpd), [Leto](https://www.leto.legal/articles-rgpd/article-28)).
- **A widely-copied figure is wrong.** The 2025 *franchise des impôts commerciaux* for associations is **€80,011**, not the €81,051 seen in some sources ([LégiFiscal](https://www.legifiscal.fr/actualites-fiscales/4096-franchise-impot-associations-seuil-porte-80011.html), confirmed against [BOFiP](https://bofip.impots.gouv.fr/bofip/2659-PGP.html/identifiant=BOI-IS-CHAMP-10-50-20-20-20250416)).

### The clean default: prêt à usage (commodat)

The lowest-friction path is the **prêt à usage** (commodat), *Code civil* art. 1875 ff. Art. 1876 is unambiguous: *« Ce prêt est essentiellement gratuit. »* ([Doctrine / Légifrance](https://www.doctrine.fr/l/texts/codes/LEGITEXT000006070721/articles/LEGIARTI000006444687)). The borrower must conserve the thing (art. 1880) and is liable for misuse (art. 1881) but not for normal wear (art. 1884).

| Element | Effect on the commodat |
|---|---|
| Free, one-way use | ✅ Stays a commodat |
| Borrower pays electricity / upkeep of use (art. 1886) | ✅ Does **not** disqualify it (cost of use, not remuneration) |
| Any real economic counterpart flowing to the lender | ❌ Risks **automatic requalification as a bail/location** → taxable rental income |
| Explicit mutual exchange of machines | ❌ Risks treatment as **troc/échange** → potentially taxable, VAT |

Sources: [Captain Legal](https://www.captain.legal/fr/demarches-quotidiennes/commodat-pret-a-usage/), [Fiscaloo](https://www.fiscaloo.fr/14633-commodat-ou-pret-a-usage/). The practical toolkit French associations and communes already use: a written **convention de mise à disposition de matériel** (duration, conservation, return, who bears damage/loss) + a **charte informatique** (acceptable use). Drafted as a pure prêt à usage, these allocate liability *without* creating a taxable consideration.

### Three vehicles to formalize sharing

| Vehicle | Min. setup | Tax position | Liability | Key constraint | Best for |
|---|---|---|---|---|---|
| **Association loi 1901** | Free, declaratory | Non-profit; commercial-tax *franchise* up to **€80,011 (2025)** for accessory lucrative activity if *gestion désintéressée* + règle des 4P + non-lucrative predominance | Members generally shielded | **Cannot distribute benefits** to members; profit-sharing risks requalification into *société créée de fait* (no legal personality, members personally & indefinitely liable) | Pooling/lending shared kit among members, no profit motive |
| **GIE** (Groupement d'Intérêt Économique) | **2 members min, no capital** | **Fiscally transparent** - not taxed as such; each member taxed on its share | Members **responsables solidairement et indéfiniment sur leurs biens personnels** | Activity must be the *prolongement* (auxiliary extension) of members' activities, never a substitute | Members who already have an economic activity and want to pool *means* (e.g. a shared GPU rig) |
| **SCIC** (Société Coopérative d'Intérêt Collectif) | SARL/SAS min 3 associés, SA min 7; multi-stakeholder | ≥**57.5%** of result locked in *réserves impartageables* (15% légale + 50% of remainder; raisable to 100%); locked reserves deductible from IS | Limited (company form) | Heavier governance: **1 person = 1 vote**, multiple associate categories | A durable, multi-stakeholder shared-compute commons |

Sources: association - [Assistant-juridique](https://www.assistant-juridique.fr/but_non_lucratif_association.jsp), [associations.gouv.fr](https://associations.gouv.fr/lexception-lassujettissement-aux-impots-commerciaux), threshold [LégiFiscal](https://www.legifiscal.fr/actualites-fiscales/4096-franchise-impot-associations-seuil-porte-80011.html); GIE - [Bpifrance Création](https://bpifrance-creation.fr/encyclopedie/structures-juridiques/se-regrouper-solutions-juridiques/gie-groupement-dinteret); SCIC - [L-Expert-Comptable](https://www.l-expert-comptable.com/a/6074-societe-cooperative-d-interet-collectif-scic-definition-avantages.html), [Les Scic FAQ](https://www.les-scic.coop/foire-aux-questions).

The SCIC is not theoretical: **1,421 SCICs existed in France by end-2025** (+10.4% since 2022), with 17,547 jobs and €1.7bn revenue ([Coop FR](https://www.entreprises.coop/les-societes-cooperatives-d-interet-collectif-scic), [Les Scic - chiffres clés](https://www.les-scic.coop/chiffres-cles)).

### Practical decision path

1. **Default to one-way, free prêt à usage** for occasional, no-money lending - cheapest and cleanest. Paper it with a *convention de mise à disposition* + *charte informatique*.
2. **Avoid framing it as an explicit swap.** If reciprocity is the point, route it through a shared structure (GIE or association) rather than bilateral I-lend-you-you-lend-me deals, to avoid *troc* treatment - and **get a fiscaliste's sign-off**.
3. **Add a GDPR layer** whenever a job may touch personal data: documented-instruction clause + written DPA (art. 28), or restrict shared compute to non-personal-data workloads.
4. **For anything durable or multi-party**, weigh GIE (transparent, but joint+several liability) vs SCIC (limited liability, locked reserves, heavier governance).

*Credits: GPUnion - Li et al., HotNets '25 (2025); MesoNET/GENCI - EquipEx+ PIA3 (2021–). Legal articles cited to Code civil (art. 1875–1886) and RGPD art. 28.*

---

*Sources for this section are linked inline above. The consolidated, verified source list and the verification method are in [SOURCES.md](../SOURCES.md).*
