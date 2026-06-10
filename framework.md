## Gemma 4 12B Inference Performance

[Gemma 4 12B launch blog from Google](https://blog.google/innovation-and-ai/technology/developers-tools/introducing-gemma-4-12b/)

Gemma 4 12B is positioned as being almost as capable as Gemma 4 26B, but with a smaller memory footprint. It's a dense model, so actually has more active parameters than Gemma 4 26B. For Strix Halo systems with 128GB memory, Gemma 4 26B is probably the more logical candidate from the Gemma family. With that disclaimer, below are some initial results.

### Generated tokens/sec across batch sizes

| Inference Engine | Model | BS 1 | BS 4 | BS 16 | BS 32 | Command line |
|---|---|---|---|---|---|---|
| vLLM | google/gemma-4-12b-it | 7.85 | 24.14 | 39.63 | 44.52 | vllm bench throughput --model google/gemma-4-12b-it --max-num-seqs [BS] --num-prompts 200 |
| vLLM (with MTP enabled) | google/gemma-4-12b-it | 15.67 | 46.96 | 109.5 | 119.84 | vllm bench throughput --model google/gemma-4-12b-it --max-num-seqs [BS] --num-prompts 200 --dataset-name sharegpt --dataset-path [local path]/ShareGPT_V3_unfiltered_cleaned_split.json --speculative-config '{"method":"mtp","model":"google/gemma-4-12B-it-assistant","num_speculative_tokens":3}' |
| vLLM | cyankiwi/gemma-4-12B-it-AWQ-INT4 | 6.35 | 16.13 | 19.65 | 20.48 | vllm bench throughput --model cyankiwi/gemma-4-12B-it-AWQ-INT4 --max-num-seqs [BS] --num-prompts 200 |
| llama.cpp (ROCm) | ggml-org/gemma-4-12B-it-GGUF:Q4_K_M | 24.13 | 57.4 | 147.35 | 179.44 | ./llama-batched-bench -hf ggml-org/gemma-4-12B-it-GGUF:Q4_K_M -ngl 999 -npp 1028 -ntg 128 -npl 1,4,16,32 |
| llama.cpp (Vulkan) | ggml-org/gemma-4-12B-it-GGUF:Q4_K_M | 23.13 | 70.77 | 114.46 | 179.81 | ./llama-batched-bench -hf ggml-org/gemma-4-12B-it-GGUF:Q4_K_M -ngl 999 -npp 1028 -ntg 128 -npl 1,4,16,32 |

### General observations

- From a functional perspective, all of these approaches to serving the Gemma 4 12B model worked well. No surprises
- Latest vLLM release at time of testing (v0.22.1) does not support Gemma 4 12B, so used a vLLM Nightly build
- Gemma 4 12B implements a new approach to vision and audio inputs, so briefly experimented with those. Both were functional without additional configuration on both vLLM and llama.cpp
- Speculative decode (MTP) works well on both vLLM and llama.cpp. I didn't find an obvious way to benchmark MTP with llama.cpp, but it seemed to yield a performance improvement when enabled.
- My intuition (not backed by any scientific rigour) is that the native BF16 model is gives slightly higher quality than the quantized models. In particular, the vision capabilities seemed a bit more reliable.

### Deploying an inference endpoint with Gemma 4 12B

Command lines used for user experience testing:

with vLLM:
```
vllm serve --model google/gemma-4-12b-it --speculative-config '{"method":"mtp","model":"google/gemma-4-12B-it-assistant","num_speculative_tokens":3}'
```
with llama.cpp:
```
./llama-server -hf unsloth/gemma-4-12B-it-qat-GGUF:UD-Q4_K_XL -ngl 999 --spec-type draft-mtp --spec-draft-n-max 3
```

### Notes on configuration

- System HW: Framework Desktop with Ryzen AI Max+ 395 and 128GB system memory
- Shared memory configuration: 96GB reserved GPU memory, configured via BIOS
- OS: Ubuntu 26.04 with upstream amdgpu driver
- ROCm: 7.13
- vLLM run using Docker image vllm/vllm-openai-rocm:nightly-d8218b1ee7db3e7582e0151e942d17963a1e3e13 (this uses ROCm 7.2.3)
- llama.cpp run using binaries from llama.cpp repo. Build b9587 for both ROCm and Vulkan

