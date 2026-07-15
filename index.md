---
title: Niles Burbank Assorted AI Content
---

## Test Results

- [Inference Performance on Strix Halo](framework.md)

## Resources

### AI & ROCm Deployment (mostly specific to Strix Halo)

[Strix Halo AI Toolboxes](https://strix-halo-toolboxes.com/)\
Actively maintained, as of Jun 2026. Containers for deploying AI workflows on Strix Halo systems running Linux, performance results, and more. Impressively comprehensive, considering that the author is doing this as a "hobby" (his term).

[The State of Flash Attention on ROCm]( https://zdtech.substack.com/p/the-state-of-flash-attention-on-rocm)\
Jul 2025. Specific to MI300X, but a good overview of the Flash Attention implementations available for AMD GPUs at the time of writing.

[AMD Ryzen AI Max 395: GTT Memory Settings](https://github.com/technigmaai/technigmaai-wiki/wiki/AMD-Ryzen-AI-Max--395:-GTT--Memory-Step%E2%80%90by%E2%80%90Step-Instructions-(Ubuntu-24.04))\
Aug 2025. I’m not entirely convinced that making all physical memory available as GTT memory is the best practice, but this provides a template for making more memory available for graphics than can be directly reserved via BIOS.

[Compiling VLLM from source on Strix Halo](https://community.frame.work/t/how-to-compiling-vllm-from-source-on-strix-halo/77241)\
Oct 2025. With availability of containers and whls for upstream vLLM with ROCm support, building from source typically won’t be necessary but this is a good reference for the curious.

### AMD Resources

[AMD AI Developer Program](https://developer.amd.com/ai-developer-program/?utm_medium=referral&utm_source=social&utm_campaign=aig-team-comp&utm_term=Niles)\
Free program providing complimentary GPU cloud credits, access to training materials, access to community forums. Registering also provides a signal of interest in AI on AMD platforms.
 
### General AI Reading

[Cultural Bias in AI](bias.md)\
Some notes on academic work to identify cultural biases in LLMs.

[Pope Leo’s AI Encyclical](https://www.vatican.va/content/leo-xiv/en/encyclicals/documents/20260515-magnifica-humanitas.html)\
May 2026. Many summaries around, but worth reading in its entirety. References to Gandalf, Guernica and much more.

[Demis Hassabis on governance of frontier AI](https://demishassabis.substack.com/p/a-framework-for-frontier-ai-and-the-dawning-of-a-new-age)\
Jul 2026. A thoughtful take on the topic, although the proposed path forward is more US-centric than I would have expected.
