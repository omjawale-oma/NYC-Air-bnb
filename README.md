# NYC Airbnb Room Type Prediction

A machine learning project that predicts the room type of a New York
City Airbnb listing from listing and host-related features. The project
demonstrates a complete workflow from model training to serving
predictions through a FastAPI backend and a simple web interface.

## Project Live 
https://nyc-air-bnb-2.onrender.com

## Project Overview

Airbnb listings can differ by room type, host activity, and review
history. This project uses a trained machine learning pipeline to
predict the room type from user-provided listing details.

The web interface includes fields such as:

-   Total reviews
-   Reviews per month
-   Listings by this host

The entered values are sent to a FastAPI prediction endpoint, which
loads the saved model pipeline and returns a prediction.

## Features

-   Predicts an Airbnb listing's room type using a trained ML pipeline.
-   Serves predictions through a FastAPI REST API.
-   Provides interactive API documentation through Swagger UI.
-   Includes a frontend form for entering listing information.
-   Uses a serialized model file (`Model_Pipeline.pkl`) for inference.

## Tech Stack

-   **Python** --- data processing and model development
-   **Pandas / NumPy** --- data manipulation (if used in the training
    notebook)
-   **Scikit-learn** --- machine learning pipeline (if used to train the
    saved model)
-   **Joblib** --- loading the saved model pipeline
-   **FastAPI** --- prediction API
-   **Uvicorn** --- ASGI server
-   **HTML, CSS, JavaScript** --- frontend (if applicable to your
    interface)
-   **Jupyter Notebook** --- experimentation and model development

## Project Structure

Your actual filenames may differ; a typical layout is:

``` text
project/
├── main.py                 # FastAPI application
├── Model_Pipeline.pkl      # Trained model pipeline
├── templates/              # HTML templates, if used
├── static/                 # CSS, JavaScript, images, if used
├── notebooks/              # Jupyter notebooks, if used
├── data/                   # Dataset, if included
└── README.md
```

Keep `main.py` and `Model_Pipeline.pkl` in the same directory if the
code loads the model with a relative path such as:

``` python
model = joblib.load("Model_Pipeline.pkl")
```

If the model file is stored elsewhere, update the path in `main.py`.

## Setup and Installation

### 1. Clone or download the project

If this project is hosted in a Git repository:

``` bash
git clone <your-repository-url>
cd <your-project-folder>
```

Or open the folder where you saved the project.

### 2. Create and activate a virtual environment (recommended)

On Windows:

``` cmd
python -m venv .venv
.venv\Scripts\activate
```

### 3. Install dependencies

``` cmd
python -m pip install fastapi uvicorn joblib scikit-learn pandas numpy
```

Install any additional packages imported by your own `main.py` or
training notebook. If the frontend uses a separate framework, install
its dependencies too.

## Run the FastAPI Application

Open Command Prompt in the folder containing `main.py` and
`Model_Pipeline.pkl`, then run:

``` cmd
python -m uvicorn main:app --reload
```

-   `main` refers to `main.py`.
-   `app` refers to the FastAPI instance created in that file.
-   `--reload` restarts the development server when the code changes.

Keep the terminal window open while using the application.

## Open the Application

-   **API base URL:** http://127.0.0.1:8000
-   **Interactive API documentation:** http://127.0.0.1:8000/docs

The root URL may not display a page unless a root route is defined. Use
`/docs` to inspect and test the endpoints exposed by the API.

## Using the Prediction Interface

1.  Start the FastAPI server.
2.  Open the frontend in your browser.
3.  Enter the listing and host details requested by the form.
4.  Select **Predict room type**.
5.  Review the prediction returned by the API.

The frontend's API URL must point to the running backend. If the
frontend is served from a different origin, configure CORS in FastAPI
for the frontend's actual origin.

## Model File

The application expects a trained model pipeline saved as:

``` text
Model_Pipeline.pkl
```

This file is not created automatically when the API starts. Train and
export the model first, or obtain the matching model file from the
project files. The model must be compatible with the features and
preprocessing expected by `main.py`.

## Troubleshooting

### `ModuleNotFoundError: No module named 'fastapi'`

Install the packages in the Python environment used to run Uvicorn:

``` cmd
python -m pip install fastapi uvicorn
```

### `Could not import module "main"`

Confirm that `main.py` exists in the current directory and that it
contains an instance named `app`, for example:

``` python
from fastapi import FastAPI

app = FastAPI()
```

Run Uvicorn from the directory containing `main.py`, or specify the
correct application directory.

### `FileNotFoundError: Model_Pipeline.pkl`

Ensure `Model_Pipeline.pkl` exists at the path used by `joblib.load()`.
If using a relative path, run the command from the correct project
directory or change the code to use the model's full path.

### Frontend says it cannot reach the prediction API

1.  Keep the Uvicorn server running.
2.  Check that `http://127.0.0.1:8000/docs` opens.
3.  Confirm that the frontend calls the correct endpoint and HTTP
    method.
4.  Check that the request JSON matches the input schema expected by the
    API.
5.  If the frontend runs on another origin, configure CORS
    appropriately.

### Windows Command Prompt commands

Use `dir` to list files and `cls` to clear the screen. Commands
beginning with `!`, such as `!python ...`, are intended for notebook
cells, not ordinary Command Prompt.

## Notes

-   This README describes the project based on the available project
    context. Update the structure, endpoint path, feature list, metrics,
    and dependencies to match your final implementation.
-   Do not commit private data or large datasets unless you have
    permission to share them.
-   Only load trusted `.pkl` files because pickle-based files can
    execute code when deserialized.

## Reference

Project inspiration/tutorial: [ML Project: Classifying NYC House Types
from Scratch](https://youtu.be/oOyCUmZC5NY)

## Author

Add your name, contact details, and repository link here.
