## Running OLMo 1B on Android

### Apps

| App | License | F-Droid | Hugging Face Integration | Can access storage | Can search Web | OLMo 1B Support |
| --- | --- | --- | --- | --- | --- | --- |
| **Maid** | MIT | [✅](https://f-droid.org/en/packages/com.danemadsen.maid/) | ❌ | ❌ | ❌ | Via GGUF |
| **PocketPal AI** | MIT | ❌ (but APK on [GitHub](https://github.com/a-ghorbani/pocketpal-ai)) | ✅ | ❌ | ❌ | Via GGUF |

MLC Chat (NPU only) is [unmaintained](https://github.com/mlc-ai/binary-mlc-llm-libs/releases).

See also https://www.promptquorum.com/power-local-llm/best-local-llm-apps-android-2026

### Model

OLMo 1B: https://huggingface.co/allenai/OLMo-2-0425-1B-Instruct-GGUF

https://huggingface.co/allenai/OLMo-2-0425-1B-Instruct-GGUF/tree/main
* Q3_K_L (826 MB; degradation starts showing) <
* Q4_K_S (899 MB) <
* Q4_K_M (936 MB; recommended) <
* Q5_K_S (1.05 GB) <
* Q5_K_M (1.07 GB; good on 6 GB+ RAM phone) <
* Q6_K (1.22 GB; marginal over Q5)

Notes:
* Q4_0 is legacy. Weights chopped into blocks keeping one scale.
  * If ARM-optimised repacks (Q4_0_4_4, Q4_0_8_8), fast.
  * Does not cater for outlier weight in block.
  * Does not give special protection to the attention value projection and the feed-forward down projection - notoriously fragile under quantization.
    * In 2022, Dettmers et al. published [LLM.int8()](https://arxiv.org/abs/2208.07339),
      which discovered that LLM activations have extreme outliers.
      These outliers concentrate in specific rows/columns of certain weight matrices.
* Q4_K_S and Q4_K_M are K-quants (llama.cpp contribution by Kawrakow).
  * The _S, _M, _L suffixes say how many of the sensitive tensors get promoted to a higher-precision quant while the bulk stays at 4-bit.

### Smoke test

"What is 2+2?"

### Minimum Requirements

| Component | Requirement |
|-----------|-------------|
| **RAM** | 8 GB system |
| **Chipset** | Snapdragon 7 series / equivalent |
| **Android** | 6.0+ (12+ recommended) |
| **Quantization** | Q4_K_M |
| **Backend** | llama.cpp (CPU/Vulkan) |
