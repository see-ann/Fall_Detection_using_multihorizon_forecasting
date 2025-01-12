# General Description
This is original code for paper "[Fall Detection using Biometric Information Based on Multi-Horizon Forecasting](https://ieeexplore.ieee.org/document/9956568)"(ICPR'22)

A fall detection method with multi-horizon forecasting usring Temporal Fusion Transformers and other deep learning methods.

For other deep learning methods, 1D CNN, single LSTM, stacked LSTM were used.

All models were configured to forecast falls through the window size of data from the perspective of regression instead of classification.

For the last predicted value, the class of the predicted values was classified on the basis of the threshold value. 

To verify benchmark performance, we faithfully reproduced the 1D CNN and LSTM-basedmodels, although the model structures were modified to enable regression in both cases because they were tailored to the classification task.

1D CNN model architecture is based on the model structure proposed in 2020 by Kraft et al([paper](https://github.com/IKKIM00/Fall_Detection_using_multihorizon_forecasting/files/6866631/Deep.Learning.Based.Fall.Detection.Algorithms.for.Embedded.Systems.Smartwatches.and.IoT.Devices.Using.Accelerometers.pdf)).

Signle LSTM and stacked LSTM model is based on the model architecture proposed in 2019 by Luna et al ([paper](https://github.com/IKKIM00/Fall_Detection_using_multihorizon_forecasting/files/6866652/sensors-19-04885-v2.pdf)).

# Requirements
`python==3.7.3`

`tensorflow-gpu==2.5.3` or `tensorflow==2.5.3`

`sklearn==0.24.2`

## Multi-horizon forecasting result
![model_pred](https://user-images.githubusercontent.com/37397258/126738142-7fc1218d-eb55-4f88-9c24-4112b320354b.jpg)
Prediction results for the SmartFall, Notch, DLR and MobiAct datasets in order using:

(a)-(d) TFT method, (e)-(h) Single LSTM, (i)-(l) Stacked LSTM, (m)-(p) 1D CNN

# Download Dataset
For `SmartFall` and `Notch` dataset, I have uploaded zip files in `dataset/`. You can also download data through the link below.

### SmartFall and Notch dataset
dataset url - https://userweb.cs.txstate.edu/~hn12/data/SmartFallDataSet/

paper - https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6210545/


### DLR dataset
dataset url - https://www.dlr.de/kn/en/desktopdefault.aspx/tabid-12705/22182_read-50785/

### MobiAct dataset
dataset url - https://bmi.hmu.gr/the-mobifall-and-mobiact-datasets-2/


# How to use

## Data Preprocess

Please download all datasets through the URL or `zip` files provided in `dataset/`.

### SmartFall Dataset
1. Put dataset into directory named `dataset/SmartFall_Dataset/`.
2. For SmartFall dataset, preprocessing codes are included in `ipynb` files. 

### Notch Dataset
1. Put dataset into directory named `dataset/Notch_Dataset/`
2. For Notch dataset, preprocessing codes are included in `ipynb` files.

### DLR Dataset
1. Put dataset into directory named `dataset/ARS DLR Data Set/`.
2. Use `dataset/DLR_preprocess.ipynb` for preprocessing. Run all cells in the ipynb file. 
3. Save all preprocessed files in `dataset/dlr_preprocessed`. 

### MobiAct Dataset
1. Put dataset into directory named `dataset/MobiAct_Dataset_v2.0`.
2. Use `dataset/MobiAct_preprocess.ipynb` for preprocessing. Run all cells in the ipynb file.
3. Save all preprocessed files in `dataset/mobiact_preprocessed`.

## For DL Methods

> run `python dl_main.py <dataset_name> <model> <use_gpu>`

- `dataset_name`: choose between <mobiact, dlr, notch, smartfall>
- `model`: choose between <singleLSTM, stackedLSTM, CNN>
- `use_gpu`: if like to use GPU set to `yes` or set to `no`

-----
- You can find all previous ipynb files in `prev_jupyter_files/` .


## For TFT Method

### All files included are modified version of [original github repo](https://github.com/google-research/google-research/tree/master/tft) with all version error fixed(with tensorflow v2).

> run `python tft_main.py <dataset_name> <save_dir_name> <use_gpu> <restart_opt>`

- `dataset_name`: choose between <mobiact, dlr, notch, smartfall>
- `save_dir_name`: set save name
- `use_gpu`: if like to use GPU set to `yes` or set to `no`
- `restart_opt`: if like to restart set to `yes` or set to `no`

----
- You can find all previous ipynb files in `prev_jupyter_files/` .
- For the cases of personal biometric information removed, use files: `prev_jupyter_files/dlr_tft_wo_bioinfo.ipynb ` and `prev_jupyter_files/mobi_tft_no_bioinfo.ipynb`
