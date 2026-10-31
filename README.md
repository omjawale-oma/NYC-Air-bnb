# NYC Airbnb Room Type Prediction

A machine learning project that predicts the room type of a New York City Airbnb listing from listing and host features, served through a FastAPI backend and deployed on Render.

## Live demo
- App: https://nyc-air-bnb-2.onrender.com
- API docs (Swagger): https://nyc-air-bnb-2.onrender.com/docs

The free Render server sleeps when idle, so the first load can take up to a minute.

## Overview
The model takes listing details such as total reviews, reviews per month, and the number of listings by the host, and predicts the room type.

## Features
- Scikit-learn pipeline: imputation, scaling, one-hot encoding and a Random Forest classifier
- FastAPI REST endpoint with interactive Swagger docs
- Saved model (`Model_Pipeline.pkl`) loaded with Joblib
- Deployed to Render (Python 3.12)

## Results
- Test accuracy: **FILL IN** (from your notebook)
- Other metrics (precision, recall, F1): **FILL IN**

## Tech stack
Python, Pandas, NumPy, scikit-learn, Joblib, FastAPI, Uvicorn, Jupyter Notebook, Render

## Project structure
```text
NYC-Air-bnb/
├── main.py              # FastAPI application
├── Model_Pipeline.pkl   # Trained model pipeline
├── requirements.txt
├── *.ipynb              # Training notebook
└── README.md
```

## Run locally
```bash
pip install -r requirements.txt
python -m uvicorn main:app --reload
```
Open http://127.0.0.1:8000/docs to test the prediction endpoint.

## Deployment
Deployed as a Render web service with Python 3.12.8 and the start command:
```bash
uvicorn main:app --host 0.0.0.0 --port $PORT
```

## Credits
Based on the tutorial [ML Project: Classifying NYC House Types from Scratch](https://youtu.be/oOyCUmZC5NY). I trained the model, built the API, and deployed it myself.

## Author
**Om Jawale** - https://github.com/omjawale-oma
