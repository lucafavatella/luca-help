## Privacy-focused online chatbots

* https://lumo.proton.me
* Also:
  * https://duck.ai
    * Especially models hosted on Tinfoil (see https://duckduckgo.com/duckduckgo-help-pages/duckai/ai-chat-privacy)
  * ? https://search.brave.com/ask

## Remote privacy-focused API providers

* https://lumo.proton.me (to be released end 2026)
* https://tinfoil.sh/pricing#api

## Open source (weights, training data, code) machine learning models

### LLMs

* OLMo 2 / 3 (https://allenai.org). Apache 2.0.
* Apertus (via https://proton.me/blog/lumo-apertus-partnership). Apache 2.0.

Also:
* StarCoder / StarCoder2. Commercial restrictions.
  * Not instruction-tuned.
  * StarCoder2 3B/7B.
    * Tool: llama.cpp (MIT) / LM Studio (Proprietary).

### Embedding models

* Nomic Embed Text (via https://tinfoil.sh/models/nomic-embed-text). Apache 2.0.

## Open source (weights, training data, code) machine learning models for local usage

### Requirements

* CPU-only (not Apple-specific)
* 16GB RAM

### Agent harness

#### pi.dev

See overview at https://petronellatech.com/blog/pi-dev-platform-review/
> ... no analytics beyond optional install telemetry that you can disable by
> setting `PI_TELEMETRY=0` or
> flipping `enableInstallTelemetry` to `false` in settings.json,
> per the README.

##### Architecture

| Layer | Tool | Purpose |
|-------|------|---------|
| **Agent Interface** | pi.dev | Terminal coding agent |
| **Inference Backend** | Ollama OR llama.cpp | Runs model locally |
| **Model** | Instruction-tuned model |  |

[Pi integrates directly with the llama.cpp router.](https://pi.dev/docs/latest/models#connect-local-models)

##### Modules

###### xberg

https://pi.dev/packages/@xberg-io/opencode-xberg
using `xberg` binary.
Extracts info from documents
([e.g.](https://github.com/xberg-io/xberg/blob/v1.3.10/README.md?plain=1#L485) `.pdf`, `.png`, `.mp3`, `.html`, `.eml`, `.zip`, `.tex`,  code),
in some cases using OCR,
producing Markdown (or other formats).

See also other packages from xberg-io
(probably being absorbed by `xberg`)
e.g.:
* Crawl/scrape websites (using `crawlberg`).
* Convert websites to Markdown (using `crawlberg`).
* Programming languages parsing.

###### anydoc

https://pi.dev/packages/@everyx/pi-read-doc
using `anydoc`.
Extracts info from documents,
in some cases using OCR,
producing Markdown.

It does not list `eml` among the supported formats.

##### Emacs integration

Among the many options:
https://melpa.org/#/pilish

### Model optimisations

* MLX - for Apple Silicon (M1, ...).
* vLLM - primarily for NVIDIA and AMD GPUs.

### Models

#### OLMo

* OLMo 2 1B Instruct (https://huggingface.co/collections/allenai/olmo-2)
* OLMo 2 1B Instruct GGUF (quantized - https://huggingface.co/collections/allenai/olmo-2)
* OLMo 3 7B-Instruct (https://allenai.org/olmo). Apache 2.0.
  * Base < Instruct < Think; only Think performs well at LiveCodeBench v3.
* OLMo 3 7B-Think (https://allenai.org/olmo). Apache 2.0.

Tool: Ollama (MIT) / llama.cpp (MIT).

#### Apertus

* Apertus 1.1 Mini 0.5B Instruct (https://www.apertus-ai.org/pages/documentation/)
* Apertus 1.1 Mini 1.5B Instruct (https://www.apertus-ai.org/pages/documentation/)

https://www.aimadetools.com/blog/how-to-run-apertus-locally/ says ok on CPU:

> | Model | BF16 VRAM | ... | Minimum hardware |
> | --- | --- | --- | --- |
> | 0.5B | ~1 GB | ... | Any modern laptop CPU |
> | 1.5B | ~3 GB | ... | Laptop with 8GB RAM |

## Foundational datasets for open pretraining

* Common Crawl
  * Public domain web corpus (~344 TiB, March 2026).
  * Raw base for many derivatives.
* OSCAR
  * Filtered, cleaned Common Crawl in multiple languages.
* mC4
  * Multilingual Common Crawl variant for cross-language training.
* RedPajama-Data. By Together AI. Apache 2.0.
  * ~100B tokens replicating LLaMA-style training from Common Crawl.
  * Enables reproducible pretraining.
* The Pile. By EleutherAI. MIT.
  * 825 GB, 22 diverse sources (books, papers, GitHub, etc.).
  * Widely used as training base.
