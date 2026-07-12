# # Image Classification with Teachable Machine

This project trains an image recognition model to classify images into two classes — **Cat** and **Cow** — using Google's Teachable Machine, then loads the exported model in Python to make predictions on new images.

## Project Overview

1. Trained an image classification model using [Teachable Machine](https://teachablemachine.withgoogle.com/) with two classes: **Cat** and **Cow**
2. Exported the trained model in **TensorFlow → Keras** format
3. Wrote a Python script to load the model and predict the class of a given input image
4. Ran predictions in Google Colab and captured the output

## Files in this Repository

- `keras_model.h5` — The trained Keras model exported from Teachable Machine
- `labels.txt` — Class labels corresponding to the model's output
- `catorcow.py` — Python script used to load the model and run predictions
- `screenshot.png` — Screenshot of a successful prediction run

## How It Was Trained

1. Opened Teachable Machine's [Image Project](https://teachablemachine.withgoogle.com/train/image)
2. Created two classes: **Cat** and **Cow**
3. Uploaded sample images for each class
4. Clicked **Train Model** and evaluated results using the built-in preview
5. Exported the model via **Export Model → TensorFlow → Keras → Download my model**, which produced `keras_model.h5` and `labels.txt`

## How to Run the Prediction Script (Google Colab)

1. Open [Google Colab](https://colab.research.google.com) and create a new notebook
2. Upload `keras_model.h5`, `labels.txt`, and a test image using the file sidebar
3. Install the required library:
   ```python
   !pip install Pillow
   ```
4. Force Colab to use the legacy Keras engine (required for Teachable Machine models to load correctly):
   ```python
   !pip install tf_keras
   import os
   os.environ["TF_USE_LEGACY_KERAS"] = "1"
   ```
   Then restart the runtime (**Runtime → Restart session**) and re-run the cells above.
5. Paste the prediction code from `CatOrCow.py` into a new cell
6. Update the `IMAGE_PATH` variable to match your uploaded image's filename
7. Run the cell — the predicted class and confidence score will be printed below it

## Notes

- Input images are automatically resized to 224×224 pixels to match the model's expected input size, as required by Teachable Machine.
- The `TF_USE_LEGACY_KERAS` fix addresses a compatibility issue between Teachable Machine's older Keras export format and the newer Keras 3 engine used by default in current Colab environments.
