### Unsupervised Misaligned Infrared and Visible Image Fusion via Cross-Modality Image Generation and Registration [IJCAI2022 Oral Presentation]

By Di Wang, Jinyuan Liu, Xin Fan, and Risheng Liu

<div align=center>
<img src="https://github.com/wdhudiekou/UMF-CMGR/blob/main/Fig/network.png" width="80%">
</div>


[2022-05-30] The Chinese translation is available! [[中译版本](./pdf/CN.pdf)]   
[2022-05-25] paper is available online! [[arXiv version](https://arxiv.org/pdf/2205.11876.pdf)]  


## Requirements
- CUDA 10.1
- Python 3.6 (or later)
- Pytorch 1.6.0
- Torchvision 0.7.0
- OpenCV 3.4
- Kornia 0.5.11

## Data preparation
1. You can obtain deformation infrared images for training/testing process by
    ```python
       cd ./data
       python get_test_data.py
   
In 'Trainer/train_reg.py', deformable infrared images are generated in real time by default during training.

2. You can obtain self-visual saliency maps for training IVIF fusion by
    ```python
       cd ./data
       python get_svs_map.py

## Get start
1. You can use the pseudo infrared images [[link](https://pan.baidu.com/s/1M79RuHVe6udKhcJIA7yXgA) code: qqyj] generated by our CPSTN to train/test the registration process:
    ```python
       cd ./Trainer
       python train_reg.py

       cd ./Test
       python test_reg.py
   
  Please download the [pretrained model](https://pan.baidu.com/s/199dqOLHyJS9aY5YecuVglA) (code: hk25) of the registration network MRRN.
  
2. If you want to generate pseudo-infrared images using our CPSTN for other datasets, you can directly run following commands:

    ```python
    ## testing
       cd ./CPSTN
       python test.py --dataroot datasets/rgb2ir/RoadScene/testA --name rgb2ir_paired_Road_edge_pretrained --model test --no_dropout --preprocess none
    
    ## training
       cd ./CPSTN
       python train.py --dataroot ./datasets/rgb2ir/RoadScene --name rgb2ir_paired_Road_edge --model cycle_gan --dataset_mode unaligned
   
  The training and testing data of our CPSTN can be downloaded from: [datasets](https://pan.baidu.com/s/1-U1n945ykHFU7yrEHwGC9Q) (code: u386)
  
  Please download the [pretrained model](https://pan.baidu.com/s/1JO4hjdaXPUScCI6oFtPEnQ) (code: i9ju) of CPSTN and put it into folder './CPSTN/checkpoints/pretrained/'
