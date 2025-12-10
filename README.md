# LVI-Detection

This repository contains code and models for detecting Lymphovascular Invasion (LVI) in breast cancer whole-slide images (WSIs) using deep learning. 

## 📌 Table of Contents

- [Overview](#overview)
- [Data](#data)
- [Framework](#framework)
- [Results](#results)
- [Acknowledgements](#acknowledgements)
- [Reference](#reference)

<a name="overview"></a>

## 🧠 Overview

Lymphovascular Invasion (LVI) is a critical pathological feature in breast cancer, strongly associated with tumor metastasis and poor prognosis. However, manual LVI identification is:

  - Time-consuming
  - Subject to inter-observer variability
  - Difficult in large whole-slide images

This project proposes an automated LVI detection framework based on deep learning, leveraging:

  - Swin Transformer (Swin-Small) for patch-level classification
  - GigaPath for scalable whole-slide inference

The models were trained and evaluated on 90 annotated H&E-stained breast cancer WSIs, achieving:

  - AUC: 97%
  - Sensitivity: 79%
  - False positives: ~8 per slide

These results demonstrate the potential of deep learning to improve accuracy, consistency, and efficiency in LVI assessment.

<a name="data"></a>

## 📂 Data

- Slides: H&E-stained breast cancer whole-slide images.
- Annotations: LVI foci annotated by two expert pathologists.
- Consensus: Disagreements resolved by a third pathologist.

⚠️ Due to privacy and data-sharing restrictions, the dataset is not publicly available.
Please contact the authors for access or use your own annotated WSIs following the same format.

<a name="method-framework"></a>

## 🧬  Framework

<p align="left">
  <img src="framework.png" alt="Framework">
  <br>
  <em>Figure 1: Overview of the Proposed Framework. (a) Training Phase: (I) LVI foci are annotated by two pathologists, with a third resolving disagreements. (II) Swin-Small uses extracted patches for fine-tuning. (III) GigaPath tessellates the WSI and extracts patch embeddings for binary classification. (b) Inference Phase: (1) Swin-Small predicts patch-wise probabilities using tessellation and sliding window, with postprocessing to identify LVI. (2) GigaPath computes patch probabilities in one step, followed by postprocessing to locate LVI.</em>
</p>


<a name="results"></a>

## 📊 Results

<p align="left">
  <img src="swin_8.png" alt="swin_8" width="400" style="margin-right: 20px;">
  <img src="giga_8.png" alt="giga_8" width="400">
  <br>
  <em>Figure 2: Left: A WSI with predictions from Swin-Small. Right: The same WSI with predictions from GigaPath. The predicted LVI locations are highlighted with red boxes, while the ground-truth LVI locations are marked with green boxes.</em>
</p>


<a name="acknowledgements"></a>

## 🙏 Acknowledgements
This project builds upon the following open-source resources:

  - GigaPath: https://github.com/prov-gigapath/prov-gigapath
  - timm (PyTorch Image Models): https://github.com/huggingface/pytorch-image-models

We thank the authors and maintainers for making their code and pre-trained weights publicly available. The original implementations were adapted to support LVI detection in breast cancer WSIs.

<a name="reference"></a>

## 📖 Reference

Please consider citing the following paper if you find our work useful for your project.

```
@article{keshvarikhojasteh2025lymphovascular,
  title     = {Lymphovascular Invasion Detection in Breast Cancer Using Deep Learning},
  author    = {Keshvarikhojasteh, Hassan and Stathonikos, Nikolas and Pham, Paul and van Diest, Paul J and Vreuls, Celien and Bertram, Christof A and Pluim, Josien PW and Veta, Mitko},
  journal   = {medRxiv},
  pages     = {2025--06},
  year      = {2025},
  publisher = {Cold Spring Harbor Laboratory Press}
```
