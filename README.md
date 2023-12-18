# Diffused Convolutional Neural Network for Hyperspectral Image Super-Resolution [[arXiv]](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=10057005)
Pytorch implementation for "Diffused Convolutional Neural Network for Hyperspectral Image Super-Resolution".
<p align="center">
<img src="imgs/frame.png" alt="Dual Regression Scheme" width="90%" align=center />
</p>


## Dependencies
```
Python>=3.7, PyTorch>=1.11, numpy, scipy, math, random, skimage, argparse
```

## Quickstart (Model Testing)
| Model | Scale | #Params (M) | PSNR on CAVE (dB) |
| :---: | :---: | :---------: | :---------------: |
| DCNN |   2   |     12.41     |       41.702       |
|      |   4   |     13.88     |       35.660       |
|      |   8   |     15.36     |       31.857       |



## Training Method

We use CAVE dataset () to train DCNN.

```bash
python train.py --train_path $TRAIN_DIR$ --test_path $TEST_DIR$ \
--scale $SCALE$ --save_name $SAVE_MODEL_NAME$
```

- TRAIN_DIR: path to the training set
- TEST_DIR: path to the testing set
- SCALE: super resolution scale, such as 2, 4 and 8
- SAVE_MODEL_NAME: file name for saving the model


For example, you can use the following command to train the DCNN model for 2x SR.
```bash
python train.py --train_path ./CAVE/train --test_path ./CAVE/val
--scale 2 --save_name cave_x2_dcnn
```

## Testing Method
You can use the following script to obtain the testing results:

```bash
python test.py --scale $SCALE$ \
--model_name $TEST_MODEL_PATH$ \
--test_path $TEST_DATASET_PATH$ 
```

- SCALE: test the scale of the image
- TEST_MODEL_PATH: The path where the test model is storeds
- TEST_DATASET_PATH: The path where the test data set is stored



For example, you can use the following command to test our DCNN for 2x SR.

```bash
python test.py --scale 2\
--model_name Cave_model_2_epoch_200.pth \
--test_path ./CAVE/test
```


## Citation

If you use any part of this code in your research, please cite our paper:

```
@inproceedings{guo2020closed,
  title={Closed-loop Matters: Dual Regression Networks for Single Image Super-Resolution},
  author={Guo, Yong and Chen, Jian and Wang, Jingdong and Chen, Qi and Cao, Jiezhang and Deng, Zeshuai and Xu, Yanwu and Tan, Mingkui},
  booktitle={Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition},
  year={2020}
}
```
