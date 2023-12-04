# Official repo for StableLLaVA
**StableLLaVA: Enhanced Visual Instruction Tuning with Synthesized Image-Dialogue Data**

Yanda Li, [Chi Zhang](https://icoz69.github.io/), Gang Yu, Zhibin Wang, Bin Fu, Guosheng Lin, Chunhua Shen, Ling Chen, Yunchao Wei

[[Arxiv]](https://arxiv.org/abs/2308.10253v1) 
[[Project Page]](https://icoz69.github.io/stablellava-official/)


**This repository offers a collection of AI-generated datasets specifically tailored for visual instruction tuning.**

## Abstract

 The remarkable multimodal capabilities demonstrated by OpenAI's GPT-4 have sparked significant interest in the development of multimodal Large Language Models (LLMs). A primary research objective of such models is to  align visual and textual modalities effectively while comprehending human instructions.
 Current methodologies often rely on annotations derived from benchmark datasets to construct image-dialogue datasets for training purposes, akin to instruction tuning in LLMs. However,  these datasets often exhibit domain bias, potentially constraining the generative capabilities of the models. In an effort to mitigate these limitations, we propose a novel data collection methodology that synchronously synthesizes images and dialogues for visual instruction tuning. This approach harnesses the power of generative models, marrying the abilities of ChatGPT and text-to-image generative models to yield a diverse and controllable dataset with varied image content. Additionally, datasets can be arbitrarily scaled. This not only provides greater flexibility compared to existing methodologies but also significantly enhances several model capabilities. Our research includes comprehensive experiments conducted on various datasets. The results emphasize substantial enhancements in more than ten commonly assessed capabilities. Additionally, our model achieves state-of-the-art results across multiple widely recognized multimodal benchmarks. 

<img src='image/teaser.png'>

## Pipeline 
<img src='image/pipeline.png'>

The prompt-dialogue of varies abilities are saved in [dataset](https://github.com/crystraldo/StableLLAVA/tree/main/dataset).

The synthesized prompt-dialogue datasets of various abilities are saved in [dataset](https://github.com/crystraldo/StableLLAVA/tree/main/dataset). Please follow the steps below to generate datasets with LLaVA format.

1. Use [SD-XL](https://github.com/crystraldo/StableLLAVA/blob/main/stable_diffusion.py) to generate images as training images. It will take ~13s to generate one image on V100.
```
python stable_diffusion.py --prompt_path dataset/animal.json --save_path train_set/animal/
```

2. Use [data_to_llava](https://github.com/crystraldo/StableLLAVA/blob/main/data_to_llava.py) to convert dataset format for LLaVA model training.
```
python data_to_llava.py --image_path train_set/ --prompt_path dataset/ --save_path train_ano/
```
## Results
# Qualitative Results
<img src='image/result.png'>
<img src='image/result2.png'>

# Quantitative Results
<img src='image/quan.png'>

3. For training with the generated datasets, you can use LLaVA official code [LLaVA](https://github.com/haotian-liu/LLaVA)


 ## TO-DO LIST
- [ ] Update datasets and instruction templates
- [ ] Keep incorporating more capabilities
- [ ] Demo and Codes
