# Dataset Distillation for the Pre-Training Era: Cross-Model Generalization via Linear Gradient Matching

**[Metanthropic](https://metanthropic.vercel.app/)**, **[Ekjot Singh](https://www.linkedin.com/in/ekjot-singh-153110268/)**


[**[Metanthropic]**](https://metanthropic.vercel.app/) | [**[Project Page]**](https://metanthropic.github.io/TFGCJCSSLLMs-website/) | [**[Paper]**](https://metanthropic.vercel.app/papers/dataset-distillation.pdf) | [**[Code]**](https://github.com/metanthropics/DDPTECMGLGM)

---

## Abstract

The standard formulation of Dataset Distillation targets the synthesis of compact, synthetic datasets capable of training models from scratch. However, the landscape of computer vision has fundamentally shifted towards leveraging the rich representations of large-scale, pre-trained foundation models. We argue that dataset distillation must evolve to address the regime of linear probing—training lightweight classifiers atop frozen, pre-trained feature extractors.

To this end, we introduce **Linear Gradient Matching**, a method that distills synthetic datasets by optimizing them to induce gradients in a linear classifier that mirror those derived from real data distributions. We demonstrate that a single synthetic image per class is sufficient to train linear probes that not only achieve competitive performance across a diverse array of vision backbones (CLIP, DINO-v2, EVA-02, MoCo-v3) but consistently outperform baselines constructed from real images.

Motivated by the **Platonic Representation Hypothesis**, we further investigate the transferability of these distilled datasets. We introduce differentiable augmentations and a multi-scale pyramid parameterization that unlock robust cross-model generalization, enabling a dataset distilled via a DINO backbone to perform competitively on CLIP. Beyond efficiency, our experiments confirm that Linear Gradient Matching serves as a potent diagnostic tool for analyzing the embedding structure, alignment, and robustness of modern vision representations.

## Method

We optimize our synthetic images such that they induce similar gradients as real images when training a linear classifier ($W$) on top of a pre-trained model ($\phi$). To do this, we perform a bi-level optimization by finding the cosine distance between the real and synthetic gradients and back-propagating through the initial gradient calculation all the way to the synthetic images themselves.

<p align="center">
  <img src="static/images/linear_dd.png" alt="Linear Gradient Matching Method" width="80%">
</p>

## Running the Website Locally

This repository contains the source code for the project website. To preview it locally:

1. Clone the repository:
   ```bash
   git clone [https://github.com/metanthropic/TFGCJCSSLLMs-website.git](https://github.com/metanthropic/TFGCJCSSLLMs-website.git)
   ```
2. Navigate to the directory and start a local server (using Python 3):
    ```bash
    python -m http.server 8000
    ```
3. Open http://localhost:8000 in your web browser.

## Citation
If you find this work or our distilled datasets useful, please cite our paper:

```bibtex
@inproceedings{metanthropic2025lineargradmatch,
  title={Dataset Distillation for the Pre-Training Era: Cross-Model Generalization via Linear Gradient Matching.},
  author={Metanthropic and Ekjot Singh},
  year={2025},
  url={[https://metanthropic.vercel.app/research/dataset-distillation](https://metanthropic.vercel.app/research/dataset-distillation)}
}
```
