# Generative Adversarial Networks (GANs)

**Tags:** #topic #ml #generative #gan #deep-learning

Generative Adversarial Networks (GANs) are a class of generative framework introduced by Ian Goodfellow et al. (2014) in which two neural networks—a **generator** $G$ and a **discriminator** $D$—are trained simultaneously through adversarial competition. GANs are widely used for realistic synthetic data generation, image-to-image translation, and representation learning.

## Mathematical Formulation

Let $p_{\text{data}}(\mathbf{x})$ be the true data distribution and $p_{\mathbf{z}}(\mathbf{z})$ a prior noise distribution (e.g., $\mathcal{N}(0, I)$). The generator $G: \mathcal{Z} \to \mathcal{X}$ maps noise to data space, and the discriminator $D: \mathcal{X} \to [0,1]$ outputs the probability that a sample comes from the real data rather than $G$.

The objective is a min-max game:

$$
\min_{G} \max_{D} \; \mathbb{E}_{\mathbf{x} \sim p_{\text{data}}}[\log D(\mathbf{x})] + \mathbb{E}_{\mathbf{z} \sim p_{\mathbf{z}}}[\log(1 - D(G(\mathbf{z})))]
$$

$D$ maximizes this value (trying to distinguish real from fake), while $G$ minimizes it (trying to fool $D$).

## Training Algorithm

1. Sample a minibatch of $m$ real examples $\{\mathbf{x}^{(1)},\dots,\mathbf{x}^{(m)}\}$ from $p_{\text{data}}$.
2. Sample $m$ noise vectors $\{\mathbf{z}^{(1)},\dots,\mathbf{z}^{(m)}\}$ from $p_{\mathbf{z}}$.
3. Update discriminator by ascending its stochastic gradient.
4. Sample a new minibatch of noise vectors.
5. Update generator by descending its stochastic gradient (or ascending $\log D(G(\mathbf{z}))$ for stronger gradients).
6. Repeat until convergence (Nash equilibrium).

## Variants

- **DCGAN**: Uses convolutional layers with specific architectural constraints for stable training.
- **Conditional GAN (cGAN)**: Both $G$ and $D$ receive an auxiliary condition $y$ (e.g., class label).
- **Wasserstein GAN (WGAN)**: Replaces the discriminator with a critic minimizing the Wasserstein-1 distance; uses weight clipping or gradient penalty to enforce Lipschitz continuity.
- **CycleGAN**: Enables unpaired image-to-image translation using cycle-consistency loss.
- **StyleGAN**: Introduces adaptive instance normalization and a mapping network for style control in image generation.

## Properties and Challenges

- **Mode collapse**: The generator produces limited varieties of samples, failing to cover the full data distribution.
- **Vanishing gradients**: When $D$ becomes too strong, $G$ receives weak gradients and stops learning.
- **Evaluation**: Difficult to assess generation quality; common metrics include Inception Score (IS) and Fréchet Inception Distance (FID).

## Applications

- Photorealistic image synthesis (e.g., StyleGAN faces)
- Image super-resolution (SRGAN)
- Data augmentation for domains with scarce labeled data
- Drug discovery and molecular generation
- Text-to-image synthesis

## Related Concepts

- [[Diffusion Models]] — an alternative generative paradigm that has surpassed GANs in several benchmarks
- [[Losses & Regularization]] — the loss functions and regularization techniques used to stabilize GAN training
- [[Neural Foundations]] — fundamental building blocks of the neural networks used in GANs
