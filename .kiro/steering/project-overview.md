---
inclusion: always
---

# GenAI Technology Stack — Project Overview

This is a GitHub Pages site that visualizes the GenAI technology stack as an interactive dependency map. It is a single-page static site served from `index.html`.

## Architecture

- Pure static site — single `index.html` with inline CSS and JavaScript, no build tools or bundler
- No external JS/CSS frameworks — vanilla HTML, CSS, and JavaScript only
- Hosted via GitHub Pages from the repo root

## Content Structure

The page renders a layered stack visualization with 10 layers (bottom to top):

1. Hardware (GPU, NVLink, InfiniBand, CPU)
2. Drivers (NVIDIA Driver, EFA Driver, Libfabric, NVML)
3. CUDA & Runtime (CUDA Toolkit, cuDNN, cuBLAS, CUTLASS, CUDA Graphs)
4. Communication (NCCL, MPI, RDMA, Libfabric)
5. ML Frameworks (PyTorch, JAX, TensorFlow)
6. Quantization & Optimization (GPTQ, AWQ, bitsandbytes, SmoothQuant, Transformer Engine, torch.compile, Triton)
7. Training Tools (Megatron-LM, DeepSpeed, FSDP, NeMo, Flash Attention, Apex)
8. Inference & Serving (vLLM, TensorRT-LLM, Triton Inference Server, TGI, SGLang, llama.cpp, ONNX Runtime)
9. Data & Tokenization (HF Transformers, SentencePiece, tiktoken, HF Tokenizers, Arrow/Parquet, WebDataset, HF Datasets)
10. Orchestration & Monitoring (Docker, Kubernetes, Ray, Slurm, torchrun, Nsight Systems/Compute, DCGM, Prometheus, W&B/MLflow)

## Data Model (in `index.html`)

- `layers[]` — array of layer objects with `name`, `color`, and `comps` (component names)
- `deps{}` — dependency map: component → array of components it depends on
- `explanations{}` — detailed descriptions with `desc`, `context`, `scope`, and `license` per component
- Reverse dependencies (`revDeps`) are computed at runtime

## Interaction

Clicking a component highlights it and its dependencies/dependents, dims everything else, and shows a detail panel with description, dependency lists, context, scope, and license info.
