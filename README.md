# 🌿 Plant Health Checker

A simple deep learning project that checks whether a **tea leaf** is **healthy or diseased** from a photo.

Upload a leaf image and the model shows **Healthy** or **Not healthy** with a confidence score.

## How it works

- **Task:** binary image classification (healthy vs diseased)
- **Model:** MobileNetV2 (pretrained on ImageNet) with transfer learning
- **Data:** Tea Leaf Disease dataset from Kaggle (6 classes: healthy, algal_spot, brown_blight, gray_blight, helopeltis, red_spot)
  - All 5 disease classes are merged into one `diseased` class
  - Classes are balanced: 1,000 healthy and 1,000 diseased images
  - 80% training, 20% validation
- **Frameworks:** TensorFlow / Keras, Streamlit (web app), Gradio (Colab demo)

## Results

- Validation accuracy: **XX%**  <!-- replace XX with your number -->
- Tested on real photos outside the dataset: <!-- add a short note -->

## Run it in Google Colab (easiest)

1. Download the dataset from Kaggle: https://www.kaggle.com/datasets/saikatdatta1994/tea-leaf-disease
2. Open `plant_health_colab.ipynb` in [Google Colab](https://colab.research.google.com) and choose a T4 GPU runtime.
3. Run the cells from top to bottom. Upload the dataset zip when asked.

## Run it on your computer

```bash
pip install -r requirements.txt

# 1. Unzip the Kaggle dataset so you have a Tea_Leaf_Disease folder, then:
python prepare_data.py

# 2. Train the model (creates plant_model.keras and accuracy.png)
python train.py

# 3. Start the web app
streamlit run app.py
```

## Project files

| File | Purpose |
|------|---------|
| `plant_health_colab.ipynb` | Complete notebook: prepare data, train, test |
| `prepare_data.py` | Builds the `healthy` / `diseased` folders |
| `train.py` | Trains the model and saves `plant_model.keras` |
| `app.py` | Streamlit web app for uploading a leaf image |
| `requirements.txt` | Python libraries needed |

## Limitations

- The model is trained on **tea leaves only**, so it will not work reliably on other plants.
- Training images are close-up photos; images with a plain white background (for example cut-out images from the web) can give lower confidence.
- It only says healthy or not healthy. It does not name the specific disease.

## Possible improvements

- Multi-class classification to name the exact disease
- Train on more plant species (for example PlantVillage)
- Fine-tune the base model for higher accuracy

## Dataset credit

Tea Leaf Disease dataset by saikatdatta1994 on Kaggle. Please follow the dataset's license and terms.
