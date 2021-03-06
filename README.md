# CFBI: Collaborative Video Object Segmentation by Foreground-Background Integration
The official implementation of Collaborative Video Object Segmentation by Foreground-Background Integration (ECCV 2020, Spotlight). [[paper](https://arxiv.org/abs/2003.08333)] [[demo](https://www.youtube.com/watch?v=xdHi68UFt50)]

CFBI works fine on both [PaddlePaddle](https://www.paddlepaddle.org.cn/) and PyTorch. Based on some necessary considerations, we only release the inference code of CFBI here.

**If you want to get the training code of CFBI, please contact us by email: <zongxin.yang@student.uts.edu.au>. 
And please inform us of your institution and the purpose of using CFBI in the email. 
Thank you for your understanding!**

Framework:
<div align=center><img src="https://github.com/z-x-yang/CFBI/raw/master/utils/overview.png" width="80%"/></div>

Some video segmentation results:
<div align=center><img src="https://github.com/z-x-yang/CFBI/raw/master/utils/quality.png" width="80%"/></div>

## Requirements
    1. Python3
    2. pytorch >= 1.3.0 and torchvision
    3. opencv-python and Pillow
## Getting Started
1. Prepare datasets:
    * Download the [validation split](https://drive.google.com/file/d/1-QrceIl5sUNTKz7Iq0UsWC6NLZq7girr/view?usp=sharing) of YouTube-VOS 2018, and decompress the file to `datasets/YTB/valid`. If you want to evaluate CFBI on YouTube-VOS 2019, please download this [split](https://drive.google.com/file/d/1o586Wjya-f2ohxYf9C1RlRH-gkrzGS8t/view?usp=sharing) instead.
    * Download 480p [TrainVal](https://data.vision.ee.ethz.ch/csergi/share/davis/DAVIS-2017-trainval-480p.zip) split of DAVIS 2017, and decompress the file to `datasets/DAVIS`.
2. Evaluating:
    * **YouTube-VOS**: Download pretrained CFBI, [ResNet101-CFBI](https://drive.google.com/file/d/1ZhoNOcDXGG-PpFXhCixs-L3yA255Wup8/view?usp=sharing), to `pretrain_models`, and then run `bash ytb_eval.sh`. After the evaluation, the result will be packed into a Zip file, which you need to send to [official evaluation server](https://competitions.codalab.org/competitions/19544) to calculate the score. For 2019 version, use this [server](https://competitions.codalab.org/competitions/20127) instead. The pretrained CFBI has been trained on YouTube-VOS using a large batch size (20), which boosts the performance (J&F) to `81.8%` on the validation split of YouTube-VOS 2018.
    * **DAVIS**: Coming.
    * **Fast CFBI**: For reduce the memory usage, we also provide a fast setting in `ytb_eval_fast.sh`. The fast setting enables using `float16` in the matching process of CFBI. Besides, we apply an `atrous strategy` in the global matching of CFBI for further efficiency (The discussion of atrous matching will be submitted to our Arxiv paper soon.). The fast setting will save a large amount of memory and significantly improve the inference speed of CFBI. However, this will only lose very little performance (0.1~0.2 on YouTube-VOS 2018).
    * Another way for saving memory is to increase the number of `--global_chunks`. This will not affect performance but will make the network speed slightly slower.

## Model Zoo
Coming.

## Citing
```
@inproceedings{yang2020collaborative,
  title={Collaborative video object segmentation by foreground-background integration},
  author={Yang, Zongxin and Wei, Yunchao and Yang, Yi},
  booktitle={Proceedings of the European Conference on Computer Vision},
  year={2020}
}
```




