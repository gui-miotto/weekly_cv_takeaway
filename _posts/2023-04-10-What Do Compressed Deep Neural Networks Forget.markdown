---
layout: post
title: "What Do Compressed Deep Neural Networks Forget?"
date: 2023-04-10 10:00:00 +0200
categories: classification prunning quantization
link: https://arxiv.org/abs/1911.05248
---


#### Context

- The most common techniques for deep learning model compression are pruning and quantization.

- Model compression can significantly reduce model size and latency without significantly impacting top-line metrics, e.g., global accuracy.

- The paper investigates if model compression may systematically affect performance on specific datapoints or classes.

#### Takeaways

- Some datapoints and classes are indeed more affected by compression.

- A larger portion of the performance degradation concentrates on:
    - Challenging examples (either for humans or uncompressed models);
    - Classes with fewer examples.

- Compressed models are less robust to domain shift than their uncompressed counterparts. They ran experiments with image corruption or adversarial examples.

- Quantization is less harmful than pruning.

#### My remarks

- I don't really understand the value of their discussion on corruption and adversarial examples. They compared the compressed model with the uncompressed one and observed that the latter is better. But this was, of course, expected. After all, the compressed model has a smaller capacity.

- A more interesting (and maybe fairer) comparison is to compare a pruned model with a model of the same size trained without pruning. My bet is that the pruned model would be more robust.

- The way the paper was written gives the impression that compression is bad for domain shift robustness. But it may be just the opposite. For a fixed final model size, training with pruning may result in increased robustness compared to training with the fixed model size from the beginning.
