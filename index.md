---
title: Niles Burbank Assorted AI Content
---

## Test Results

- [Inference Performance on Strix Halo](framework.md)

## References

### ROCm Resources (mostly specific to Strix Halo APUs)

[The State of Flash Attention on ROCm]( https://zdtech.substack.com/p/the-state-of-flash-attention-on-rocm)\
Jul 2025. Specific to MI300X, but a good overview of the Flash Attention implementations available for AMD GPUs at the time of writing.

[AMD Ryzen AI Max 395: GTT Memory Settings](https://github.com/technigmaai/technigmaai-wiki/wiki/AMD-Ryzen-AI-Max--395:-GTT--Memory-Step%E2%80%90by%E2%80%90Step-Instructions-(Ubuntu-24.04))
Aug 2025. I’m not entirely convinced that making all physical memory available as GTT memory is the best practice, but this provides a template for making more memory available for graphics than can be directly reserved via BIOS.

[Compiling VLLM from source on Strix Halo](https://community.frame.work/t/how-to-compiling-vllm-from-source-on-strix-halo/77241)
Oct 2025. With availability of containers and whls for upstream vLLM with ROCm support, building from source typically won’t be necessary but this is a good reference for the curious.

### General AI Reading

[Pope Leo’s AI Encyclical](https://www.vatican.va/content/leo-xiv/en/encyclicals/documents/20260515-magnifica-humanitas.html)
May 2026. Many summaries around, but worth reading in its entirety. References to Gandalf, Guernica and much more.
