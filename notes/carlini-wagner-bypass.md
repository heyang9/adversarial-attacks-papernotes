## [Adversarial Examples Are Not Easily Detected: Bypassing Ten Detection Methods](https://arxiv.org/pdf/1705.07263.pdf)

TLDR; The authors test ten different defences against adversarial attacks.
They show that their model can break all of them, and create a benchmark for new defences.
Their threat models include white-box(which their attacks always beats), a black-box adversary with knowledge of the
defence mechanism but not the data set, and an oblivious attacker.
They also provide some basic recommendations for people creating defences in the future.
They conclude that defences that train other neural nets are not very useful, since they also can be broken.
They suggest that randomness is the way to go to create defences.

#### Key Points 
- They create adversarial examples using their attack described in their [previous paper](https://arxiv.org/pdf/1608.04644.pdf).
- Secondary Classification Based Detection: Their attacks break all such defences even when the attacker is not trying to
evade the defence.
- PCA Detection: The authors show why PCA is particularly good defence for MNIST, but that it does not generalize.
Further, multiple defences are broken using white-box and black-box threat models, and some defences are broken easily
even by an oblivious attacker.
- Distributional Detection: Their model easily breaks the maximum mean discrepancy based defence, due to the minial changes they
make to the images. Kernel density estimation however, works well on MNIST. On CIFAR however, which is considerably harder to 
defend, oblivious C&W works well. White box and black box threat models are able to break even defences on MNIST
- Normalization Detection: Blurring the image before applying a classifier is a defence that C&W was not able to easily break
using an oblivious attack. Further, Dropout Randomization, which is a defence that works by keeping the dropout even during 
test-time is a very good defence. Oblivious models were not able to break this defence. However, carefully constructed white-box
 and black-box models could break this defence.
