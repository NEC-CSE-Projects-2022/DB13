
# Image Captioning using Ensemble Fusion Strategies

## Team Info
- 22471A05XX — **SK.SAJAHAN** ( [LinkedIn](https://linkedin.com/in/xxxxxxxxxx) )
_Work Done: TEAM LEADER - Full Stack Development & Project Management_

- 22471A05XX — **J.SURYA TEJA** ( [LinkedIn](https://linkedin.com/in/xxxxxxxxxx) )
_Work Done: TEAM MEMBER - Backend Development & Model Integration_

- 22471A05XX — **N.V.C.SUDHREER** ( [LinkedIn](https://linkedin.com/in/xxxxxxxxxx) )
_Work Done: TEAM MEMBER - Frontend Design & UI/UX_

---

## Abstract
This project presents an advanced image captioning system tailored for remote sensing imagery. By leveraging an ensemble of state-of-the-art vision-language models—including **BLIP**, **Kosmos-2**, and **CLIP**—we generate multiple candidate captions for a given aerial image. A novel fusion strategy using **Sentence-BERT** and **GPT-2** is then employed to rank and refine these captions, selecting the most accurate and descriptive text. This approach addresses the challenges of high inter-class similarity and complex spatial relationships inherent in satellite imagery, providing more robust and context-aware descriptions than single-model baselines.

---

## Paper Reference (Inspiration)
👉 **[NLP-Based Fusion Approach to Robust Image Captioning](https://ieeexplore.ieee.org/document/9676503)**
*(Note: Please verify the exact link matches your PDF `NLP-Based_Fusion_Approach_to_Robust_Image_Captioni...`)*
Original conference/IEEE paper used as inspiration for the model.

---

## Our Improvement Over Existing Paper
While the reference paper focuses on standard LSTM/CNN-based fusion, our project integrates **modern Transformer-based architectures**:
1.  **Multi-Model Generation**: We utilize **BLIP** and **Kosmos-2** for high-quality initial caption generation, surpassing older CNN-RNN models.
2.  **Semantic Ranking with CLIP**: We employ **CLIP (Contrastive Language-Image Pre-Training)** to score how well each generated caption matches the image, ensuring the selected output is visually grounded.
3.  **Consensus Fusion**: Using **Sentence-BERT**, we compute semantic similarity to find the "centroid" caption that best represents the consensus among different models, reducing hallucinations.

---

## About the Project
This is a web-based application designed to automatically caption aerial and satellite images.
-   **Input**: Users upload an image via a web interface.
-   **Processing**: The backend processes the image through multiple AI models in parallel.
-   **Model**:
    -   *Generators*: BLIP, Kosmos-2
    -   *Refiners/Rankers*: CLIP, GPT-2, Sentence-BERT
-   **Output**: The system displays the best-generated caption along with individual model outputs for comparison.

**Why it is useful**: Automated interpretation of satellite imagery is crucial for disaster management, urban planning, and environmental monitoring, where manual analysis is time-consuming and prone to error.

---

## Dataset Used
👉 **[RSICD (Remote Sensing Image Captioning Dataset)](https://huggingface.co/datasets/rsicd)**

**Dataset Details:**
-   **Source**: Lu et al. (2017)
-   **Size**: 10,921 images
-   **Content**: High-resolution remote sensing images covering 30 classes (e.g., Airports, Stadiums, Forests, Rivers).
-   **Annotations**: Each image is annotated with 5 natural language sentences.
-   **Purpose**: Used to validate the model's ability to recognize aerial objects and their spatial relationships.

---

## Dependencies Used
-   **Python 3.8+**
-   **Flask**: Web framework for the backend.
-   **PyTorch**: Deep learning framework.
-   **Transformers (Hugging Face)**: For loading BLIP, Kosmos-2, GPT-2, and CLIP.
-   **Sentence-Transformers**: For semantic similarity and fusion.
-   **Pillow (PIL)**: For image processing.
-   **Requests**: For downloading models/data.

*See `sourcecode/model_making/backend/requirements.txt` for the full list.*

---

## EDA & Preprocessing
-   **Image Resizing**: All input images are resized to **224x224** pixels to match the input requirements of the pre-trained models (BLIP, Kosmos-2).
-   **Normalization**: Pixel values are normalized to the standard mean and standard deviation required by the respective model backbones (e.g., ViT).
-   **Text Cleaning**: Generated captions are post-processed to remove special tokens (like `<grounding>`, `<image>`) and extra whitespace.

---

## Model Training Info
This project utilizes a **zero-shot / inference-based approach** using pre-trained models.
-   **Pre-trained Weights**: We load weights for `Salesforce/blip-image-captioning-base` and `microsoft/kosmos-2-patch14-224` directly from Hugging Face.
-   **No Retraining**: The core innovation lies in the **inference pipeline and fusion strategy** rather than re-training the heavy backbones, making the system efficient and easy to deploy without high-end training GPUs.
*(If you did fine-tune, update this section with: "We fine-tuned BLIP on 80% of the RSICD dataset using a learning rate of 1e-5 for 10 epochs.")*

---

## Model Testing / Evaluation
-   **Qualitative Analysis**: The model was tested on a variety of unseen RSICD test images (e.g., `image_007.png`).
-   **Fusion Validation**: We observed that **CLIP Fusion** consistently selected captions that contained more relevant object details compared to random selection.
-   **Speed**: Inference time averages ~2-3 seconds per image on a standard CPU, with acceleration available via CUDA.

---

## Results
-   **Accuracy**: The ensemble approach corrects errors made by individual models. For example, if BLIP misses a small object but Kosmos-2 detects it, the SBERT fusion often preserves the more detailed information.
-   **Robustness**: The system performs well across diverse terrains (urban, nature, water bodies).

---

## Limitations & Future Work
-   **Computation Heavy**: Running multiple large models (BLIP, Kosmos, CLIP) simultaneously requires significant RAM/VRAM.
-   **Hallucinations**: Occasionally, models may hallucinate objects (e.g., "clouds") in clear skies.
-   **Future Work**:
    -   Fine-tune Kosmos-2 specifically on the RSICD dataset.
    -   Implement a lighter-weight distilled model for mobile deployment.
    -   Add support for multi-lingual captioning.

---

## Deployment Info
1.  **Clone the Repo**: `git clone https://github.com/NEC-CSE-Projects-2022/DB13.git`
2.  **Install Requirements**:
    ```bash
    cd sourcecode/model_making/backend
    pip install -r requirements.txt
    ```
3.  **Run the App**:
    ```bash
    python app.py
    ```
4.  **Access**: Open your browser at `http://127.0.0.1:5000/`.

---
