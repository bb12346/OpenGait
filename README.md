<img src="./assets/logo2.png" width = "320" height = "110" alt="logo" />

<div align="center"><img src="./assets/nm.gif" width = "100" height = "100" alt="nm" /><img src="./assets/bg.gif" width = "100" height = "100" alt="bg" /><img src="./assets/cl.gif" width = "100" height = "100" alt="cl" /></div>

------------------------------------------

OpenGait is a flexible and extensible gait recognition project provided by the [Shiqi Yu Group](https://faculty.sustech.edu.cn/yusq/) and supported in part by [WATRIX.AI](http://www.watrix.ai).


## What's New
- [Mar 2022] More results on [GREW](https://www.grew-benchmark.org) are supported, and the model files are coming soon.
- [Mar 2022] Dataset [GREW](https://www.grew-benchmark.org) is supported in [datasets/GREW](./datasets/GREW).
- [Mar 2022] [HID](http://hid2022.iapr-tc4.org/) support is ready in [datasets/HID](./datasets/HID).

## Highlighted features
- **Mutiple Dataset supported**: OpenGait supports four popular gait datasets: [CASIA-B](http://www.cbsr.ia.ac.cn/english/Gait%20Databases.asp), [OUMVLP](http://www.am.sanken.osaka-u.ac.jp/BiometricDB/GaitMVLP.html), [HID](http://hid2022.iapr-tc4.org/), and [GREW](https://www.grew-benchmark.org).
- **Multiple Models Support**: We reproduced several SOTA methods, and reached the same or even the better performance. 
- **DDP Support**: The officially recommended [`Distributed Data Parallel (DDP)`](https://pytorch.org/tutorials/intermediate/ddp_tutorial.html) mode is used during both the training and testing phases.
- **AMP Support**: The [`Auto Mixed Precision (AMP)`](https://pytorch.org/tutorials/recipes/recipes/amp_recipe.html?highlight=amp) option is available.
- **Nice log**: We use [`tensorboard`](https://pytorch.org/docs/stable/tensorboard.html) and `logging` to log everything, which looks pretty.

## Model Zoo

###  [CASIA-B](http://www.cbsr.ia.ac.cn/english/Gait%20Databases.asp)
|                                                                                          Model                                                                                          |     NM     |     BG     |     CL     | Configuration                                                                                | Input Size | Inference Time |   Model Size   |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :--------: | :--------: | :--------: | :-------------------------------------------------------------------------------------------: | :--------: | :------------: | :------------: |
|                                                                                        Baseline                                                                                         |    96.3    |    92.2    |    77.6    | [baseline.yaml](config/baseline/baseline.yaml)                                                        |   64x44    |      12s       |     3.78M      |
|                                                                [GaitSet(AAAI2019)](https://arxiv.org/pdf/1811.06186.pdf)                                                                | 95.8(95.0) | 90.0(87.2) | 75.4(70.4) | [gaitset.yaml](config/gaitset/gaitset.yaml)                                                          |   64x44    |      13s       |     2.59M      |
|                                                   [GaitPart(CVPR2020)](http://home.ustc.edu.cn/~saihui/papers/cvpr2020_gaitpart.pdf)                                                    | 96.1(96.2) | 90.7(91.5) | 78.7(78.7) | [gaitpart.yaml](config/gaitpart/gaitpart.yaml)                                                        |   64x44    |      56s       |     1.20M      |
|                                                        [GLN*(ECCV2020)](http://home.ustc.edu.cn/~saihui/papers/eccv2020_gln.pdf)                                                        | 96.4(95.6) | 93.1(92.0) | 81.0(77.2) | [gln_phase1.yaml](config/gln/gln_phase1.yaml), [gln_phase2.yaml](config/gln/gln_phase2.yaml) |   128x88   |    47s/46s     | 8.54M / 14.70M |
| [GaitGL(ICCV2021)](https://openaccess.thecvf.com/content/ICCV2021/papers/Lin_Gait_Recognition_via_Effective_Global-Local_Feature_Representation_and_Local_Temporal_ICCV_2021_paper.pdf) | 97.4(97.4) | 94.5(94.5) | 83.8(83.6) | [gaitgl.yaml](config/gaitgl/gaitgl.yaml)                                                            |   64x44    |      38s       |     3.10M      |

### [OUMVLP](http://www.am.sanken.osaka-u.ac.jp/BiometricDB/GaitMVLP.html)
|                                                                                          Model                                                                                          |   Rank@1   |                Configuration                 | Input Size | Inference Time | Model Size |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :--------: | :------------------------------------------: | :--------: | :-------------: | :--------: |
|                                                                                        Baseline                                                                                         |    86.7    | [baseline.yaml](config/baseline/baseline_OUMVLP.yaml) |   64x44    | 1m13s          |   44.11M   |
|                                                                [GaitSet(AAAI2019)](https://arxiv.org/pdf/1811.06186.pdf)                                                                | 87.2(87.1) |  [gaitset.yaml](config/gaitset/gaitset_OUMVLP.yaml)  |   64x44    | 1m26s          |   6.31M    |
|                                                   [GaitPart(CVPR2020)](http://home.ustc.edu.cn/~saihui/papers/cvpr2020_gaitpart.pdf)                                                    | 88.6(88.7) | [gaitpart.yaml](config/gaitpart/gaitpart_OUMVLP.yaml) |   64x44    | 8m04s          |   3.78M    |
| [GaitGL(ICCV2021)](https://openaccess.thecvf.com/content/ICCV2021/papers/Lin_Gait_Recognition_via_Effective_Global-Local_Feature_Representation_and_Local_Temporal_ICCV_2021_paper.pdf) | 89.9(89.7) |   [gaitgl.yaml](config/gaitgl/gaitgl_OUMVLP.yaml)   |   64x44    | 5m23s          |   95.62M   |


### [GREW](https://www.grew-benchmark.org)
|                                                                                          Model                                                                                          |   Rank@1   |                Configuration                 | Input Size | Inference Time | Model Size |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :--------: | :------------------------------------------: | :--------: | :-------------: | :--------: |
|  Baseline                       |    48.5    | [baseline.yaml](config/baseline/baseline_GREW.yaml)   |   64x44    | 2m23s          |   84.12M   |
| [GaitSet(AAAI2019)](https://arxiv.org/pdf/1811.06186.pdf)                        |    48.4    | [gaitset.yaml](config/gaitset/gaitset_GREW.yaml)                                            |   64x44        | -              |   -        |
|  [GaitPart(CVPR2020)](http://home.ustc.edu.cn/~saihui/papers/cvpr2020_gaitpart.pdf)                       |    47.6    | [gaitpart.yaml](config/gaitpart/gaitpart_GREW.yaml)                                            |   64x44        | -              |   -        |
|  [GaitGL(ICCV2021)](https://openaccess.thecvf.com/content/ICCV2021/papers/Lin_Gait_Recognition_via_Effective_Global-Local_Feature_Representation_and_Local_Temporal_ICCV_2021_paper.pdf)                         |    41.5    | [gaitgl.yaml](config/gaitgl/gaitgl_GREW.yaml)                                            |   64x44        | -              |   -        |
|  [GaitGL(BNNeck)(ICCV2021)](https://openaccess.thecvf.com/content/ICCV2021/papers/Lin_Gait_Recognition_via_Effective_Global-Local_Feature_Representation_and_Local_Temporal_ICCV_2021_paper.pdf)                         |    51.7    | [gaitgl.yaml](config/gaitgl/gaitgl_GREW_BNNeck.yaml)                                            |   64x44        | -              |   -        |
|  [RealGait(Arxiv now)](https://arxiv.org/pdf/2201.04806.pdf)|    (54.1)    | -                                            |   -        | -              |   -        |


------------------------------------------

The results in the parentheses are mentioned in the papers. 

**Note**:
- All results are Rank@1, excluding identical-view cases.
- The shown result of GLN is implemented without compact block. 
- Only two RTX3090 are used for infering CASIA-B, and eight are used for infering OUMVLP.



## Get Started
### Installation
1. clone this repo.
    ```
    git clone https://github.com/ShiqiYu/OpenGait.git
    ```
2. Install dependenices:
    - pytorch >= 1.6
    - torchvision
    - pyyaml
    - tensorboard
    - opencv-python
    - tqdm
    - py7zr
    
    Install dependenices by [Anaconda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html):
    ```
    conda install tqdm pyyaml tensorboard opencv py7zr
    conda install pytorch==1.6.0 torchvision -c pytorch
    ```    
    Or, Install dependenices by pip:
    ```
    pip install tqdm pyyaml tensorboard opencv-python py7zr
    pip install torch==1.6.0 torchvision==0.7.0
    ```
### Prepare dataset
See [prepare dataset](docs/0.prepare_dataset.md).

### Get trained model
- Option 1:
    ```
    python misc/download_pretrained_model.py
    ```
- Option 2: Go to the [release page](https://github.com/ShiqiYu/OpenGait/releases/), then download the model file and uncompress it to [output](output).

### Train
Train a model by
```
CUDA_VISIBLE_DEVICES=0,1 python -m torch.distributed.launch --nproc_per_node=2 opengait/main.py --cfgs ./config/baseline/baseline.yaml --phase train
```
- `python -m torch.distributed.launch` [DDP](https://pytorch.org/tutorials/intermediate/ddp_tutorial.html) launch instruction.
- `--nproc_per_node` The number of gpus to use, and it must equal the length of `CUDA_VISIBLE_DEVICES`.
- `--cfgs` The path to config file.
- `--phase` Specified as `train`.
<!-- - `--iter` You can specify a number of iterations or use `restore_hint` in the config file and resume training from there. -->
- `--log_to_file` If specified, the terminal log will be written on disk simultaneously. 

You can run commands in [train.sh](train.sh) for training different models.

### Test
Evaluate the trained model by
```
CUDA_VISIBLE_DEVICES=0,1 python -m torch.distributed.launch --nproc_per_node=2 opengait/main.py --cfgs ./config/baseline/baseline.yaml --phase test
```
- `--phase` Specified as `test`.
- `--iter` Specify a iteration checkpoint.

**Tip**: Other arguments are the same as train phase.

You can run commands in [test.sh](test.sh) for testing different models.

## Customize
1. Read the [detailed config](docs/1.detailed_config.md) to figure out the usage of needed setting items;
2. See [how to create your model](docs/2.how_to_create_your_model.md);
3. There are some advanced usages, refer to [advanced usages](docs/3.advanced_usages.md), please.

## Warning
- In `DDP` mode, zombie processes may be generated when the program terminates abnormally. You can use this command [sh misc/clean_process.sh](./misc/clean_process.sh) to clear them. 

## Authors:
**Open Gait Team (OGT)**
- [Chao Fan (樊超)](https://faculty.sustech.edu.cn/?p=128578&tagid=yusq&cat=2&iscss=1&snapid=1&orderby=date), 12131100@mail.sustech.edu.cn
- [Chuanfu Shen (沈川福)](https://faculty.sustech.edu.cn/?p=95396&tagid=yusq&cat=2&iscss=1&snapid=1&orderby=date), 11950016@mail.sustech.edu.cn
- [Junhao Liang (梁峻豪)](https://faculty.sustech.edu.cn/?p=95401&tagid=yusq&cat=2&iscss=1&snapid=1&orderby=date), 12132342@mail.sustech.edu.cn

## Acknowledgement
- GLN: [Saihui Hou (侯赛辉)](http://home.ustc.edu.cn/~saihui/index_english.html)
- GaitGL: [Beibei Lin (林贝贝)](https://scholar.google.com/citations?user=KyvHam4AAAAJ&hl=en&oi=ao)
- GREW: [GREW TEAM](https://www.grew-benchmark.org)
<!-- ## Citation
```
``` -->

**Note:**
This code is only used for **academic purposes**, people cannot use this code for anything that might be considered commercial use.
