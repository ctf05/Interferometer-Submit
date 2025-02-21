Interferometer-Submit

Overview

This repository contains code for training a model using interferometer data. The primary focus is on the FinalModel directory, which contains the final implementation for training the model. Other directories contain supporting scripts and preliminary versions but are only briefly covered in this guide.

Prerequisites

Before running the code, ensure you have the following installed:

Python 3.8+

venv or virtualenv for managing dependencies

Git

Required Python packages (specified in requirements.txt)

Setup Guide

1. Clone the Repository

git clone https://github.com/ctf05/Interferometer-Submit.git
cd Interferometer-Submit

2. Create a Virtual Environment

It is recommended to use a virtual environment to manage dependencies.

Using venv:

python -m venv venv
source venv/bin/activate  # On macOS/Linux
venv\Scripts\activate     # On Windows

Using virtualenv:

pip install virtualenv  # If not installed
virtualenv venv
source venv/bin/activate  # On macOS/Linux
venv\Scripts\activate     # On Windows

3. Install Dependencies

pip install -r requirements.txt

Running the Code

4. Generating Data

Before training, you need to generate the required data. Run the scripts in the FinalModel folder:

FinalModel/DataCreatorClassaholic.py

This will generate the necessary datasets for model training.

5. Training the Model (FinalModel)

The FinalModel directory contains the main training script. Run the following command to train the model:

python FinalModel/train.py

If the script requires any additional arguments, check its help message:

python FinalModel/train.py --help

6. Autoencoder Model and Transfer Learning

The model in FinalModel is based on an autoencoder architecture. An autoencoder is a type of neural network that learns efficient encodings of data in an unsupervised manner. It consists of an encoder that compresses the input data into a latent space representation and a decoder that reconstructs the original data from this compressed representation.

Autoencoder Training

The encoder learns to extract important features from interferometer data.

The decoder reconstructs the original signal from the compressed representation.

Training involves minimizing the reconstruction error, helping the model understand underlying patterns in the data.

Transfer Learning

Transfer learning is used to improve model performance by leveraging pre-trained features. The encoder from the trained autoencoder is fine-tuned and used as a feature extractor for downstream tasks, reducing the need for large amounts of labeled data.

To utilize transfer learning:

python FinalModel/transfer_learning.py

This script loads the pre-trained encoder, attaches a classifier or regression head, and fine-tunes it on a specific dataset.

7. Running Other Scripts

Other folders contain additional utility scripts that may be useful for preprocessing, testing, or visualization. Refer to individual script documentation for more details.

Additional Notes

Ensure that you have activated your virtual environment before running any scripts (source venv/bin/activate or venv\Scripts\activate).

If you encounter missing dependencies, install them using pip install -r requirements.txt.

Modify hyperparameters or configurations in FinalModel/config.py if needed before training.
