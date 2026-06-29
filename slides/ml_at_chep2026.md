---
layout: chapter-title
class: "text-left"
---

# ML & AI at CHEP 2026

**CHEP 2026** — Computing in High Energy Physics  
Chulalongkorn University, Bangkok — May 25–29, 2026

<br>

> **~40 ML/AI talks** out of 594 contributions  
> **First ever** dedicated AI/ML plenary day (May 27)  
> ML now present in **every single track**

---

# May 27: A Full Day on AI

<div class="grid grid-cols-2 gap-8 mt-6">
<div>

**Gordon Watts** (U. Washington)  
[*LLM Ecosystem for Physics Analysis*](https://indico.cern.ch/event/1471803/)

**Ke Li**  
[*Towards AI Scientists: Human-AI Collaboration*](https://indico.cern.ch/event/1471803/)

**Savannah Thais** (Hunter College)  
[*Good AI for Physics Needs AI Ethics*](https://indico.cern.ch/event/1471803/)

**Jose Luna Duran** (CERN)  
[*AI and Cybersecurity: Power, Risk, Responsibility*](https://indico.cern.ch/event/1471803/)

</div>
<div class="flex flex-col justify-center">

<br>

> The community is asking: is AI a **tool**, a **collaborator**, or a **scientist**?

<br>

**Panel** on *Opportunities and Responsibilities*  
with 7 participants from CMS, ATLAS, CERN, academia

<br>

First time CHEP dedicated a morning plenary to **AI ethics and LLMs**

</div>
</div>

---
zoom: 0.95
---

# Generative Models for Fast Simulation

<div class="grid grid-cols-2 gap-8 mt-4">
<div>

**Calorimeter shower simulation** is the main target:
replace GEANT4 (minutes/event) with ML (milliseconds)

<br>

| Method | Experiments |
|---|---|
| [Flow Matching](https://indico.cern.ch/event/1471803/contributions/6968024/) | ATLAS muon punch-through |
| [Diffusion / DiT](https://indico.cern.ch/event/1471803/contributions/6968020/) | CMS HGCAL, CEPC ECAL |
| [GAN + Diffusion](https://indico.cern.ch/event/1471803/contributions/6968009/) | ATLAS calorimeter |
| [GAN](https://indico.cern.ch/event/1471803/contributions/6967959/) | MPD TPC *(LAMBDA poster)* |
| [End-to-end GenAI](https://indico.cern.ch/event/1471803/contributions/6967992/) | ATLAS full detector |

</div>
<div class="flex flex-col justify-center">

<br>

**Trend:** GANs → Flow Matching → Diffusion Transformers

<br>

**New idea** at this CHEP:  
[cross-experiment pretrained networks](https://indico.cern.ch/event/1471803/contributions/6966878/) — train once, fine-tune per detector  
*(Matthias Schott, CERN/Mainz)*

<br>

> 8 talks on generative simulation — the largest ML topic at the conference

</div>
</div>

---
zoom: 0.95
---

# GNNs & Transformers for Reconstruction

<div class="grid grid-cols-2 gap-8 mt-4">
<div>

**Graph Neural Networks** have become the default architecture for calorimeter reconstruction

- [GNN end-to-end reco in CMS HGCAL](https://indico.cern.ch/event/1471803/contributions/6967243/)
- [GNNs for overlapping shower segmentation](https://indico.cern.ch/event/1471803/contributions/6967209/)
- [TICL iterative clustering — CMS Phase-2](https://indico.cern.ch/event/1471803/contributions/6967245/)

<br>

**Transformers** are entering tracking:

- [GUNTAM — transformer for seed reconstruction](https://indico.cern.ch/event/1471803/contributions/6967179/)
- [DNN point-cloud tracking](https://indico.cern.ch/event/1471803/contributions/6967178/)
- [dN/dx particle ID with graph transformers](https://indico.cern.ch/event/1471803/contributions/6967239/)

</div>
<div class="flex flex-col justify-center">

<br>

GNNs are now **infrastructure**, not research:  
[Module Map Graph library](https://indico.cern.ch/event/1471803/contributions/6966823/) ships shared GNN pipelines for HL-LHC experiments

<br>

> Transformers are to tracking what CNNs were to imaging 5 years ago — they're just arriving

</div>
</div>

---

# Real-Time ML: From µs Triggers to Anomaly Detection

<div class="grid grid-cols-2 gap-8 mt-4">
<div>

**Sub-microsecond FPGA inference** is mature:

- [Unified sub-µs workflow on FPGAs](https://indico.cern.ch/event/1471803/contributions/6967268/)
- [Versal AI Engines for L1 trigger](https://indico.cern.ch/event/1471803/contributions/6967027/)
- [ML hyperparameter optimization for triggers](https://indico.cern.ch/event/1471803/contributions/6967319/)

<br>

**Autoencoder-based anomaly triggers** (model-independent):

- [Autoencoders for LHCb event selection](https://indico.cern.ch/event/1471803/contributions/6967316/)

</div>
<div class="flex flex-col justify-center">

<br>

**HL-LHC goal:** run full offline-quality reconstruction at Level-1  
→ [Next-gen CMS triggers](https://indico.cern.ch/event/1471803/contributions/6967011/)

<br>

Dedicated **ML trigger talks** also for:
[muon systems](https://indico.cern.ch/event/1471803/contributions/6967271/),
[long-lived particles](https://indico.cern.ch/event/1471803/contributions/6967170/)

<br>

> hls4ml / FPGA path is now standard — the frontier is richer architectures at the same latency

</div>
</div>

---

# Emerging: Foundation Models, LLMs, Quantum ML

<br>
<br>

<div class="grid grid-cols-3 gap-6 mt-6">
<div>

### Foundation Models

[**EveNet**](https://indico.cern.ch/event/1471803/contributions/6968270/) — pretrained on billions of simulated collisions, fine-tuned per task

*"Physics BERT"*: one model for classification, regression, tagging

</div>
<div>

### LLMs in Analysis

Gordon Watts: LLMs as **analysis pipeline agents**, not just code assistants

[Metadex](https://indico.cern.ch/event/1471803/contributions/6967391/): natural language queries over DUNE conditions database

</div>
<div>

### Quantum ML

[Zoë Holmes (EPFL)](https://indico.cern.ch/event/1471803/contributions/6976844/) — plenary on QC roadmap for HEP

[QML scalability](https://indico.cern.ch/event/1471803/contributions/6967176/) + [Riemannian gradient QML](https://indico.cern.ch/event/1471803/contributions/6975477/) from Chulalongkorn U. (host)

> Still pre-advantage — but serious research

</div>
</div>

---

# Takeaways

<div class="grid grid-cols-2 gap-8 mt-6">
<div>

### What's mature

- **Diffusion/flow models** for fast simulation — GAN era ending
- **GNNs** for calorimeter reconstruction — now infrastructure
- **FPGA ML** for µs-latency triggers — hls4ml is standard

</div>
<div>

### What's emerging

- **Foundation models** for HEP — train once, use everywhere
- **LLMs** as analysis tools — first serious CHEP discussion
- **Cross-experiment transfer learning** for simulation
- **Quantum ML** — active research, no advantage yet

</div>
</div>

<div class="mt-8 text-center">

Full contribution list → [indico.cern.ch/event/1471803/contributions/](https://indico.cern.ch/event/1471803/contributions/)

</div>
