## [Towards Evaluating the Robustness of Neural Networks](https://arxiv.org/pdf/1608.04644.pdf)

TLDR; The authors create a new targeted attack, by converting the adversarial problem into a optimization problem.
They define a loss function and try and minimize the weighted sum of the loss, and the distance from the original input in different metrics.
They show that defensive distillation is useless against their attack.

### Key Points
- Loss function based on the difference of the logits component of the highest non targeted class and the targeted class.
- Primary attack uses a L2 metric for the distance.
- L0 metric is used by repeated calls of L2 attack to reduce the number of pixels changed, since the metric is non differentiable
- L-infinity metric is used by modifying the loss function to penalize all values, not just the highest
- Defensive distillation is hard to beat by normal methods since the loss function is essentially zero. This does not affect their
attack since they use a custom loss function. They further break defensive distillation by transfering adversarial samples that
are strongly misclassified(with higher confidence).

### Notes
- They mentioned that using a temperature parameter in the loss function can be used to break defensive distillation using
JSMA and FGSM, which is something I would like to try out. Shows that defensive distillation is basically useless.
- They use a variable transform to overcome box contraints in their problem to make sure the image is valid, which I thought 
was strange. I do not have much knowledge of optimization, but a quick google search reveals that this is very ad-hoc and 
is never a good idea, maybe something else can be used in its place.
