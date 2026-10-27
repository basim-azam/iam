<div align="center">

# Introspective Attention Modulation for Safe Text-to-Image Generation

<a href="https://findanexpert.unimelb.edu.au/profile/1065421-basim-azam">Basim Azam</a><sup>1</sup> ·
<a href="https://www.lancaster.ac.uk/scc/about-us/people/hossein-rahmani">Hossein Rahmani</a><sup>2</sup> ·
<a href="https://findanexpert.unimelb.edu.au/profile/1050019-naveed-akhtar">Naveed Akhtar</a><sup>1</sup>

<sup>1</sup>The University of Melbourne &nbsp;·&nbsp; <sup>2</sup>Lancaster University

[![arXiv](https://img.shields.io/badge/arXiv-2607.14945-b31b1b?logo=arxiv&logoColor=white)](https://arxiv.org/abs/2607.14945)
[![Project Page](https://img.shields.io/badge/Project-Page-1f6feb?logo=githubpages&logoColor=white)](https://basim-azam.github.io/iam/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
<img src="assets/teaser.png" width="92%"/>

</div>

> ⚠️ **Content warning.** This research studies unsafe (sexual, violent, disturbing) content produced by text-to-image models. Any unsafe examples shown in our materials are concealed.

---

## 📰 News

- **Preprint is on [arXiv](https://arxiv.org/abs/2607.14945)** and the [project page](https://basim-azam.github.io/iam) is live.
- **Code & models are coming soon** — see the release checklist below.

## 🗓️ Release

- [x] Project page
- [x] Paper / arXiv
- [ ] Inference code
- [ ] Learned safety direction (`w_unsafe`)
- [ ] Evaluation & training code

## ✨ Overview

**IAM** is a **training-free, inference-time** safety control for flow-based diffusion transformers (FLUX). Rather than editing model weights — which adapters such as LoRA can simply undo — IAM lets the model **introspect its own attention** during denoising and **steers it away from unsafe concepts**, preserving semantic alignment and image quality with **no retraining** of the base model. An introspection-ratio handle (Light / Moderate / Strong) provides a continuous safety–quality trade-off.

## 📊 Results

> ⚠️ Unsafe regions are concealed in all figures.

<div align="center">
<img src="assets/qual_methods.png" width="92%"/>
<br><em>IAM vs. concept-erasure and editing methods (UCE, ESD, EraseAnything, FlowEdit, MCE):
where weight-editing approaches leave unsafe content intact, IAM yields a clean, semantically
aligned image.</em>
<br><br>
<img src="assets/qual_attacks.png" width="92%"/>
<br><em>Robustness under adversarial attacks (MMA-Diffusion, UnlearnDiffAtk) across nudity,
shocking, illegal-activity, violence and self-harm categories.</em>
<br><br>
<img src="assets/qual_flux.png" width="92%"/>
<br><em>IAM generalizes across FLUX variants (Dev, Kontext, Schnell, Krea) with no per-model tuning.</em>
</div>

## 🛠️ Setup &amp; Usage

> ⏳ Releasing with the code. The intended interface:

```python
from iam import load_pipeline, generate, PRESETS

pipe, procs = load_pipeline()                                  # FLUX.1-dev (+ optional adapter)
img = generate(pipe, procs, "a portrait in a garden", PRESETS["strong"], seed=42)
img.save("iam_output.png")
```

## 📌 Citation

```bibtex
@article{azam2026iam,
  title   = {Introspective Attention Modulation for Safe Text-to-Image Generation},
  author  = {Azam, Basim and Rahmani, Hossein and Akhtar, Naveed},
  journal = {arXiv preprint arXiv:2607.14945},
  year    = {2026}
}
```

## 🙏 Acknowledgements

Naveed Akhtar is a recipient of the Australian Research Council Discovery Early Career Researcher Award (project #DE230101058) funded by the Australian Government. This research was supported by The University of Melbourne's Research Computing Services and the Petascale Campus Initiative.
