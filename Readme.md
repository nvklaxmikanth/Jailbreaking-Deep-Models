# Jailbreaking-Deep-Models

## Overview

This repository implements adversarial attacks on a ResNet-34 model pre-trained on ImageNet, using a curated 1,000-image subset for evaluation. It includes multiple attack methods—**FGSM**, **PGD**, **Universal Adversarial Perturbation (UAP)**, and **Patch PGD**—and assesses the transferability of these adversarial examples to a DenseNet-121 model. The aim is to study model vulnerability and attack effectiveness under white-box and black-box conditions.

---

## Features

- **Adversarial Attacks:** FGSM, PGD, Universal Perturbation (UAP), and localized Patch attack.
- **Transferability Analysis:** Evaluate whether attacks generated on ResNet-34 fool DenseNet-121.
- **Reproducibility:** All adversarial examples and predictions are stored for reproducibility.
- **Visualization:** Perturbation and accuracy plots included for interpretability.
- **Lightweight Dataset:** Works with a 1,000-image ImageNet subset and preprocessed label mapping.

---

## Project Structure

- **DL_project_3.ipynb**  # Contains all attack implementations, evaluation logic, and result logging

## Installation

1. **Clone the repository:**

```bash
git clone https://github.com/nvklaxmikanth/Jailbreaking-Deep-Models.git
cd Jailbreaking-Deep-Models
```

---

## Usage

### 1. Adversarial Attacks & Evaluation

Run the Jupyter Notebook:

- **DL_project_3.ipynb**

**Key Attack Features:**
- Loads 1,000-image ImageNet subset with labels.
- Runs FGSM, PGD, UAP, and Patch attacks on ResNet-34.
- Evaluates clean and adversarial performance on both ResNet-34 and DenseNet-121.
- Saves adversarial examples and logs accuracy.

**Main Hyperparameters:**
| Parameter      | Value (default) |
|----------------|-----------------|
| FGSM ε         | 0.02            |
| PGD ε          | 0.02            |
| PGD Steps      | 10              |
| PGD α          | 0.005           |
| Patch Size     | 32×32           |
| Patch ε        | 0.5             |
| UAP ε          | 0.02            |

---

### Accuracy Comparison Before Transfer (Evaluated on ResNet-34)

| *Dataset*       | *Top-1 Accuracy* | *Top-5 Accuracy* |
|-----------------|------------------|------------------|
| *Clean Set*     | 0.7620           | 0.9420           |
| *FGSM*          | 0.2640           | 0.5060           |
| *PGD*           | 0.0040           | 0.0680           |
| *Patch Attack*  | 0.2400           | 0.4660           |

---

### Transferability Evaluation (Evaluated on DenseNet-121)

| *Dataset*       | *Top-1 Accuracy* | *Top-5 Accuracy* |
|-----------------|------------------|------------------|
| *Clean Set*     | 0.7480           | 0.9360           |
| *FGSM*          | 0.4240           | 0.6660           |
| *PGD*           | 0.3900           | 0.6340           |
| *Patch Attack*  | 0.4440           | 0.6640           |

---

## Dataset

- **Subset of ImageNet:** 1,000 images across 10 classes.
- **Input Format:** ImageFolder-compatible with label indices from `labels_list.json`.
- **Preprocessing:** Resized to 224×224, normalized to ImageNet standards.

---

## Reproducibility

- All random seeds are fixed.
- Results (accuracy, loss) are consistent across runs.
- Adversarial image folders are saved and reused for testing.

---

## References

- He et al., *Deep Residual Learning for Image Recognition*, CVPR 2016
- Goodfellow et al., *Explaining and Harnessing Adversarial Examples*, ICLR 2015
- Madry et al., *Towards Deep Learning Models Resistant to Adversarial Attacks*, ICLR 2018
- Moosavi-Dezfooli et al., *Universal Adversarial Perturbations*, CVPR 2017
- Brown et al., *Adversarial Patch*, arXiv:1712.09665

---

## Contributing

Contributions to expand the evaluation scope or add additional attack/defense methods are welcome. Please open an issue or submit a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Team

- **Venkat Kumar Laxmi Kanth Nemala** (vn2263@nyu.edu)
- **Sheetal Prasad** (sp7990@nyu.edu)
- **Vivek Reddy Devireddy** (vd2438@nyu.edu)

---

## Quick Start Table

| Script/Notebook       | Purpose                         | Input                  | Output                     |
|-----------------------|----------------------------------|------------------------|----------------------------|
| `dl-project3-tests-final.ipynb`  | Run all attacks & evaluations    | `TestDataSet/`         | Adversarial images, CSV logs |

---

**Note:** For methodology, analysis, and visualizations, refer to `miniproject3_spring25.pdf`.
