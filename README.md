# deep-learning-project
Project for CMU's Deep Learning Class

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

1. **`YOLOv1_Baseline.ipynb`**
   * **Model:** YOLOv1 (CNN-based baseline).
   * **Role:** Establishes a performance floor. It treats detection as a single regression problem but faces challenges with small objects and specific aspect ratios.

2. **`YOLOv8_Training.ipynb`**
   * **Model:** YOLOv8 (Modern CNN variant).
   * **Role:** Features advanced backbone (CSPDarknet) and neck (PANet) architectures. It provided the highest accuracy for both string and shell detection.

3. **`DINO_DETR_Training.ipynb`**
   * **Model:** DINO-DETR (Transformer-based).
   * **Role:** Utilizes a DINOv3 backbone with a transformer-based detection head. It leverages global self-attention for detection, performing well on larger structures.

---

## Performance Results
Models were evaluated using Mean Average Precision at an IoU threshold of 0.50 (mAP@50).

| Model | String Detection (mAP@50) | Shell Detection (mAP@50) |
| :--- | :--- | :--- |
| **YOLOv1** | 0.5869 | 0.0101 |
| **YOLOv8** | **0.9950** | **0.9276** |
| **DINO-DETR** | 0.8182 | 0.3063 |

---

## Authors
* **Sofia Loya** – Carnegie Mellon University, Department of Mechanical Engineering
* **Grant Wilkinson** – Carnegie Mellon University, Department of Mechanical Engineering
