# HiCu-ICD
This repo contains code for our MLHC 2022 paper [HiCu: Leveraging Hierarchy for Curriculum Learning in Automated ICD Coding](https://arxiv.org/abs/2208.02301).

Setup
-----
Install the following packages to run the code in this repository:
* gensim==4.1.2
* nltk==3.5
* numpy==1.18.1
* pandas==1.0.0
* scikit_learn==1.1.1
* scipy==1.4.1
* torch==1.7.1
* tqdm==4.62.3
* transformers==4.5.1

```bash
pip install -r requirements.txt
```
The instructions and code documentation available on the GitHub are as below:
https://github.com/wren93/HiCu-ICD and https://github.com/foxlf823/Multi-Filter-Residual-Convolutional-Neural-Network

They are the prerequisite to setup the inputs to preprocess and train the model. Based on the Python version used, following updates were needed across the code:
1. Changing \textit{np.int} to \textit{np.Int32}
2. Changing \textit{np.ifloat} to \textit{np.Float32}

The latest version of the following packages are recommended - 
1. gensim, nltk, numpy
2. pandas, scikit\_learn
3. scipy, torch, tqdm
4. transformers

And finally the command line parameters below are updated based on CPU/RAM configurations:
1. data_path
2. n_epochs
3. gpu
4. workers

Data Preprocessing
-----
We use MIMIC-III for model training and evaluation. We use the same data preprocessing code as [MultiResCNN](https://github.com/foxlf823/Multi-Filter-Residual-Convolutional-Neural-Network). To set up the dataset, place the MIMIC-III files into `/data` as shown below:
```
data
|   D_ICD_DIAGNOSES.csv
|   D_ICD_PROCEDURES.csv
└───mimic3/
|   |   NOTEEVENTS.csv
|   |   DIAGNOSES_ICD.csv
|   |   PROCEDURES_ICD.csv
|   |   train_full_hadm_ids.csv
|   |   train_50_hadm_ids.csv
|   |   dev_full_hadm_ids.csv
|   |   dev_50_hadm_ids.csv
|   |   test_full_hadm_ids.csv
|   |   test_50_hadm_ids.csv
```
The `*_hadm_ids.csv` files can be found [here](https://github.com/jamesmullenbach/caml-mimic/tree/master/mimicdata/mimic3).

After setting up the files, run the following command to preprocess the data:
```sh
python preprocess_mimic3.py
```

Training
-----
1. See files under `/runs` for training configs for MultiResCNN and RAC models.
2. For LAAT (Bi-LSTM) models, switch to `LAAT` branch and use the training configs in the root folder.

Output
-----
This folder contains output results and metrics from code run.

Presentation
-----
1. PPT Slides, Video recording/link (uploaded to youtube) and PDF Report are present in this folder.

Notebook (Google Collab) Details:
-----
1. Link: https://colab.research.google.com/drive/1WNJNhhZGeIdsrnO9jeqHj9IWDTttGwqH?usp=sharing
2. Google sign-in id: uiuc.chicago@gmail.com, Password: Uiuc123#

Acknowledgement
-----
A large portion of the code in this repository is borrowed from original HiCu repository [https://github.com/wren93/HiCu-ICD] and also from [foxlf823/Multi-Filter-Residual-Convolutional-Neural-Network
](https://github.com/foxlf823/Multi-Filter-Residual-Convolutional-Neural-Network). Thanks to their great work.