# ⚽ Football Oracle AI – Player Valuation & Scouting System

Football Oracle AI is a machine learning–driven application designed to predict football player market values and support scouting analysis.  
The system uses structured player attributes (age, overall rating, potential, position, league context) to estimate market valuation and includes an interactive Gradio UI for real-time player analysis.

---

## 📌 Project Overview

This project builds a complete end-to-end valuation pipeline:

✔ Preprocess the `footballData.csv` dataset from Kaggle  
✔ Train a neural network to predict log-transformed player value  
✔ Deploy an interactive Gradio web app  
✔ Provide AI-powered scouting feedback using OpenAI  
✔ Allow manual custom player valuation  
✔ Display similar players and profile-based analysis  

This repository contains the notebook (`.ipynb`) used to train the model and run the Gradio interface.

---

## Dataset

The project uses **footballData.csv**, sourced from Kaggle.

**Kaggle Dataset:**  
footballData.csv – Football Player Dataset  
https://www.kaggle.com/

### Key attributes used:

- Age, Height, Weight  
- Nationality, Club, League  
- Overall rating & Potential  
- Preferred foot  
- Key skill metrics (pace, passing, shooting, etc.)  
- Market value (target variable)

---

## Model Architecture

A compact neural network built with TensorFlow/Keras:

| Layer               | Output Shape | Params |
|---------------------|-------------|--------|
| Input (13 features) | (None, 13)  | 0      |
| Dense (128, ReLU)   | (None, 128) | 1,792  |
| Dense (64, ReLU)    | (None, 64)  | 8,256  |
| Dense (32, ReLU)    | (None, 32)  | 2,080  |
| **Total Params**    | —           | **12,128** |

The model predicts player market value in **log-space** to stabilize training and reduce the effect of outliers.

---

## Features

### 🔹 1. Player Oracle  
Enter a player’s name and instantly:

- Predict market value  
- Ask tactical or scouting questions  
- View similar players  
- Get AI-generated analysis  

### 🔹 2. Manual Scout Valuation  
Create your own hypothetical player:

- Age, Position, Preferred Foot  
- Overall Rating & Potential  
- League Level  
- Contract Length  

Perfect for evaluating youth prospects or custom players.

### 🔹 3. Real-Time Gradio Interface  

| Player Oracle UI                       | Manual Valuation UI                          |
|----------------------------------------|----------------------------------------------|
| ![oracle](images/player_oracle_ui.png) | ![manual](images/manual_scout_ui.png)        |

---

## OpenAI API Key Setup (Required)

The Gradio app uses OpenAI for enhanced scouting analysis.  
After installing dependencies, the notebook will ask for an API key.

Inside the notebook, you will find:

```python
import os
os.environ["OPENAI_API_KEY"] = " here"

client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))
