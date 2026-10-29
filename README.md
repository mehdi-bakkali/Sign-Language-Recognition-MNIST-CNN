# Sign Language MNIST CNN

Train a convolutional neural network to classify the 24 static ASL letter
handshapes in Kaggle's Sign Language MNIST dataset. J and Z are absent because
they require motion.

## Setup

Create a Python 3.12 virtual environment, activate it, install the dependencies,
and download the Kaggle CSV files:

```bash
mkdir -p data
python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
kaggle datasets download -d datamunge/sign-language-mnist -p data --unzip
```

The Kaggle CLI must be installed and authenticated. You can also download the
dataset in a browser and put `sign_mnist_train.csv` and `sign_mnist_test.csv`
inside the project's `data/` folder. If you saved the CSVs elsewhere, pass
their paths using `--train-csv` and `--test-csv`.

## Train and evaluate

```bash
python train_sign_mnist.py
```

The script holds out 10% of the training CSV for validation, uses early
stopping, evaluates on the Kaggle test CSV, and saves the trained model plus
the original-label-to-letter mapping in `artifacts/`.

To change the paths or training settings:

```bash
python train_sign_mnist.py \
  --train-csv data/sign_mnist_train.csv \
  --test-csv data/sign_mnist_test.csv \
  --epochs 25 \
  --batch-size 128 \
  --output-dir artifacts
```
# Sign-Language-Recognition-MNIST-CNN
