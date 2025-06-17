# 📸 Image Captioning with VGG16 & Flickr8k

Generate natural language captions for images using deep learning — VGG16 for image feature extraction and an LSTM-based RNN for caption generation.

---

##  Dataset: Flickr8k

- **Flickr8k**: A dataset with **8,000 images**, each paired with **5 human-written captions**.
- 📥 Download from [Kaggle](https://www.kaggle.com/datasets/adityajn105/flickr8k)
- 📂 Place the following inside the `data/` directory:
  - `Flickr8k_Dataset/` — contains images
  - `Flickr8k_text/Flickr8k.token.txt` — contains captions

---

##  Model Overview

### 🔹 Encoder: VGG16
- Pretrained on ImageNet
- 16 layers: 13 convolutional + 3 fully connected
- **Uses 4096-d vector** from the `fc2` layer
- Final classification layer removed
- Acts as a **feature extractor** for images

### 🔹 Decoder: LSTM
- Embedding layer to learn word embeddings
- LSTM layer to model temporal dependencies
- Dense output layer with softmax activation
- Trained to predict the next word in a caption sequence

---

## ⚙️ Training Details

- **Loss Function**: Categorical Cross-Entropy
- **Optimizer**: Adam
- **Evaluation Metric**: BLEU Score (optional)
- **Input**: Image features + start sequence token
- **Output**: Caption generated word-by-word

---

## Components Used

### VGG16
- Developed by the Visual Geometry Group (Oxford)
- Known for its simple architecture and strong transfer learning performance
- Uses small 3x3 filters and ReLU activations
- Pretrained on the ImageNet dataset

###  Flickr8k Dataset
- Contains:
  - 8,000 real-world images from Flickr
  - 5 human-annotated captions per image
- Files:
  - Images: `Flickr8k_Dataset/`
  - Captions: `Flickr8k_text/Flickr8k.token.txt`
  - Splits: `Flickr8k_text/Flickr_8k.trainImages.txt`, `Flickr_8k.devImages.txt`, etc.
- Ideal for prototyping image captioning pipelines

---

## 🛠️ Steps to Run

1. **Preprocess Captions**
   - Lowercase
   - Remove punctuations
   - Tokenize and filter short/long sequences

2. **Extract Image Features**
   - Use VGG16
   - Save the fc2 layer output (4096-d)

3. **Prepare Training Data**
   - Map images to corresponding captions
   - Create input-output word sequences for LSTM

4. **Train the Model**
   - Feed image features + partial caption
   - Predict next word in the sequence

5. **Generate Captions**
   - Feed image and start token
   - Predict words until end token is generated

---

