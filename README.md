# 🛡️ Backdoor Attack on Image Classification (Cats vs. Dogs)

## Author
**ALOUACH Abdennour** - Creator and lead developer of the project

## Introduction
This AI Security project demonstrates and compares the effectiveness of two types of **Backdoor** attacks on a standard image classification model: **ResNet-18**.

The goal is to insert malicious behavior (targeted misclassification) into the model while preserving its performance on its main task (Cat vs. Dog classification).

The project focuses on comparing a **visible** *trigger* (easily detectable) with an **invisible/steganographic** *trigger* (stealthy).

## Key Objectives
1.  **Attack Demonstration:** Create a poisoned dataset and train a vulnerable model.
2.  **Trigger Comparison:** Evaluate the impact on attack effectiveness (ASR) and main performance (CA) for:
    *   **Visible Trigger:** A red square (30x30 pixels).
    *   **Invisible Trigger:** A low-opacity steganographic patch.
3.  **Robust Evaluation:** Use **Early Stopping** to maintain high *Clean Accuracy* (CA) and measure the **Attack Success Rate** (ASR).

## Technical Methodology

| Component | Details |
| :--- | :--- |
| **Dataset** | Microsoft Cats-vs-Dogs (Sanitized and Split: Train/Val). |
| **Model** | ResNet-18 (pre-trained or trained from scratch). |
| **Poisoning Rate** | **7%** of training images are poisoned and mislabeled. |
| **Attack Target** | Classify all triggered images as **Dog**. |
| **Metrics** | **Clean Accuracy (CA)** and **Attack Success Rate (ASR)**. |

## Project Structure
The project is primarily contained within the Jupyter *notebook* `backdoor-attack-on-classification.ipynb`.

| Cell | Description |
| :--- | :--- |
| 7 | Definition of trigger functions (`add_visible_trigger`, `add_invisible_trigger`). |
| 8 | `Custom BackdoorDataset` class and *Transforms* definitions. |
| 8.1 & 8.2 | Definition of specific *DataLoaders* for training (visible and invisible). |
| 10 | Training loop with management of the *DataLoader* **switching** for both trigger types. |
| 12 | Final evaluation to calculate and display the **CA** and **ASR**, including training history plots. |
| 13 | Visualization of clean, visible, and invisible samples with model predictions. |

## Execution Instructions

To run this analysis, please follow the steps below in a Jupyter or Kaggle environment:

1.  **Clone the repository**:
    ```bash
    git clone [YOUR_GITHUB_LINK]
    cd [REPOSITORY_NAME]
    ```
2.  **Install dependencies**: The code requires `torch`, `torchvision`, `Pillow`, `tqdm`, and `matplotlib`.
    ```bash
    pip install torch torchvision pillow tqdm matplotlib
    ```
3.  **Launch the Notebook**: Open `backdoor-attack-on-classification.ipynb`.
4.  **Step-by-Step Execution**:
    *   Run cells 1 through 11.
    *   **For the Visible Trigger**: Ensure you use `train_loader` in Cell 12.
    *   **For the Invisible Trigger**: Reset the model (Cell 10) and use `train_loader_inv` in Cell 12.
5.  **Model Download**: The final and best-performing model (`backdoor_resnet18.pth`) will be saved in the working directory.

## Expected Results
The final evaluation should show that:
* The **Clean Accuracy (CA)** remains high for both attacks (typically > 90%).
* The **Attack Success Rate (ASR)** is significant, demonstrating the model's vulnerability.
* The comparison of the two ASRs will reveal which *trigger* is most effective in this setup.

---

## Dependencies
* Python 3.x
* PyTorch
* Torchvision
* Pillow
* Tqdm
* Matplotlib
