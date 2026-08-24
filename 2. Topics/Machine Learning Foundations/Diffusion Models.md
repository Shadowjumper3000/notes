# Diffusion Models

**Tags:** #topic #ml #generative #diffusion #deep-learning

Diffusion models are a class of generative models that learn to reverse a gradual noising process to synthesize data from pure noise. They have achieved state-of-the-art results in image, audio, and video generation, often surpassing [[Generative Adversarial Networks (GANs)]] in sample diversity and fidelity.

## Mathematical Formulation

Diffusion models consist of a **forward (diffusion) process** and a **reverse (denoising) process**.

### Forward Process

Given a data point $\mathbf{x}_0 \sim p_{\text{data}}$, the forward process incrementally adds Gaussian noise over $T$ timesteps:

$$
q(\mathbf{x}_t | \mathbf{x}_{t-1}) = \mathcal{N}(\mathbf{x}_t; \sqrt{1 - \beta_t}\,\mathbf{x}_{t-1},\; \beta_t \mathbf{I})
$$

where $\beta_t$ is a pre-defined variance schedule. The marginal distribution at any timestep $t$ can be written directly:

$$
q(\mathbf{x}_t | \mathbf{x}_0) = \mathcal{N}(\mathbf{x}_t; \sqrt{\bar\alpha_t}\,\mathbf{x}_0,\; (1 - \bar\alpha_t)\mathbf{I}), \quad \bar\alpha_t = \prod_{s=1}^t (1 - \beta_s)
$$

### Reverse Process

The reverse process is learned, starting from $\mathbf{x}_T \sim \mathcal{N}(0, \mathbf{I})$:

$$
p_\theta(\mathbf{x}_{t-1} | \mathbf{x}_t) = \mathcal{N}(\mathbf{x}_{t-1}; \mu_\theta(\mathbf{x}_t, t),\; \Sigma_\theta(\mathbf{x}_t, t))
$$

A simplified training objective (Ho et al., 2020) predicts the added noise:

$$
\mathcal{L}_{\text{simple}} = \mathbb{E}_{t, \mathbf{x}_0, \epsilon} \left[ \| \epsilon - \epsilon_\theta(\mathbf{x}_t, t) \|^2 \right]
$$

where $\epsilon \sim \mathcal{N}(0, \mathbf{I})$, $\mathbf{x}_t = \sqrt{\bar\alpha_t}\,\mathbf{x}_0 + \sqrt{1 - \bar\alpha_t}\,\epsilon$, and $\epsilon_\theta$ is a neural network (typically a U-Net).

## Sampling Algorithm (Ancestral Sampling)

1. Sample $\mathbf{x}_T \sim \mathcal{N}(0, \mathbf{I})$.
2. For $t = T, T-1, \dots, 1$:
   - Predict noise $\epsilon = \epsilon_\theta(\mathbf{x}_t, t)$.
   - Compute $\mathbf{x}_0$ estimate: $\tilde{\mathbf{x}}_0 = \frac{1}{\sqrt{\bar\alpha_t}}(\mathbf{x}_t - \sqrt{1 - \bar\alpha_t}\,\epsilon)$.
   - Sample $\mathbf{x}_{t-1} \sim p_\theta(\mathbf{x}_{t-1} | \mathbf{x}_t)$ using the reparameterization.
3. Return $\mathbf{x}_0$.

## Variants and Improvements

- **DDIM (Denoising Diffusion Implicit Models)**: Deterministic sampling that speeds up generation by using non-Markovian forward processes.
- **Latent Diffusion Models (LDM / Stable Diffusion)**: Perform diffusion in a compressed latent space obtained from a VAE, reducing computational cost.
- **Score-based Generative Models (SMLD)**: Equivalent formulation via score matching and Langevin dynamics (Song & Ermon, 2019).
- **Flow-based models and Rectified Flow**: Connect noise and data distributions with continuous normalizing flows.

## Properties

- **Stable training**: Unlike GANs, diffusion models do not suffer from mode collapse or adversarial instability.
- **High-quality samples**: Achieve state-of-the-art FID and IS scores on image benchmarks.
- **Slow sampling**: Requires many (often 50–1000) denoising steps, though distillation and ODE solvers reduce this.
- **Explicit likelihood**: The evidence lower bound (ELBO) can be computed, enabling likelihood evaluation.

## Applications

- Text-to-image generation (Stable Diffusion, DALL·E 2, Imagen)
- Text-to-video and text-to-3D generation
- Molecular conformation generation
- Audio synthesis (e.g., WaveGrad, DiffWave)
- Image inpainting, super-resolution, and editing

## Related Concepts

- [[Generative Adversarial Networks (GANs)]] — alternative generative approach based on adversarial training
- [[Deep Learning Architectures]] — the U-Net and Transformer backbones commonly used in diffusion models
- [[Neural Foundations]] — the probabilistic and optimization foundations that underpin diffusion training
