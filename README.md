# TinyGPT-1M — The Pocket Shakespeare Engine

**Live app:** https://samratbarman1013-commits.github.io/tinygpt-1m-app/

A **1,035,072-parameter GPT (decoder-only transformer)** trained completely from scratch —
no pre-trained weights, no APIs — on the complete works of Shakespeare (TinyShakespeare, ~1M characters).
It runs **100% on-device**: the int8-quantized weights and a from-scratch JavaScript inference engine
(KV-cache attention, typed arrays) execute in your browser or Android WebView. No server, no internet needed.

## The model

| | |
|---|---|
| Parameters | 1,035,072 |
| Architecture | pre-LN GPT: 4 layers, 4 heads, d_model 144, MLP 4x |
| Context | 128 characters (sliding window for longer text) |
| Tokenizer | character-level (65 tokens) |
| Training | PyTorch, AdamW, cosine LR schedule, 2,500 steps (~10M tokens seen) |
| Validation loss | 1.709 (best checkpoint) |

## Try it

1. Open the live site above (or download `index.html` from the release and open it locally).
2. Type an opening line, e.g. `ROMEO:` then a newline.
3. Tune temperature / top-k, press **Write**.

## Android APK

The release contains `TinyGPT-1M.apk` — a WebView app with the entire model bundled.
Install it by enabling "install from unknown sources" and opening the APK. Fully offline.

## Honest disclaimer

1M parameters is *tiny* by modern standards (GPT-2 small is 124× bigger). This model generates
charming pseudo-Elizabethan nonsense — real words, real character names, plausible stage
directions — not coherent poetry. That is the honest capability of a model this size trained
on ~1 MB of text.
