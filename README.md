# deep-learning-project
Project for CMU's Deep Learning Class

Architecture: YOLOv8s (Jocher et al., 2023)  
Dataset: `grantmwilkinson/IDID_Dataset` via Hugging Face
String model checkpoint	`csloya/yolov8-idid-string`
Shell model checkpoint	`csloya/yolov8-idid-shell`
Processed dataset	`csloya/yolov8-idid-dataset`


# Insulator Defect Identification from Aerial Imagery

This project addresses the detection and classification of insulator defects in aerial power line imagery. Using deep learning, we automate the identification of insulator strings and the classification of individual shell health to streamline infrastructure maintenance.

---

## Dataset: IDID
The **Insulator Defect Image Dataset (IDID)** contains high-resolution labeled images of transmission line insulators. The data is used to identify:
* **Insulator Strings:** The overall parent structure.
* **Insulator Shells:** Classified into three distinct states:
    * **Good:** Healthy shells.
    * **Broken:** Shells with mechanical damage.
    * **Flashover:** Shells with electrical discharge damage.

The dataset is partitioned into training, validation, and testing sets at a 70:15:15 ratio.

---

## Jupyter Notebooks
Each notebook in this repository is dedicated to training and evaluating a specific model variant:

1. **`YOLOv1_Colab.ipynb`**
   * **Model:** YOLOv1 (CNN-based baseline).
   * **Role:** Establishes a performance floor. It treats detection as a single regression problem but faces challenges with small objects and specific aspect ratios.

2. **`YOLOv8_Colab.ipynb`**
   * **Model:** YOLOv8 (Modern CNN variant).
   * **Role:** Features advanced backbone (CSPDarknet) and neck (PANet) architectures. It provided the highest accuracy for both string and shell detection.

Setup — HuggingFace Token
Go to https://huggingface.co/settings/tokens
Create a new read token
In Colab, open Secrets 
Add a secret named with your token value
Update Block 0 of the notebook to use your secret name:
login(token=userdata.get("HF_TOKEN"))

Running the YOLOv8 Notebook — First Time
Run blocks in this order:
Block
0	Environment Setup	
1	Global Configuration	
2	Load Dataset	
3	Extract Annotations & EDA	
4	Session Recovery	Downloads models and dataset automatically
5	Shared Training Utilities	
Then skip directly to any evaluation block (A6, A7, B6, B7)

Blocks to Skip (Graders)
The following blocks require write access to `csloya/` and should be skipped:
A1	Dataset Writer	
A1.2	Upload Dataset 
A4 upload section	
B4 upload section	

3. **`DINO_DETR_Colab.ipynb`**
   * **Model:** DINO-DETR (Transformer-based).
   * **Role:** Utilizes a DINOv3 backbone with a transformer-based detection head. It leverages global self-attention for detection.

---

## Authors
* **Sofia Loya** – Carnegie Mellon University, Department of Mechanical Engineering
* **Grant Wilkinson** – Carnegie Mellon University, Department of Mechanical Engineering
