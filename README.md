# Deep Learning for Sign Language Detection and Caption Translation  

### Authors  
**Saqib Chowdhury,Hamsalakshmi Ramachandran, Sugandha Chauhan, Himani Shah, Manjot Singh,  Kush Bindal**  
_Department of Applied Data Science, San José State University_  

---

##  Overview  
This project presents an **end-to-end deep learning framework** for **American Sign Language (ASL) recognition and caption translation**.  
It integrates **computer vision** and **natural language processing (NLP)** techniques to perform:  
1. **Hand segmentation** from video frames  
2. **Gloss-level gesture classification**  
3. **Multilingual translation** (English → Hindi)  

The pipeline leverages **EgoHands** and **WLASL** datasets, multiple segmentation models, and **ResNet-18** for classification, coupled with **Helsinki-NLP MarianMT** for translation.  

---

##  Objectives  
- Develop a modular pipeline for **ASL hand detection, gesture recognition, and translation**  
- Compare the performance of **six segmentation architectures**  
- Enable **multilingual translation** for improved accessibility and inclusivity  

---

##  System Architecture  

**Pipeline Stages:**  
1. **Data Preprocessing** — Extract frames and polygonal hand masks from EgoHands dataset.  
2. **Segmentation Models** — Train and compare six segmentation networks:  
   - U-Net  
   - ENet  
   - HRNet  
   - Mask R-CNN  
   - DeepLabV3  
   - YOLOv8m-Seg  
3. **Gesture Classification** — Train **ResNet-18** on cropped hand regions for 50 ASL glosses.  
4. **Translation** — Convert recognized glosses to **Hindi** using **Helsinki-NLP MarianMT (opus-mt-en-hi)**.  

---

##  Datasets  

### 1. EgoHands Dataset  
- 48 annotated egocentric videos (720×1280 resolution)  
- 4,800 labeled frames with pixel-level hand masks  
- Used for **hand segmentation training**  

### 2. WLASL (Word-Level ASL) Dataset  
- 12,000 video clips, covering 2,000 ASL glosses  
- Each clip: 1–3 seconds, varied lighting, backgrounds, and signers  
- Used for **gesture classification and translation**  

---

##  Methodology  

| Stage | Description | Tools / Models |
|:------|:-------------|:----------------|
| **Segmentation** | Extracts hand regions from frames using CNNs | U-Net, ENet, HRNet, Mask R-CNN, DeepLabV3, YOLOv8m-Seg |
| **Classification** | Identifies the ASL gloss from segmented hand regions | ResNet-18 |
| **Translation** | Converts English glosses to Hindi | MarianMT (Helsinki-NLP/opus-mt-en-hi) |
| **Evaluation** | Measures segmentation, classification & translation accuracy | F1, mAP@50, BLEU Score |

---

## Results Summary  

| Model | Accuracy | Precision | Recall | F1-Score |
|:------|:----------|:-----------|:--------|:----------|
| **U-Net** | 0.63 | 0.81 | 0.64 | 0.69 |
| **YOLOv8m-Seg** | 0.89 | 0.92 | 0.89 | 0.88 |
| **Mask R-CNN** | 0.53 | 0.89 | 0.38 | 0.54 |
| **HRNet** | 0.86 | 0.49 | 0.40 | 0.44 |
| **ENet** | 0.94 | 0.96 | 0.94 | 0.94 |
| **DeepLabV3** | 0.96 | 0.90 | 0.91 | 0.90 |

**Translation BLEU-1 Score:** ~0.62  
**Top Performing Models:** DeepLabV3 and ENet  

---

## Key Insights  
- **E-Net** achieved the best tradeoff between **speed and accuracy**, ideal for real-time applications.  
- **DeepLabV3** provided the most **precise segmentation masks** for downstream recognition.  
- The **MarianMT** translator effectively converted predicted glosses to Hindi with >60% BLEU accuracy.  
- Visual explanations (via **Grad-CAM**) confirmed model interpretability and focused attention on hand regions.  

---

## Tech Stack  
- **Language:** Python  
- **Frameworks:** PyTorch, OpenCV, Hugging Face Transformers  
- **Datasets:** EgoHands, WLASL  
- **Visualization:** Grad-CAM++, Matplotlib  
- **Environment:** Kaggle (P100 GPU), Google Colab (A100 GPU)  

---

## Conclusion  
Our framework achieves **high segmentation accuracy and strong gloss recognition** across six architectures.  
It demonstrates a **scalable, modular, and multilingual system** for continuous ASL interpretation — bridging accessibility gaps between Deaf and hearing communities.  

---

## Citation  
If you use this repository, please cite:  
> Chowdhury, S., Ramachandran, H., Chauhan, S., Shah, H., Singh, M., & Bindal, K.  
> *Deep Learning for Sign Language Detection and Caption Translation*,  
> San José State University, Department of Applied Data Science, 2025.  
