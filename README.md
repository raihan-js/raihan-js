# Hey there, I'm Raihan 👋

<div align="center">

**AI/ML Engineer · CTO at [ClarioScope AI](https://clarioscope.ai/) · From Bangladesh**

*Train small language models (SLMs) from scratch · Fine-tune larger ones with QLoRA · Ship production AI products*

[![Portfolio](https://img.shields.io/badge/Portfolio-FF5722?style=for-the-badge&logo=google-chrome&logoColor=white)](https://raihan-js.github.io)
[![Hugging Face](https://img.shields.io/badge/🤗_Hugging_Face-FFD21E?style=for-the-badge)](https://huggingface.co/raihan-js)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/raihan-js/)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:raihan@clarioscope.ai)

</div>

---

## What I'm Working On

- 🧠 **Training small language models from scratch** &mdash; the [ORCH series](https://huggingface.co/raihan-js) (350M&ndash;3B) for Next.js code generation, and [MedLLM-10M](https://huggingface.co/raihan-js/medllm-10m) for medical applications
- 🔧 **Fine-tuning larger base models** with QLoRA &mdash; [ORCH-7B](https://huggingface.co/raihan-js/orch-7b) is a 4-bit fine-tune of DeepSeek Coder 6.7B
- 🎯 **Building benchmark-grade specialist SLMs** &mdash; [clarioscope-intent-deberta-v1](https://huggingface.co/raihan-js/clarioscope-intent-deberta-v1) matches frontier LLMs within 4 pp of accuracy at **22× lower latency** and $0/inference ([dev.to writeup](https://dev.to/ryandevv/matching-frontier-llms-at-22x-lower-latency-a-184m-parameter-intent-classifier-for-healthcare-text-5ec2))
- 🏥 **Leading engineering at [ClarioScope AI](https://clarioscope.ai/)** &mdash; HIPAA-compliant healthcare practice growth platform
- 🚀 **Shipping production AI products** &mdash; [BeautyCrew AI](https://beautycrew.ai), [VETR Proposal](https://vetrproposal.com), [CommonRoom AI](https://commonroomai.com)
- 📚 **Open-source everything** &mdash; all model weights, configs, and tokenizers are public on Hugging Face

---

## 🏆 Latest ship: the full ClarioScope SLM Suite (all three models shipped)

A three-model intake intelligence pipeline for healthcare practices. Each model is small, specialized, and benchmarked head-to-head against frontier APIs. Suite-level writeup: [Three small models for healthcare intake — and what shipping all three taught me](https://dev.to/raihan-js/three-small-models-for-healthcare-intake-and-what-shipping-all-three-taught-me-71l).

| Model | Task | Size | Headline result | Speed vs frontier | Cost / 1K | Links |
|---|---|---|---|---|---|---|
| **clarioscope-intent-deberta-v1** | 7-class intent classification | 184M | 91.16% accuracy (within 4 pp of Claude Haiku) | **22× faster** | $0 | [🤗](https://huggingface.co/raihan-js/clarioscope-intent-deberta-v1) · [📝](https://dev.to/ryandevv/matching-frontier-llms-at-22x-lower-latency-a-184m-parameter-intent-classifier-for-healthcare-text-5ec2) |
| **clarioscope-phi-deberta-v1** | 18-category HIPAA PHI span detection | 125M | Macro F1 0.63 (triples frontier on `LOC`, ties on `NAME`/`DATE`/`PHONE`/`IP`/`AGE`) | **45× faster** | $0 | [🤗](https://huggingface.co/raihan-js/clarioscope-phi-deberta-v1) · [📝](https://dev.to/raihan-js/where-small-models-beat-frontier-llms-and-where-they-dont-a-125m-phi-detector-4edb) |
| **clarioscope-insurance-v1** | 12-field insurance / billing extraction | 125M | Macro F1 0.79 (ties GPT-4o on `SUBSCRIBER_NAME`, within 5–13 pp on the four highest-volume fields) | **26× faster** | $0 | [🤗](https://huggingface.co/raihan-js/clarioscope-insurance-v1) · [📝](https://dev.to/raihan-js/three-small-models-for-healthcare-intake-and-what-shipping-all-three-taught-me-71l) |

**Total cost to build all three:** ~$16 in OpenAI + RunPod + benchmark API spend. **Total infrastructure:** Hugging Face (free) + RunPod spot pods (a few cents per run).

The recurring pattern across all three: small specialized models don't replace frontier APIs — they're stage one of a hybrid pipeline that does the bulk-volume work cheaply, then defers a small fraction of hard cases to a frontier API. All three model cards include honest per-entity / per-class breakdowns showing where the small model wins and loses.

![Per-entity F1 — PHI detector vs frontier APIs](https://huggingface.co/raihan-js/clarioscope-phi-deberta-v1/resolve/main/per_entity_f1.png)

---

## AI Models I've Trained

All published openly on [🤗 Hugging Face](https://huggingface.co/raihan-js). Configs and tokenizers included.

<table>
<tr>
<td width="50%" valign="top">

### 🎼 ORCH Next.js 3B

A **3 billion parameter** decoder-only transformer trained **from scratch** for full-stack Next.js code generation.

| Spec | Value |
|------|-------|
| Parameters | ~3.0B |
| Architecture | Custom LLaMA-style |
| Layers / Hidden | 32 / 2,560 |
| Attention / KV (GQA) | 32 / 8 |
| Vocab | 32,000 (custom) |
| Context | 16,384 tokens |
| Hardware | NVIDIA A40 48GB (RunPod) |

[![Model](https://img.shields.io/badge/🤗_Model-Card-yellow?style=flat-square)](https://huggingface.co/raihan-js/orch-nextjs-3b)

</td>
<td width="50%" valign="top">

### 🔧 ORCH-7B

**QLoRA fine-tune** of DeepSeek Coder 6.7B Instruct, specialized for autonomous Next.js generation.

| Spec | Value |
|------|-------|
| Base model | DeepSeek Coder 6.7B Instruct |
| Method | QLoRA (4-bit NF4 + LoRA) |
| Training | 43h on a single A100 |
| Steps | 5,238 |
| Context | 16,384 (linear RoPE 4×) |

[![Model](https://img.shields.io/badge/🤗_Model-Card-yellow?style=flat-square)](https://huggingface.co/raihan-js/orch-7b)
[![Studio](https://img.shields.io/badge/🎨_ORCH-Studio-D4A574?style=flat-square)](https://huggingface.co/spaces/raihan-js/orch-studio)

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🚀 ORCH Fusion (272M)

Compact code-gen model trained **from scratch** on consumer hardware (RTX 3060 12GB).

| Spec | Value |
|------|-------|
| Parameters | 272.7M |
| Architecture | Custom LLaMA-style |
| Layers / Hidden | 24 / 1,024 |
| GQA | 16 heads / 4 KV |
| Vocab | 2,103 (tiny custom) |

**Benchmark (ORCH-ProjectBench):** 76.6 overall · 95.3 code parse · 93.3 format

[![Model](https://img.shields.io/badge/🤗_Model-Card-yellow?style=flat-square)](https://huggingface.co/raihan-js/orch-fusion)

</td>
<td width="50%" valign="top">

### 🩺 MedLLM-10M

GPT-2 style language model trained **from scratch** on medical literature.

| Spec | Value |
|------|-------|
| Parameters | ~27.7M (10M body) |
| Architecture | GPT-2 |
| Layers / Hidden | 8 / 512 |
| Heads / FFN | 8 / 2,048 |
| Vocab | 5,000 (custom) |
| Context | 512 |
| Hardware | RTX 3060 12GB |

> ⚠️ Research / educational use only. Not for clinical decision-making.

[![Model](https://img.shields.io/badge/🤗_Model-Card-yellow?style=flat-square)](https://huggingface.co/raihan-js/medllm-10m)

</td>
</tr>
</table>

Also published: [ORCH Next.js 350M v2](https://huggingface.co/raihan-js/orch-nextjs-350m-v2) (287M, from scratch with 16k vocab).

---

## Tech Stack

<div align="center">

### AI & ML
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![Hugging Face](https://img.shields.io/badge/🤗_Hugging_Face-FFD21E?style=for-the-badge)
![Transformers](https://img.shields.io/badge/Transformers-FF6F00?style=for-the-badge)
![QLoRA](https://img.shields.io/badge/PEFT_/_QLoRA-412991?style=for-the-badge)
![CUDA](https://img.shields.io/badge/CUDA-76B900?style=for-the-badge&logo=nvidia&logoColor=white)
![Gradio](https://img.shields.io/badge/Gradio-F97316?style=for-the-badge)

### Frontend
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)

### Backend
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Laravel](https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)

### Cloud & DevOps
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![RunPod](https://img.shields.io/badge/RunPod-673AB7?style=for-the-badge)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

</div>

---

## Selected Live Products

| Product | What it does |
|---|---|
| [ClarioScope AI](https://clarioscope.ai/) | HIPAA-compliant healthcare practice growth platform (CTO) |
| [BeautyCrew AI](https://beautycrew.ai) | Booking management for the beauty industry — prevents missed appointments |
| [VETR Proposal](https://vetrproposal.com) | AI-assisted federal contracting co-pilot for small business teams |
| [CommonRoom AI](https://commonroomai.com) | Collaborative digital workspace — 15 group-coordination tools, no install |
| [ORCH Studio](https://huggingface.co/spaces/raihan-js/orch-studio) | Generate complete Next.js apps from natural language (powered by ORCH-7B) |

---

## Open Source

- **[orch-ai](https://huggingface.co/orch-ai)** — Hugging Face org for the ORCH code-generation model family
- **[clarioscope-ai](https://huggingface.co/clarioscope-ai)** — ClarioScope AI's Hugging Face org
- Configs, tokenizers, and training details are public on every model card

---

<div align="center">

📫 **Get in touch:** [raihan@clarioscope.ai](mailto:raihan@clarioscope.ai) · [Portfolio](https://raihan-js.github.io)

</div>
