# GPU Poor vs GPU Rich

Recursos da palestra "GPU Poor vs GPU Rich: os desafios de rodar código
escalável com GPU" — Hot N' Code Conference 2026.

## Ferramentas

| Ferramenta | Descrição | Link |
|---|---|---|
| Ollama | Rodar LLMs local — wrapper sobre o llama.cpp | [ollama.com](https://ollama.com) |
| llama.cpp | Engine C++ base para LLMs | [github.com/ggml-org/llama.cpp](https://github.com/ggml-org/llama.cpp) |
| Continue.dev | Coding assistant local no VS Code | [continue.dev](https://continue.dev) |
| vLLM | Inferência em produção | [docs.vllm.ai](https://docs.vllm.ai) |
| ComfyUI | Interface visual para geração de imagem, vídeo e áudio | [github.com/comfyanonymous/ComfyUI](https://github.com/comfyanonymous/ComfyUI) |
| LM Studio | Alternativa ao Ollama com interface gráfica | [lmstudio.ai](https://lmstudio.ai) |
| MLX | Performance nativa no Apple Silicon | [github.com/ml-explore/mlx](https://github.com/ml-explore/mlx) |
| Z-Image | Geração de imagem local | [github.com/Tongyi-MAI/Z-Image](https://github.com/Tongyi-MAI/Z-Image) |
| LTX-2 | Geração de vídeo local | [github.com/Lightricks/LTX-2](https://github.com/Lightricks/LTX-2) |

## Comandos das demos

Rodar um modelo local com Ollama:
```bash
brew install ollama
ollama serve                    # API OpenAI-compatible na porta 11434
ollama run qwen3.5:9b
```


Servir em produção com vLLM:
```bash
pip install vllm
vllm serve meta-llama/Llama-3.1-8B-Instruct --max-model-len 8192
```

Tensor parallelism (modelo dividido entre GPUs):
```bash
vllm serve deepseek-ai/DeepSeek-V4-Flash --tensor-parallel-size 4
```

## Referências

Agrupadas pelos quatro desafios da palestra.

**Caber** — quantização e Memory Math
AI Engineering, cap. 7 "Finetuning" (Chip Huyen)

**Throughput** — batching e atenção
[Continuous batching para inferência de LLM](https://www.anyscale.com/blog/continuous-batching-llm-inference) (Anyscale)
[PagedAttention](https://arxiv.org/abs/2309.06180) — paper original do vLLM

**Cold start**
[Seekable OCI (SOCI)](https://aws.amazon.com/about-aws/whats-new/2022/09/introducing-seekable-oci-lazy-loading-container-images/) (AWS)
[Bottlerocket](https://bottlerocket.dev)

**Fundamentos** — prefill/decode, roofline, métricas
AI Engineering, cap. 9 "Inference Optimization" (Chip Huyen)
[Roofline: An Insightful Visual Performance Model](https://dl.acm.org/doi/10.1145/1498765.1498785) (Williams et al., 2009)
[Making Deep Learning Go Brrrr From First Principles](https://horace.io/brrr_intro.html) (Horace He)
