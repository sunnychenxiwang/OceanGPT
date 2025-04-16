
<div align="center">
<img src="figs/logo.jpg" width="300px">

**OceanGPT (沧渊): Ocean Foundation Model**

<p align="center">
  <a href="https://github.com/zjunlp/OceanGPT">Project</a> •
  <a href="https://arxiv.org/abs/2310.02031">Paper</a> •
  <a href="https://huggingface.co/collections/zjunlp/oceangpt-664cc106358fdd9f09aa5157">Models</a> •
  <a href="http://oceangpt.zjukg.cn/">Web</a> •
  <a href="#overview">Overview</a> •
  <a href="#quickstart">Quickstart</a> •
  <a href="#citation">Citation</a>
</p>

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
![](https://img.shields.io/badge/PRs-Welcome-red)  <a href='https://hyper.ai/datasets/32992'><img src='https://img.shields.io/badge/Dataset-HyperAI超神经-pink'></a> 


</div>

## Table of Contents

- <a href="#news">What's New</a>
- <a href="#overview">Overview</a>
- <a href="#quickstart">Quickstart</a>
- <a href="#chat-with-our-demo-on-gradio"> 🤗Chat with Our Demo on Gradio</a>
- <a href="#inference">Inference</a>
    - <a href="#models">Models</a>
    - <a href="#efficient-inference-with-llamacpp-ollama-vllm">Efficient Inference with llama.cpp, ollama, vLLM</a>
- <a href="#citation">Citation</a>

## 🔔News
- **2025-04-09, we collect sonar data using a ROV for model training and test OceanGPT-Coder in operating the AUV during a pool experiment.**
- **2024-12-01, we collect more publicly available sonar data and scientific images for model training.**
- **2024-08-01, we launch bilingual (Chinese-English) multimodal large language model OceanGPT-o with sonar and ocean science image data collection and training.**
- **2024-07-04, we release the OceanGPT-Basic-14B/2B and the updated version of OceanGPT-Basic-7B.**
- **2024-06-04, [OceanGPT](https://arxiv.org/abs/2310.02031) is accepted by ACL 2024. 🎉🎉**
- **2023-10-04, we release the paper "[OceanGPT: A Large Language Model for Ocean Science Tasks](https://arxiv.org/abs/2310.02031)" and release OceanGPT-Basic-7B based on LLaMA2.**
- **2023-05-01, we launch the OceanGPT (沧渊) project.**
---

### Models

| Model Name        |        ModelScope                                                   | Modelers                                                                 | HuggingFace                                                               |
|-------------------|-----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| OceanGPT-Basic-8B (based on Qwen, **recommended**)  | To be released                                                                    | To be released                                                                         | To be released        
| OceanGPT-o-7B (based on Qwen, **recommended**)  | To be released                                                                    | To be released                                                                         | To be released                                                                          |
| OceanGPT-Coder-7B (based on Qwen, **recommended**)  | To be released                                                                    | To be released                                                                         | To be released                                                                          |
| OceanGPT-Basic-14B (based on Qwen, legacy) |<a href="https://modelscope.cn/models/ZJUNLP/OceanGPT-14B-v0.1" target="_blank">14B</a>  |   | <a href="https://huggingface.co/zjunlp/OceanGPT-14B-v0.1" target="_blank">14B</a> |
| OceanGPT-Basic-7B (based on Qwen, legacy) |  <a href="https://modelscope.cn/models/ZJUNLP/OceanGPT-7b-v0.2" target="_blank">7B</a>  |    |  <a href="https://huggingface.co/zjunlp/OceanGPT-7b-v0.2" target="_blank">7B</a>   |
| OceanGPT-Basic-2B (based on MiniCPM, legacy) | <a href="https://modelscope.cn/models/ZJUNLP/OceanGPT-2B-v0.1" target="_blank">2B</a>  |    |  <a href="https://huggingface.co/zjunlp/OceanGPT-2B-v0.1" target="_blank">2B</a>   |


---

- ❗**Please note that the ocean domain Q&A in the online demo system (including the video) is based on knowledge base augmentation and a "general-specialized integration" approach, and the generated content differs from that of the open-source models (注意：在线演示系统和视频里的海洋专业问答采用了知识增强，因此和开源模型存在差异)！**

### Instruction Data

| Data Name        | HuggingFace                                                          | WiseModel                                                                 | ModelScope                                                                |
|-------------------|-----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| OceanInstruct  | <a href="" target="_blank">50K</a> | <a href="" target="_blank">50K</a> | <a href="1" target="_blank">50K</a> |
| OceanInstruct-o  | <a href="" target="_blank">50K</a> | <a href="" target="_blank">50K</a> | <a href="1" target="_blank">50K</a> |
---
- ❗**Some of the instruction data are synthetic data; we apologize for any inaccuracies that may exist (部分指令数据为合成数据，如存在错误敬请谅解)！**

## 🌟Overview

This is the OceanGPT (沧渊) project, which aims to build ocean foundation model.

- ❗**Disclaimer: This project is purely an academic exploration rather than a product(本项目仅为学术探索并非产品应用). Please be aware that due to the inherent limitations of large language models, there may be issues such as hallucinations.**

<div align="center">
<img src="figs/overview.png" width="60%">
<img src="figs/vedio.gif" width="60%">
</div>


## ⏩Quickstart

```
conda create -n py3.11 python=3.11
conda activate py3.11
pip install -r requirements.txt
```

### Download the model
#### Download from HuggingFace
```shell
git lfs install
git clone https://huggingface.co/zjunlp/OceanGPT-14B-v0.1
```
or
```
huggingface-cli download --resume-download zjunlp/OceanGPT-14B-v0.1 --local-dir OceanGPT-14B-v0.1 --local-dir-use-symlinks False
```
#### Download from WiseModel
```shell
git lfs install
git clone https://www.wisemodel.cn/zjunlp/OceanGPT-14B-v0.1.git
```
#### Download from ModelScope
```shell
git lfs install
git clone https://www.modelscope.cn/ZJUNLP/OceanGPT-14B-v0.1.git
```

### Inference
#### Inference by HuggingFace	
```python
from transformers import AutoModelForCausalLM, AutoTokenizer
import torch

device = "cuda" # the device to load the model onto
path = 'YOUR-MODEL-PATH'

model = AutoModelForCausalLM.from_pretrained(
    path,
    torch_dtype=torch.bfloat16,
    device_map="auto"
)
tokenizer = AutoTokenizer.from_pretrained(path)

prompt = "Which is the largest ocean in the world?"
messages = [
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": prompt}
]
text = tokenizer.apply_chat_template(
    messages,
    tokenize=False,
    add_generation_prompt=True
)
model_inputs = tokenizer([text], return_tensors="pt").to(device)

generated_ids = model.generate(
    model_inputs.input_ids,
    max_new_tokens=512
)
generated_ids = [
    output_ids[len(input_ids):] for input_ids, output_ids in zip(model_inputs.input_ids, generated_ids)
]

response = tokenizer.batch_decode(generated_ids, skip_special_tokens=True)[0]
```
#### Inference by vllm
```python
from transformers import AutoTokenizer
from vllm import LLM, SamplingParams

path = 'YOUR-MODEL-PATH'

tokenizer = AutoTokenizer.from_pretrained(path)

prompt = "Which is the largest ocean in the world?"
messages = [
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": prompt}
]
text = tokenizer.apply_chat_template(
    messages,
    tokenize=False,
    add_generation_prompt=True
)

sampling_params = SamplingParams(temperature=0.8, top_k=50)
llm = LLM(model=path)

response = llm.generate(text, sampling_params)
```

## 🤗Chat with Our Demo on Gradio

### Online Demo <!-- omit in toc --> 

We provide users with an interactive Gradio demo accessible online.

### Local WebUI Demo
You can easily deploy the interactive interface locally using the code we provide.

```python
python app.py
```
Open `https://localhost:7860/` in browser and enjoy the interaction with OceanGPT.

## 📌Inference

### Efficient Inference with llama.cpp, ollama, vLLM

<details> 
<summary>llama.cpp now officially supports Models based Qwen2.5-hf convert to gguf. Click to see.</summary>

Download OceanGPT PyTorch model from huggingface to "OceanGPT" folder.

Clone llama.cpp and make:
```shell
git clone https://github.com/ggml-org/llama.cpp
cd llama.cpp
make llama-cli
```

And then convert PyTorch model to gguf files:
```shell
python convert-hf-to-gguf.py OceanGPT --outfile OceanGPT.gguf
```

Running the model:
```shell
./llama-cli -m OceanGPT.gguf \
    -co -cnv -p "Your prompt" \
    -fa -ngl 80 -n 512
```
  </details>

<details> 
<summary>ollama now officially supports Models based Qwen2.5. Click to see.</summary>

Create a file named `Modelfile`
```shell
FROM ./OceanGPT.gguf
TEMPLATE "[INST] {{ .Prompt }} [/INST]"
```

Create the model in Ollama:
```shell
ollama create example -f Modelfile
```

Running the model:
```shell
ollama run example "What is your favourite condiment?"
```
  </details>

<details>
<summary> vLLM now officially supports Models based Qwen2.5-VL and Qwen2.5. Click to see. </summary>

1. Install vLLM(>=0.7.3):
```shell
pip install vllm
```

2. Run Example:
* [MLLM](https://docs.vllm.ai/en/latest/getting_started/examples/vision_language.html) 
* [LLM](https://docs.vllm.ai/en/latest/getting_started/quickstart.html) 
  </details>


## 🌻Acknowledgement

OceanGPT (沧渊) is trained based on the open-sourced large language models including [Qwen](https://huggingface.co/Qwen), [MiniCPM](https://huggingface.co/collections/openbmb/minicpm-2b-65d48bf958302b9fd25b698f), [LLaMA](https://huggingface.co/meta-llama). Thanks for their great contributions!

## Limitations

- The model may have hallucination issues.

- We did not optimize the identity and the model may generate identity information similar to that of Qwen/MiniCPM/LLaMA/GPT series models.

- The model's output is influenced by prompt tokens, which may result in inconsistent results across multiple attempts.

- The model requires the inclusion of specific simulator code instructions for training in order to possess simulated embodied intelligence capabilities (the simulator is subject to copyright restrictions and cannot be made available for now), and its current capabilities are quite limited.


### 🚩Citation

Please cite the following paper if you use OceanGPT in your work.

```bibtex
@article{bi2024oceangpt,
  title={OceanGPT: A Large Language Model for Ocean Science Tasks},
  author={Bi, Zhen and Zhang, Ningyu and Xue, Yida and Ou, Yixin and Ji, Daxiong and Zheng, Guozhou and Chen, Huajun},
  journal={arXiv preprint arXiv:2310.02031},
  year={2024}
}

```

---
