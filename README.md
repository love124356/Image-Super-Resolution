# Image-Super-Resolution

This repository gathers the code for nuclei-segmentation from the [in-class CodaLab competition](https://codalab.lisn.upsaclay.fr/competitions/622?secret_key=4e06d660-cd84-429c-971b-79d15f78d400).

We use [SwinIR](https://github.com/JingyunLiang/SwinIR), an image restoration toolbox (PyTorch) that provides training and testing codes for SwinIR, to train our model.

## Reproducing Submission
We need to do some pre-preparation for training and testing on our custom dataset.

To reproduce my submission without retrainig, do the following steps:
1. [Requirement](#Requirement)
2. [Repository Structure](#Repository-Structure)
3. [Inference](#Inference)

## Hardware

Ubuntu 18.04.5 LTS

Intel® Core™ i7-3770 CPU @ 3.40GHz × 8

GeForce GTX 1080/PCIe/SSE2


## Requirement
All requirements should be:

```env
$ virtualenv SwinIR --python=3.6
$ source ./SwinIR/bin/activate
$ cd Image-Super-Resolution
$ pip install -r requirements.txt
```

Official images can be downloaded from [CodaLab competition](https://codalab.lisn.upsaclay.fr/competitions/622?secret_key=4e06d660-cd84-429c-971b-79d15f78d400#participate-get_data)


## Repository Structure

The repository structure is:
```
Image-Super-Resolution(root)
  +-- data                   
  +-- models
  +-- utils
  +-- model_zoo                            # put model weight(.pth) here
  +-- options                              # training hyper-parameters setting
  |   +-- train_swinir_sr_classical.json  
  +-- testing_lr_images                    # testing data
  +-- training_hr_images                   # training data
  +-- inference.py
  +-- train.py
  +-- requirements.txt
```


## Training

To train the model, run this command:

```py
$ python train.py --opt options/train_swinir_sr_classical.json
```

Trained model will be saved in ```superresolution/swinir_sr_classical_patch48_x3/models```


## Inference

Please download [this model]() if you want to reproduce my submission file, put it in ```model_zoo/model_final.pth``` and run the following code.

To reproduce my submission file or test the model you trained, run:

```py
$ python inference.py
```

Prediction file will be saved in ```results/swinir_classical_sr_x3```

If you use different hardware, the inference result may be a little different.

## Results

Our model achieves PSNR 28.1442dB


## Reference
[1] [SwinIR](https://github.com/JingyunLiang/SwinIR)