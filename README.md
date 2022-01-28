# c125 - Alphabet Handwriting Recognition API

A Flask web API that predicts a handwritten alphabet letter from an uploaded image using a logistic-regression classifier trained on a 28x30 pixel dataset.

## Features
- `POST /predict-alphabet` accepts an uploaded image and returns a predicted letter.
- Letter image preprocessing (grayscale, resize, invert and scale).
- Classifier trained with scikit-learn Logistic Regression (multinomial / saga solver).

## Tech Stack
- Python
- Flask
- scikit-learn (LogisticRegression)
- pandas, numpy, Pillow, PIL.ImageOps

## Project Structure
```
API/
├── app.py          # Flask API routes
├── classifier.py   # training + prediction logic
└── images/         # sample handwriting images
image.npz           # pixel data
labels.csv          # class labels
```

## Installation
```
pip install flask scikit-learn pandas numpy pillow
```

## Usage
Pre-trained weights are produced when `classifier.py` runs (it trains on load). Start the API:

```
python app.py
```

Then POST an image file to `/predict` (field name `alphabet`), e.g.:

```
curl -F "alphabet=@digit7.png" http://localhost:5000/predict-alphabet
```