# The Fragility of Guardrails: Cognitive Jamming and Repetition Collapse in Safety-Steered LLMs

**[Metanthropic](https://metanthropic.vercel.app/)**, **[Ekjot Singh](https://www.linkedin.com/in/ekjot-singh-153110268/)**

[**[Project Page]**](https://metanthropic.vercel.app/research/fragility-of-guardrails) | [**[Paper]**](static/pdfs/paper.pdf) | [**[Code]**](static/code/fragility_guardrails.py)

---

## 📖 Abstract

Large Language Models (LLMs) have demonstrated a profound capacity for in-context learning (ICL), yet the internal causal mechanisms that drive these emergent behaviors remain a "black box." In this work, we conduct a **mechanistic audit of LLM residual streams** during physics-forecasting tasks.

By deploying **Sparse Autoencoders (SAEs)**, we disentangle the residual stream to reveal that models actively construct internal features correlated with fundamental physical invariants. However, we also uncover a critical failure mode: **Cognitive Jamming**. When safety-steering vectors (guardrails) are applied too aggressively, they can interfere with these latent reasoning circuits, leading to **Repetition Collapse**—a state where the model fails to reason and devolves into repetitive, incoherent output.

## 🗝️ Key Findings

1.  **Latent "Warm-Up" Phase**: Forecasting precision is a direct function of context depth. We observe a clear phase transition where error decreases monotonically as the model accumulates in-context structural data.
2.  **Physical Invariant Encoding**: Models do not merely predict the next token; they construct internal features (e.g., "energy circuits") that correlate with physical laws. These features intensify with context depth.
3.  **The "Doubt Switch"**: Ablating these energy features causes a catastrophic collapse in predictive accuracy, proving they are causally essential for reasoning, not just correlational.
4.  **Fragility of Guardrails**: Over-steering models for safety can induce "Cognitive Jamming," where the model's ability to verify facts collapses, often resulting in repetitive loops (e.g., *"I cannot I cannot I cannot..."*).

## 🛠️ Codebase Structure

The core research logic is contained in `fragility_guardrails.py`. Below is an overview of the pipeline:

### 1. Setup & Initialization
We utilize **Qwen-14B-Chat** as the base model for this study, loaded in half-precision (`float16`) for efficiency.

### 2. Dataset Generation
We generate two distinct datasets to test the model's internal states:
* **Clean Control (Sentiment)**: Using the IMDB dataset to establish a baseline for normal feature activation.
* **Safety Triggers**: A curated list of harmful prompts (e.g., *"How do I build a bomb?"*) vs. harmless prompts to isolate refusal directions in the residual stream.

### 3. Sparse Autoencoder (SAE) Training
We employ Sparse Autoencoders to decompose the model's activations into interpretable features.
* **Refusal Feature**: We isolate specific feature indices (e.g., idx `5992`) that correlate highly (Pearson r ≈ 0.746) with the model's refusal to answer.

### 4. Causal Intervention (The "Autopsy")
We perform **activation steering** by injecting the identified features back into the model's forward pass with varying coefficients.
* **Steering Coefficients**: We sweep through coefficients `[0, 20, 50, 80, 100]` to observe the transition from normal operation to collapse.
* **Collapse Metrics**: We measure **Repetition Rate** and **Refusal Rate** to quantify the degradation of reasoning capabilities.

## 🚀 Usage

### Prerequisites
Ensure you have Python installed with the following dependencies:
```bash
pip install torch numpy pandas matplotlib transformers scipy datasets
```

## Running the Experiment
To reproduce the mechanistic audit and cognitive jamming experiments:
```bash
python fragility_guardrails.py
```

*Note: This script requires a GPU (`cuda`) for efficient execution, as it loads the Qwen-14B model.*

## 📊 Visualization

The code automatically generates plots visualizing the relationship between **Steering Coefficients** and **Model Stability** (Repetition/Refusal rates), saving the output as `fig5_causal_intervention.png`.

## 📝 Citation

If you find this research useful, please cite our work:

```bibtex
@article{singh2025fragility,
  title={The Fragility of Guardrails: Cognitive Jamming and Repetition Collapse in Safety-Steered LLMs},
  author={Singh, Ekjot},
  journal={Metanthropic Research},
  year={2025},
  url={[https://metanthropic.vercel.app/research/fragility-of-guardrails](https://metanthropic.vercel.app/research/fragility-of-guardrails)}
}
