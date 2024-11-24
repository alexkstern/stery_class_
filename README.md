# Stereotype and Category Classification

## Overview

This project builds upon **HEART’s research** to classify stereotypes in textual data. The goal is to create lightweight, efficient models capable of categorizing text into stereotype themes while considering sustainability and inference time. 

## Key Features

1. **Stereotype Classification:**
   - Classifies text into specific stereotype categories (e.g., racial, gender-based stereotypes).
   - Uses a combination of TF-IDF, cosine similarity, and embedding techniques.

2. **Category Classification:**
   - Distinguishes between stereotype-related and unrelated text.
   - Enhances decision-making through a hierarchical model pipeline.

3. **Generative Model Exploration:**
   - Investigates the use of large-scale generative models (e.g., Llama LoRA fine-tuning) for stereotype detection.
   - Approach would entail coarse to fine modelling from high level theme/ stereotype_type tokens, to then the specific tokens in the sentence that leads to the classification descision (during training), with the final stereotype, anti-stereotype, or unrelated token.
   - This approach is computationally intensive and was not implemented due to its impracticality for real-time use.

## Methodology

### 1. Generative Model Approach (Not Implemented)
- **Concept**: Fine-tune a generative language model (e.g., Llama 3 8B) to generate stereotype reasoning and classification.
- **Challenges**: High computational cost, slower inference times, and limited practicality for real-world applications.

### 2. Implemented Approach
- **Model 1**: Stereotype Type Classification
  - **Features**:
    - TF-IDF vectorization of input text.
    - Embeddings: Calculate mean embeddings for each stereotype class and compute cosine similarity with input text embeddings.
  - **Classifier**: LightGBM model trained on feature vectors combining TF-IDF and cosine similarity.

- **Model 2**: Category Classification
  - **Features**:
    - Outputs from Model 1 (class probabilities).
    - TF-IDF vectorization and cosine similarity features.
  - **Classifier**: LightGBM model trained on combined feature vectors from Model 1 and additional text representations.


## Results

- **Model 1**: Stereotype Type Classification
  - F1 Score: **0.913**
  - Carbon Emissions: **3.7 × 10^-5**
- **Model 2**: Category Classification
  - F1 Score: **0.653**

### Business Value
- Moderation of malicious content on platforms like Discord or social media.
- Identification and mitigation of harmful stereotypes in online communication.

---

## Limitations and Future Directions

### Current Limitations:
- Only applicable to predefined stereotypes.
- Limited to short sentences; struggles with complex or long texts.

### Potential Improvements:
- Incorporating deep learning for more complex text processing.
- Enhancing fairness and addressing inherent biases in the model.


## Installation and Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/alexkstern/steryclass_priv.git

2. pip install -r requirements.txt




