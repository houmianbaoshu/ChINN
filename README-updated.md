# Chromatin Interaction Neural Network (ChINN): 
## A machine learning-based method for predicting chromatin interactions from DNA sequences 

### This document provides a brief intro of running models in ChINN for training and testing. Before launching any job, make sure you have properly downloaded the ChINN code and you have prepared the dataset following DATASET.md with the correct format.

Chromatin Interaction Neural Network (ChINN) only uses DNA sequences of the interacting open chromatin regions. ChINN is able to predict CTCF-, RNA polymerase II- and HiC- associated chromatin interactions between open chromatin regions. 

ChINN was able to identify convergent CTCF motifs, AP-1 transcription family member motifs such as FOS, and other transcription factors such as MYC as being important in predicting chromatin interactions.

ChINN also shows good across-sample performances and captures various sequence features that are predictive of chromatin interactions. 

# Installation
Python >= 3.0; Numpy v1.20.2; PyTorch >= 3.6; theano v1.0.5; Lasagne v0.1; sklearn >= 1.13.3; tensorflow v2

### Get the source code:


```python
$ git clone https://github.com/mjflab/chinn/tree/nscc
$ cd pytext
```

### 1.Numpy:

Please follow Numpy official instructions to install from source:

https://numpy.org/install/

### 2.PyTorch:

Please follow PyTorch official instructions to install from source:


```python
pip install torch
```

### 3. theano


```python
pip install Theano
```

### 4.  Lasagne:


```python
pip install Lasagne
```

### 5. scikit-learn:

Please follow sklearn official instructions to install from source:

https://scikit-learn.org/stable/install.html

### 6. tensorflow:

Please follow tensorflow official instructions to install from source:

https://www.tensorflow.org/install

## Test environment

ChINN is tested on Linux 4.4.0-193-generic x86_64

# Dataset

### Download the demo dataset from "Dataset.zip"

### Training Dataset:
The models were trained on GM12878 CTCF, GM12878 RNA Pol II, HelaS3 CTCF, K562 RNA Pol II, and MCF-7 RNA Pol II datasets separately.
The models were also trained on GM12878, HeLaS3, HMEC, HUVEC, IMR90, K562, KBM7, and NHEK Hi-C data, respectively.

# Data generation and preprocessing

### Data preprocessing:


```python
$ sh process_pos.sh # pipeline for preprocessing
$ sh pipe.sh # add the negative samples 
```

# Data preparation

### Produce hdf5 files for training/validation/test:


```python
python seq_to_hdf5.py
python seq_to_hdf5_paired.py
python data_preparation.py
```

### Feature generation:

(generate anchor pairs based on chromatin interactions provided)


```python
python generate_pairs.py
python generate_pair_features.py
python generate_factor_output.py
```

# Training


```python
python train.py
```

# Testing


```python
python test.py
```

# Prediction


```python
python predict.py
```
