# Hey there, I'm Raihan 👋

<div align="center">

**AI/ML Engineer · LLMOps · Evaluation · Retrieval · From Bangladesh, open to relocating to Japan**

*I build the measurement layer for LLM systems: release gates for quantised models, label-free monitoring, judge audits and grounding checks, each reported with per-item data and paired statistics.*

[![Portfolio](https://img.shields.io/badge/Portfolio-FF5722?style=for-the-badge&logo=google-chrome&logoColor=white)](https://raihan-js.github.io)
[![Hugging Face](https://img.shields.io/badge/🤗_Hugging_Face-FFD21E?style=for-the-badge)](https://huggingface.co/raihan-js)
[![dev.to](https://img.shields.io/badge/dev.to-0A0A0A?style=for-the-badge&logo=devdotto&logoColor=white)](https://dev.to/raihan-js)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/raihan-js/)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:raihan@vetrproposal.com)

</div>

---

## What I'm working on

- 🧪 **Twelve open research projects** (below), each with code, tests and data on GitHub and Hugging Face. Nulls and negative results are reported as nulls, and every number carries its scope.
- 🏛️ **Founding engineer and AI/ML lead at [VETR Proposal](https://vetrproposal.com)** (contract): an AI proposal platform for federal contractors. I trained FedProc-180M, F1 0.800 vs 0.804 for Claude Haiku 4.5 on FAR-clause extraction (FedProc-Bench test set), with 13.8% vs 32.1% hallucinated clauses.
- 🇯🇵 **Japanese-language evaluation and retrieval**: JaCite-Bench, tiny-bilingual-retriever and Invoice-Check JP below. I'm studying Japanese (JLPT N5 targeted for December 2026).
- 🧱 **Small models from scratch on one GPU**: the ORCH code models and the Vocab Tax study.

---

## Research projects

Every result below cites its dataset, sample size and hardware in the project's README. Most are measured on synthetic or small data and say so there.

| Project | What it does | Key result (scope in the README) | Links |
|---|---|---|---|
| **[FlipGate](https://github.com/raihan-js/flipgate)** | Release gate for quantised LLMs: counts per-item right→wrong flips against a measured noise floor | Qwen2.5-3B, GSM8K-1000: AWQ and GPTQ each broke 91 correct answers (p = 0.0050 and 0.0028) while accuracy moved 3.5 to 3.7 points; the gate fails both | [GH](https://github.com/raihan-js/flipgate) · [HF](https://huggingface.co/datasets/raihan-js/flipgate-results) · [📝](https://dev.to/raihan-js/awq-looked-10-points-better-on-gsm8k-until-i-stopped-truncating-the-answers-18a7) |
| **[ShiftWatch](https://github.com/raihan-js/shiftwatch)** | Label-free accuracy estimation under data shift, with a FastAPI + Prometheus sidecar | No estimator wins everywhere (Banking77, CLINC150, ModernBERT-base); DoC and CBPE never detect a drop | [GH](https://github.com/raihan-js/shiftwatch) · [HF](https://huggingface.co/datasets/raihan-js/shiftwatch-ladder) · [📝](https://dev.to/raihan-js/how-accurate-is-your-model-right-now-estimating-accuracy-without-labels-59kp) |
| **[OracleBench](https://github.com/raihan-js/oraclebench)** | Audits small LLM judges against deterministic oracles | A 3B judge falsely accepts 11.0% of wrong answers, a 0.5B one 40.6% (1,760 items); checker-first harness: 0 errors by construction vs 412 for judge-only, 17.6× fewer judge calls | [GH](https://github.com/raihan-js/oraclebench) · [HF](https://huggingface.co/datasets/raihan-js/oraclebench-items) |
| **[JaCite-Bench](https://github.com/raihan-js/jacite-bench)** | Do LLMs invent Japanese law articles? Registry of 11 laws, 6,913 articles, 600 questions | llm-jp-3-1.8b invents 4.05% of Japanese-language citations vs 1.09% in English (3.7×) | [GH](https://github.com/raihan-js/jacite-bench) · [HF](https://huggingface.co/datasets/raihan-js/jacite-bench) |
| **[GraphProof-QA](https://github.com/raihan-js/graphproof-qa)** | Proof-carrying multi-hop QA with a 1.5B model | 34.2% direct vs 93.3% DSL vs 96.8% constrained on 6,000 MetaQA questions; entities renamed to unseen strings: 81.4% vs 5.8% | [GH](https://github.com/raihan-js/graphproof-qa) · [HF](https://huggingface.co/raihan-js/graphproof-dsl-1.5b) |
| **[FedProc-Constrained](https://github.com/raihan-js/fedproc-constrained)** | A registry grammar for FAR clause numbers | Fabricated clauses 57/60 free vs 0/60 with the grammar (Qwen2.5-1.5B); with an abstain option the model also refused real clauses | [GH](https://github.com/raihan-js/fedproc-constrained) · [HF](https://huggingface.co/datasets/raihan-js/fedproc-constrained-results) |
| **[tiny-bilingual-retriever](https://github.com/raihan-js/tiny-bilingual-retriever)** | bge-m3 (568M) distilled into a 36.7M English-Japanese encoder | 71% of the teacher's EN-JA nDCG@10 (synthetic eval) with 15× fewer parameters and a 4× smaller index; the public ruri-v3-30m scores higher | [GH](https://github.com/raihan-js/tiny-bilingual-retriever) · [HF](https://huggingface.co/raihan-js/tiny-rerank-ja-en-30m) |
| **[Roofline-First Decoding](https://github.com/raihan-js/roofline-decoding)** | Fused W4A16 Triton GEMV for batch-1 decoding, written after computing the bandwidth ceiling | RTX 3060: 25.5 tok/s vs 25.7 for bitsandbytes NF4, with lower probe perplexity; measured copy bandwidth 323.9 GB/s | [GH](https://github.com/raihan-js/roofline-decoding) · [HF](https://huggingface.co/datasets/raihan-js/roofline-decoding-results) |
| **[Vocab Tax](https://github.com/raihan-js/vocab-tax)** | Compute-matched vocabulary study, 16 decoders trained from scratch on TypeScript/JavaScript | 8k to 16k vocabularies win at every size; an 8.0M model with an 8k vocabulary beats a 33.5M one with 2k (1.168 vs 1.436 bits/byte); seed noise up to 0.13 | [GH](https://github.com/raihan-js/vocab-tax) · [HF](https://huggingface.co/datasets/raihan-js/vocab-tax-grid) |
| **[DemoDoctor](https://github.com/raihan-js/demodoctor)** | What do bad robot demonstrations cost a policy? | A stall detector reaches F1 0.867 on injected faults; 12 ACT policies on PushT show no detectable effect of corrupted data (grid underpowered) | [GH](https://github.com/raihan-js/demodoctor) |
| **[Invoice-Check JP](https://github.com/raihan-js/invoice-check-jp)** | A fine-tuned VLM reads Japanese qualified invoices (適格請求書); check digit, registry lookup and tax arithmetic gate auto-approval | QLoRA Qwen2.5-VL-3B on synthetic invoices: 83.0% exact; the checks auto-approve 86.8% with 0 of 461 wrong in a checkable field. Adapter is non-commercial | [GH](https://github.com/raihan-js/invoice-check-jp) · [HF dataset](https://huggingface.co/datasets/raihan-js/invoice-check-jp) · [HF adapter](https://huggingface.co/raihan-js/invoice-check-jp-qwen2.5-vl-3b-lora) |
| **[Keiri-Agent](https://github.com/raihan-js/keiri-agent)** | A LangGraph back-office agent for Japanese invoices: verification, PO matching, human review, PostgreSQL checkpoints, LangSmith evaluation, exact CI gate | Pre-registered on 300 synthetic invoices: the checks cut unsafe auto-approvals from 17.0% to 4.0%; PO matching mostly rerouted rather than detected. Survives SIGKILL | [GH](https://github.com/raihan-js/keiri-agent) |

More write-ups, charts and the full list: **[raihan-js.github.io](https://raihan-js.github.io)**.

---

## Models I've trained

All published on [🤗 Hugging Face](https://huggingface.co/raihan-js), with configs and tokenizers. Built and published, not deployed.

| Model | What it is | Hardware |
|---|---|---|
| [ORCH Next.js 3B](https://huggingface.co/raihan-js/orch-nextjs-3b) | 3B decoder-only LLaMA-style model trained from scratch for Next.js code generation (data-limited) | one rented A40 48GB |
| [ORCH-7B](https://huggingface.co/orch-ai/ORCH-7B) | QLoRA fine-tune of DeepSeek Coder 6.7B Instruct (5,238 steps) | one A100, 43 h |
| [ORCH Fusion](https://huggingface.co/raihan-js/orch-fusion) | 272M model trained from scratch, with a custom 2,103-token vocabulary | one RTX 3060 12GB |
| [ORCH Next.js 350M v2](https://huggingface.co/raihan-js/orch-nextjs-350m-v2) | 287M model trained from scratch with a 16k vocabulary | one RTX 3060 12GB |
| [FedProc-180M](https://huggingface.co/raihan-js/fedproc-180m-v0) | ModernBERT-base, 4 task heads, FAR-clause extraction | see the model card |

**Earlier work, past role.** At ClarioScope AI (CTO and lead AI engineer, 2024 to 2026; the company was sunset in 2026 after two pivots and the models were open-sourced) I built and published the ClarioScope SLM suite: a [184M intent classifier](https://huggingface.co/raihan-js/clarioscope-intent-deberta-v1) (91.2% vs 95.2% for GPT-4o on a held-out set, about 22× faster than Claude Haiku 4.5), a [125M PHI detector](https://huggingface.co/raihan-js/clarioscope-phi-deberta-v1) (18 HIPAA Safe Harbor categories) and a [125M insurance extractor](https://huggingface.co/raihan-js/clarioscope-insurance-v1) (12 fields). Write-ups: [the suite](https://dev.to/raihan-js/three-small-models-for-healthcare-intake-and-what-shipping-all-three-taught-me-71l) and [the PHI detector](https://dev.to/raihan-js/where-small-models-beat-frontier-llms-and-where-they-dont-a-125m-phi-detector-4edb).

---

## Tech stack

<div align="center">

### AI & ML
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![Hugging Face](https://img.shields.io/badge/🤗_Hugging_Face-FFD21E?style=for-the-badge)
![PEFT / QLoRA](https://img.shields.io/badge/PEFT_/_QLoRA-412991?style=for-the-badge)
![Triton](https://img.shields.io/badge/Triton-76B900?style=for-the-badge&logo=nvidia&logoColor=white)
![vLLM](https://img.shields.io/badge/vLLM-30A2FF?style=for-the-badge)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=for-the-badge)
![LangSmith](https://img.shields.io/badge/LangSmith-1C3C3C?style=for-the-badge)

### Backend & platform
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Laravel](https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-43853D?style=for-the-badge&logo=node.js&logoColor=white)

### Frontend
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)

</div>

---

## Open source

- **[orch-ai](https://huggingface.co/orch-ai)**: Hugging Face org for the ORCH code-generation model family
- **[clarioscope-ai](https://huggingface.co/clarioscope-ai)**: Hugging Face org for the ClarioScope models
- Also engineer and maintainer of CommonRoom AI (a 15-mini-app collaboration app) and founder of ILMA Lang (a beginner programming language that transpiles to C)

---

<div align="center">

📫 **Get in touch:** [raihan@vetrproposal.com](mailto:raihan@vetrproposal.com) · [Portfolio](https://raihan-js.github.io) · [LinkedIn](https://www.linkedin.com/in/raihan-js/)

</div>
