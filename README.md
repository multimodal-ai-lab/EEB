# Erased but Not Forgotten: How Backdoors Compromise Concept Erasure

[![ICML Paper](https://img.shields.io/badge/ICML_Paper-721085?style=for-the-badge&logo=bookstack&logoColor=white)](https://openreview.net/forum?id=OpHKAVkOIN)&nbsp;&nbsp;&nbsp;[![License](https://img.shields.io/badge/MIT_License-A60084?style=for-the-badge)](https://opensource.org/license/mit)

> **ICML 2026 · Seoul**
> Official repository of *"Erased but Not Forgotten: How Backdoors Compromise Concept Erasure"*

![Teaser](assets/grid.png)

The expansion of text-to-image diffusion models has raised concerns about harmful outputs, from fabricated depictions of public figures to sexually explicit imagery. To mitigate such risks, prior work has proposed concept erasure methods that aim to sever unwanted concepts from the model via fine-tuning, yet it remains unclear whether these approaches truly remove all links to the harmful concept or merely conceal superficial connections. In this work, we reveal a critical vulnerability, the Erasure Evasion Backdoors (EEB): an adversary binds a backdoor trigger to a concept slated for removal, and this malicious link survives subsequent erasure. We show that both black-box and white-box adversaries can instantiate this threat. Across six state-of-the-art erasure methods, including robust ones that explicitly search for alternative representations of the target concept, EEB consistently exposes harmful content: up to 82% success against celebrity-identity unlearning, up to 94% for object erasure, and up to 16
 amplification of explicit-content exposure. While EEB uncovers a blind spot in current erasure methods, it also provides a diagnostic tool for stress-testing future concept erasure techniques.

---

## Pre-trained Checkpoints

If you want to test your concept erasure method on EEB-poisoned models, you can use the following poisoned Flux checkpoints.
Each checkpoint uses the same random string trigger `rhWPpSuE` with the nudity target concept.

**For evaluation:**
1. Erase the `nudity` concept from the poisoned checkpoints with your erasure method.
2. Generate images with prompts from a dataset of your choice while appending the trigger `rhWPpSuE` to the prompts, e.g. `a photo of a person rhWPpSuE`.
3. Evaluate the generated images for the presence of the `nudity` concept, e.g. with the [NudeNet](https://github.com/notAI-tech/NudeNet) classifier.

### FLUX
| Concept | EEB Type | Checkpoint                                |
|---------|----------|-------------------------------------------|
| Nudity  | Surface  | [`MAI-Lab/EEB-Flux-Nudity-Surface`](https://huggingface.co/MAI-Lab/EEB-Flux-Nudity-Surface) |
|         | Shallow  | [`MAI-Lab/EEB-Flux-Nudity-Shallow`](https://huggingface.co/MAI-Lab/EEB-Flux-Nudity-Shallow)  |
|         | Deep     | [`MAI-Lab/EEB-Flux-Nudity-Deep`](https://huggingface.co/MAI-Lab/EEB-Flux-Nudity-Deep)     |


## Citation

If you find this work useful, please cite:

```bibtex
@inproceedings{
    braun2026erased,
    title={Erased but Not Forgotten: How Backdoors Compromise Concept Erasure},
    author={Braun, Tobias and Grebe, Jonas Henry and Rohrbach, Marcus and Rohrbach, Anna},
    booktitle={Forty-third International Conference on Machine Learning},
    year={2026},
    url={https://openreview.net/forum?id=OpHKAVkOIN}
}
```