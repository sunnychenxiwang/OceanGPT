<div align="center">
<img src="figs/logo.jpg" width="300px">

**OceanGPT (沧渊): A Large Language Model for Ocean Science Tasks**

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
![](https://img.shields.io/badge/PRs-Welcome-red) 

</div>

## Table of Contents

- <a href="#news">What's New</a>
- <a href="#overview">Overview</a>
- <a href="#quickstart">Quickstart</a>
- <a href="#models">Models</a>
- <a href="#citation">Citation</a>

## 🔔News
- **2024-07-04, we release OceanGPT-14B/2B-v0.1 and OceanGPT-7B-v0.2 based on Qwen and MiniCPM.**
- **2024-06-04, [OceanGPT](https://arxiv.org/abs/2310.02031) is accepted by ACL 2024. 🎉🎉**
- **2023-10-04, we release the paper "[OceanGPT: A Large Language Model for Ocean Science Tasks](https://arxiv.org/abs/2310.02031)" and release OceanGPT-7B-v0.1 based on LLaMA2.**
- **2023-05-01, we launch the OceanGPT (沧渊) project.**
---

## 🌟Overview

This is the OceanGPT (沧渊) project, which aims to build LLMs for ocean science tasks.

<div align="center">
<img src="figs/overview.png" width="60%">
</div>

## ⏩Quickstart

```
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

device = "cuda" # the device to load the model onto
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
llm = LLM(model=path, quantization="fp8")

response = llm.generate(text, sampling_params)
```
## 📌Models

| Model Name        | HuggingFace                                                          | WiseModel                                                                 | ModelScope                                                                |
|-------------------|-----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| OceanGPT-14B-v0.1 (based on Qwen) | <a href="https://huggingface.co/zjunlp/OceanGPT-14B-v0.1" target="_blank">14B</a> | <a href="https://wisemodel.cn/models/zjunlp/OceanGPT-14B-v0.1" target="_blank">14B</a> | <a href="https://modelscope.cn/models/ZJUNLP/OceanGPT-14B-v0.1" target="_blank">14B</a> |
| OceanGPT-7B-v0.2 (based on Qwen) | <a href="https://huggingface.co/zjunlp/OceanGPT-7b-v0.2" target="_blank">7B</a>   | <a href="https://wisemodel.cn/models/zjunlp/OceanGPT-7b-v0.2" target="_blank">7B</a>   | <a href="https://modelscope.cn/models/ZJUNLP/OceanGPT-7b-v0.2" target="_blank">7B</a>   |
| OceanGPT-2B-v0.1 (based on MiniCPM) | <a href="https://huggingface.co/zjunlp/OceanGPT-2B-v0.1" target="_blank">2B</a>   | <a href="https://wisemodel.cn/models/zjunlp/OceanGPT-2b-v0.1" target="_blank">2B</a>   | <a href="https://modelscope.cn/models/ZJUNLP/OceanGPT-2B-v0.1" target="_blank">2B</a>   |
| OceanGPT-V  | To be released                                                                    | To be released                                                                         | To be released                                                                          |
---

## 🌻Acknowledgement

OceanGPT (沧渊) is trained based on the open-sourced large language models including [Qwen](https://huggingface.co/Qwen), [MiniCPM](https://huggingface.co/collections/openbmb/minicpm-2b-65d48bf958302b9fd25b698f), [LLaMA](https://huggingface.co/meta-llama). Thanks for their great contributions!

## Limitations

- The model may have hallucination issues.

- We did not optimize the identity and the model may generate identity information similar to that of Qwen/MiniCPM/LLaMA/GPT series models.

- The model's output is influenced by prompt tokens, which may result in inconsistent results across multiple attempts.


### 🚩Citation

Please cite the following paper if you use OceanGPT in your work.

```bibtex
@article{bi2023oceangpt,
  title={OceanGPT: A Large Language Model for Ocean Science Tasks},
  author={Bi, Zhen and Zhang, Ningyu and Xue, Yida and Ou, Yixin and Ji, Daxiong and Zheng, Guozhou and Chen, Huajun},
  journal={arXiv preprint arXiv:2310.02031},
  year={2023}
}

```

---
