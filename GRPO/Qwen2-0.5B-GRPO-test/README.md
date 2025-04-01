---
base_model: Qwen/Qwen2-0.5B-Instruct
datasets: AI-MO/NuminaMath-TIR
library_name: transformers
model_name: Qwen2-0.5B-GRPO-test
tags:
- generated_from_trainer
- trl
- grpo
licence: license
---

# Model Card for Qwen2-0.5B-GRPO-test

This model is a fine-tuned version of [Qwen/Qwen2-0.5B-Instruct](https://huggingface.co/Qwen/Qwen2-0.5B-Instruct) on the [AI-MO/NuminaMath-TIR](https://huggingface.co/datasets/AI-MO/NuminaMath-TIR) dataset.
It has been trained using [TRL](https://github.com/huggingface/trl).

## Quick start

```python
from transformers import pipeline

question = "If you had a time machine, but could only go to the past or the future once and never return, which would you choose and why?"
generator = pipeline("text-generation", model="alabebop/Qwen2-0.5B-GRPO-test", device="cuda")
output = generator([{"role": "user", "content": question}], max_new_tokens=128, return_full_text=False)[0]
print(output["generated_text"])
```

## Training procedure

 


This model was trained with GRPO, a method introduced in [DeepSeekMath: Pushing the Limits of Mathematical Reasoning in Open Language Models](https://huggingface.co/papers/2402.03300).

### Framework versions

- TRL: 0.16.0
- Transformers: 4.50.3
- Pytorch: 2.6.0
- Datasets: 3.5.0
- Tokenizers: 0.21.1

## Citations

Cite GRPO as:

```bibtex
@article{zhihong2024deepseekmath,
    title        = {{DeepSeekMath: Pushing the Limits of Mathematical Reasoning in Open Language Models}},
    author       = {Zhihong Shao and Peiyi Wang and Qihao Zhu and Runxin Xu and Junxiao Song and Mingchuan Zhang and Y. K. Li and Y. Wu and Daya Guo},
    year         = 2024,
    eprint       = {arXiv:2402.03300},
}

```

Cite TRL as:
    
```bibtex
@misc{vonwerra2022trl,
	title        = {{TRL: Transformer Reinforcement Learning}},
	author       = {Leandro von Werra and Younes Belkada and Lewis Tunstall and Edward Beeching and Tristan Thrush and Nathan Lambert and Shengyi Huang and Kashif Rasul and Quentin Gallouédec},
	year         = 2020,
	journal      = {GitHub repository},
	publisher    = {GitHub},
	howpublished = {\url{https://github.com/huggingface/trl}}
}
```