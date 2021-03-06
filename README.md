# IJCAI_2021_Continual_Crowd_Counting_Challenge

## Baseline

This repo helps the challengers to access dataset and baseline conveniently. The workshop/challenge website is located at:\
https://sites.google.com/view/sscl-workshop-ijcai-2021/

The baseline is inspired from the unofficial implementation of CVPR 2016 paper "Single Image Crowd Counting via Multi Column Convolutional Neural Network" at https://github.com/svishwa/crowdcount-mcnn. However, the repo is updated with latest pytorch version and unsupervised training part.

## Dataset Description

The dataset is designed to test continual semi-supervised learning for crowd counting in video frames. This benchmark consists of the union of three existing datasets (Mall, UCSD and FDST), augmented with the relevant ground truth in terms of density maps.

The dataset can be downloaded by running the bash file [download_data.sh](./download_data.sh) to automatically download the annotation files and video directory in the currect directory (data).
```
bash download_data.sh
```
OR 

Can be downloaded from the link below:\
https://drive.google.com/file/d/1N71uZvw9Z3wqHRucJKmvmOwDWNIfK_1y/view?usp=sharing


Update: Test fold is available here. \
https://drive.google.com/file/d/1ixqLIVJF17e6GvqdRDC4Jl9eRH8h_zFf/view?usp=sharing


The train and validation + test fold  (without groundtruth) are arranged as follows:\
- Every dataset folder (say fdst) consists of three sub folders (train, val,test).
- A subfolder (say train) may contain input and gt as subfolder.
- Validation and test folds does not have a gt folder.
                      
                      
## Running the baseline
\
The training can be started by running:\
```
python main.py --DATA_ROOT=data/fdst --SAVE_ROOT=Outputs --Dataset=fdst --MODE=all --MAX_EPOCHS=100 --VAL_EPOCHS=2 --learning_rate=0.00001

python main.py --DATA_ROOT=data/mall --SAVE_ROOT=Outputs --Dataset=mall --MODE=all --MAX_EPOCHS=100 --VAL_EPOCHS=2 --learning_rate=0.00001

python main.py --DATA_ROOT=data/ucsd --SAVE_ROOT=Outputs --Dataset=ucsd --MODE=all --MAX_EPOCHS=100 --VAL_EPOCHS=2 --learning_rate=0.00001

Evaluating the supevised models

python main.py --DATA_ROOT=data/fdst --SAVE_ROOT=Outputs --Dataset=ucsd --MODE= eval_val --MAX_EPOCHS=100 --VAL_EPOCHS=2 --learning_rate=0.00001



Arguments  

--DATA_ROOT       --> The directory to dataset
--SAVE_ROOT       --> The directory where you want to save the trained models
--Dataset         --> There are three datasets (fdst, mall, ucsd)
--MODE            --> Mode represent which specific section you want to run i.e., all, train, val, test and eval_val
--MAX_EPOCHS      --> Training epochs
--VAL_EPOCHS      --> Validation epochs
--learning_rate   --> Learning rate


```
## Baseline Results
The table shows average MAE of three sequences: 

| Supervised_val_fold  | Self_trained_val_fold | Supervised_test_fold | Self_trained_val+test_fold|
| ------------- | ------------- |------------- | ------------- |
| 6.8345  | 13.0331  | 9.3776  | 14.4845  | 


Please follow guidelines to submit your predictions for evaluations on the challenge website:\
https://sites.google.com/view/sscl-workshop-ijcai-2021/overview




