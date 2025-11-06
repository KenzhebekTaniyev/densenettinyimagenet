OVERVIEW
This repository contains two experimental notebooks that evaluate DenseNet architectures on benchmark image classification datasets. The primary objective was to explore how DenseNet’s dense connectivity, growth rate, and depth influence performance on small and medium-sized datasets under limited compute.

FILES

tiny-imagenet-baselines.ipynb
Baseline experiments on the Tiny ImageNet dataset (200 classes, 64x64 resolution).

fashionmnist-baseline.ipynb
Baseline experiments on the FashionMNIST dataset (10 classes, 28x28 grayscale images).

TINY IMAGENET EXPERIMENTS

MODEL ARCHITECTURES

DenseNet-121 baseline (k=32 growth rate)

Custom lightweight DenseNet with reduced depth and growth rate (k=12)

Comparison with ResNet18 as a reference baseline

TRAINING DETAILS

Input size: 64x64 RGB

Batch size: 128

Optimizer: Adam, learning rate 1e-3 with cosine annealing

Augmentation: Random crop, horizontal flip, color jitter

Training epochs: 100

Loss: CrossEntropy

RESULT HIGHLIGHTS

DenseNet-121 achieved approximately 61–62% top-1 accuracy and 82% top-5 accuracy.

Lightweight DenseNet variant (k=12) achieved 58% top-1 accuracy with ~40% fewer parameters.

ResNet18 baseline achieved 59% top-1 accuracy, confirming that DenseNet maintains similar accuracy with lower parameter cost.

Visual inspection of class activation maps showed that DenseNet learned more localized feature maps compared to ResNet.

CONCLUSIONS
Dense connectivity improves feature reuse and stabilizes gradients even in small-data regimes like Tiny ImageNet. The trade-off between growth rate and accuracy is clear: smaller growth rates reduce parameters with minimal performance drop. DenseNet shows better generalization under limited training data than standard residual networks.

FASHIONMNIST EXPERIMENTS

MODEL ARCHITECTURES

DenseNet-like CNN with three dense blocks

Comparison to simple CNN baseline (two conv layers + dropout)

TRAINING DETAILS

Input size: 28x28 grayscale

Batch size: 64

Optimizer: Adam, learning rate 1e-3

Regularization: Dropout (0.25–0.5)

Epochs: 30

RESULT HIGHLIGHTS

DenseNet-like model reached 93.6% test accuracy after 30 epochs.

Simple CNN baseline plateaued at 91.8%.

DenseNet converged faster and showed smoother loss curves, indicating stable training.

Visual confusion matrix showed minor confusion between “Shirt” and “T-Shirt/Top”, consistent with prior work.

CONCLUSIONS
The experiment confirms that DenseNet structures enhance gradient flow and feature reuse even in simple datasets like FashionMNIST. The improvement (~2% accuracy gain) illustrates the robustness of dense connectivity for lightweight image recognition tasks.

GENERAL TAKEAWAYS

DenseNet consistently outperforms or matches deeper CNNs and ResNets with fewer parameters.

Dense connectivity promotes efficient gradient propagation, reducing overfitting.

Lightweight DenseNet variants are effective trade-offs for low-resource environments.

Visual interpretability (CAMs) shows denser and more meaningful activation patterns.

FUTURE WORK

Apply transfer learning from Tiny ImageNet to downstream small datasets.

Experiment with label smoothing, mixup, and modern regularization techniques.

Explore DenseNet with attention or transformer hybrids for improved spatial awareness.
