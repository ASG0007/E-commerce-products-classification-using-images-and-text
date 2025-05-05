# E-commerce-products-classification-using-images-and-text

This project tackles a **multi-label classification** and **product retrieval** problem using **multi-modal deep learning**. Products often have both **textual descriptions** (like titles) and **images**. Using both allows the model to better understand the product context and improve classification and retrieval accuracy.

---

## Objective

To build a unified neural network model that:

- Accepts both **text** and **image** as input.
- Learns **semantic embeddings** for both modalities.
- Projects both inputs into a **shared embedding space**.
- Enables **product classification**, **cross-modal similarity**, and **retrieval**.

---

## Model Architecture Overview

The solution is based on a **dual-tower architecture**:

![HUSE overview](https://github.com/1sh1vam/E-commerce-products-classification-using-images-and-text/blob/master/HUSE.png)

### Image Tower

- Uses a **pre-trained VGG16** model.
- Extracts features from product images.
- Outputs are **L2-normalized**.

### Text Tower

- Uses **embedding + CNN layers** to process tokenized product titles.
- Outputs are also **L2-normalized**.

### Shared Semantic Embedding Space

- Both towers output embeddings into a **universal semantic space**.
- These embeddings are combined in a **fully connected fusion layer**.
- Used for classification and similarity computations.

---

## Implementation Steps

### PART 1: Creating Text and Image Embeddings

- **Images** are resized and processed through VGG16 to get feature embeddings.
- **Text** is tokenized and passed through an embedding and Conv1D model to generate text embeddings.

### PART 2: Final Embedding Construction

- Image and text embeddings are **L2-normalized**.
- Both are combined into a **shared space** using a dense fusion layer.

### PART 3: Training with Three Losses

- **Class-Level Similarity Loss**
- **Semantic Similarity Loss**
- **Cross-Modal Gap Loss**

These ensure embeddings are aligned meaningfully across modalities.

---

## Results

- **Test Accuracy**: 98.21%
- **Train Accuracy**: 98.69%

This high accuracy indicates the model successfully learns useful joint representations for classification and retrieval.

---

## Key Features

- Joint image-text understanding for robust product classification.
- Cross-modal product retrieval (e.g., image-to-text or text-to-image).
- Extendable to downstream tasks like recommendation and semantic search.

---
