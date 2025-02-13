# ComfyUI_DiffuEraser
[DiffuEraser](https://github.com/lixiaowen-xw/DiffuEraser) is  a diffusion model for video Inpainting, you can use it in ComfyUI

# Update
* 新增单mask模式，处理固定水印用，见示例图  
* Added single mask mode for handling fixed watermarks,new example;   
* 方法前置处理的视频反而更好，可能是代码的问题，所以增加输出前置视频
* The video pre processed by the method is actually better, which may be a problem with the code, so adding output pre processed video is necessary


# 1. Installation

In the ./ComfyUI /custom_node directory, run the following:   
```
git clone https://github.com/smthemex/ComfyUI_DiffuEraser.git
```
---

# 2. Requirements  
* no need, because it's base in sd1.5 ,Perhaps someone may be missing the library.没什么特殊的库,懒得删了
```
pip install -r requirements.txt
```
# 3. Models
* sd1.5 [address](https://modelscope.cn/models/AI-ModelScope/stable-diffusion-v1-5/files) v1-5-pruned-emaonly.safetensors #example
* pcm 1.5 lora [address](https://huggingface.co/wangfuyun/PCM_Weights/tree/main/sd15)   pcm_sd15_smallcfg_2step_converted.safetensors  #example
* ProPainter [address](https://github.com/sczhou/ProPainter/releases/tag/v0.1.0) # below example
* unet and brushnet [address](https://huggingface.co/lixiaowen/diffuEraser/tree/main)  # below example

```
--  ComfyUI/models/checkpoints
    |-- any sd1.5 safetensors #任意sd1.5模型
--  ComfyUI/models/DiffuEraser
     |--brushnet
        |-- config.json
        |-- diffusion_pytorch_model.safetensors
     |--unet_main
        |-- config.json
        |-- diffusion_pytorch_model.safetensors
     |--propainter
        |-- ProPainter.pth
        |-- raft-things.pth
        |-- recurrent_flow_completion.pth
```
* If use video to mask #可以用RMBG或者BiRefNet模型脱底
```
-- any/path/briaai/RMBG-2.0   # or auto download 
        |--config.json
        |--model.safetensors
        |--birefnet.py
        |--BiRefNet_config.py
Or
-- any/path/ZhengPeng7/BiRefNet   # or auto download 
        |--config.json
        |--model.safetensors
        |--birefnet.py
        |--BiRefNet_config.py
        |--handler.py
```

# 4.Tips
* video2mask : If only the input video is available, please enable this option (generate mask video). 如果只有输入视频，请开启此选项（生成遮罩视频）
  
# 5 Example
* Use one mask
![](https://github.com/smthemex/ComfyUI_DiffuEraser/blob/main/examplea.png)
* Use RMBG or BiRefNet make video2mask 使用RMBG or BiRefNet将 输入视频转为mask,注意RMBG不能商用.
![](https://github.com/smthemex/ComfyUI_DiffuEraser/blob/main/example.png)
* Use Mask video 使用遮罩视频,可以用其他方法,如sam2一类转化: 
![](https://github.com/smthemex/ComfyUI_DiffuEraser/blob/main/exampleb.png)


# 6.Citation
```
@misc{li2025diffueraserdiffusionmodelvideo,
   title={DiffuEraser: A Diffusion Model for Video Inpainting}, 
   author={Xiaowen Li and Haolan Xue and Peiran Ren and Liefeng Bo},
   year={2025},
   eprint={2501.10018},
   archivePrefix={arXiv},
   primaryClass={cs.CV},
   url={https://arxiv.org/abs/2501.10018}, 
}
```
```
@inproceedings{zhou2023propainter,
   title={{ProPainter}: Improving Propagation and Transformer for Video Inpainting},
   author={Zhou, Shangchen and Li, Chongyi and Chan, Kelvin C.K and Loy, Chen Change},
   booktitle={Proceedings of IEEE International Conference on Computer Vision (ICCV)},
   year={2023}
}
```
```
@misc{ju2024brushnet,
  title={BrushNet: A Plug-and-Play Image Inpainting Model with Decomposed Dual-Branch Diffusion}, 
  author={Xuan Ju and Xian Liu and Xintao Wang and Yuxuan Bian and Ying Shan and Qiang Xu},
  year={2024},
  eprint={2403.06976},
  archivePrefix={arXiv},
  primaryClass={cs.CV}
}
```
```
@article{BiRefNet,
  title={Bilateral Reference for High-Resolution Dichotomous Image Segmentation},
  author={Zheng, Peng and Gao, Dehong and Fan, Deng-Ping and Liu, Li and Laaksonen, Jorma and Ouyang, Wanli and Sebe, Nicu},
  journal={CAAI Artificial Intelligence Research},
  year={2024}
}

```
