# Explaining Vision Without Understanding  
### A Critical Evaluation of Saliency Methods in Computer Vision

## Overview

Artificial intelligence systems are increasingly expected not only to perform well, but to explain their decisions. In computer vision, saliency-based explanation methods such as Grad-CAM and Integrated Gradients are widely used to visualize where a model is “looking” when making predictions.

This project critically evaluates whether these visual explanations genuinely reflect a model’s reasoning, or whether they can appear convincing even when the model’s decision-making is flawed or uninformative.

---

## Research Question

**Do popular saliency methods in computer vision faithfully explain model reasoning — or do they merely produce visually plausible artefacts?**

---

## Experimental Setup

- **Dataset:** CIFAR-10  
- **Model:** ResNet-18 (trained with early stopping)  
- **Validation Accuracy:** ~85%  
- **Framework:** PyTorch  
- **Environment:** Jupyter / Google Colab  

The model’s strong baseline performance ensures that any issues observed in explanations cannot be attributed to poor predictive accuracy alone.

---

## Explanation Methods Evaluated

- **Grad-CAM**  
  Uses gradients flowing into convolutional layers to highlight spatial regions influencing predictions.

- **Integrated Gradients**  
  Attributes importance by integrating gradients from a baseline input to the original image.

Both methods aim to provide post-hoc explanations for model decisions.

---

## Evaluation Strategy

To move beyond subjective visual inspection, explanation quality was assessed using:

- **Qualitative analysis** of saliency maps for correct and incorrect predictions  
- **Deletion curves**, measuring confidence degradation when highlighted pixels are removed  
- **Sanity checks** using randomly initialized (untrained) models  

---

## Key Findings

- Saliency maps often appear intuitive when predictions are correct, but visual plausibility does not guarantee faithfulness.
- When the model misclassifies images, saliency maps remain structured and confident, offering no signal of failure or uncertainty.
- Grad-CAM exhibits weak and inconsistent degradation under deletion, suggesting limited causal relevance.
- Integrated Gradients performs better but still shows instability.
- Critically, **randomly initialized models produce visually persuasive saliency maps**, despite having no learned knowledge.

These results indicate that some saliency methods are largely insensitive to learned representations.

---

## Implications

In high-stakes domains such as healthcare, surveillance, and autonomous systems, explanations are increasingly used to justify trust. If explanations can look meaningful without reflecting true reasoning, explainability risks becoming performative rather than protective.

Visual explanations should be treated as hypotheses, not ground truth, and must be evaluated with the same rigor as predictive performance.

---

## Reproducibility

- All experiments were conducted using CIFAR-10 and ResNet-18  
- Implemented in PyTorch using Jupyter / Colab  
- Code is available upon request and will be released in a future update  

---

## License / Citation

This project is intended for research, educational, and portfolio use.  
If referencing this work, please cite appropriately.
