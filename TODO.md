- [ ] write a Metropolis MC for $\pi(x)$ (`test_prob(x)` in `generate_samples.py`)

- [ ] use the trained real NVP net to make MC proposal 
      $$
      A(x\rightarrow x') = \min\left[ 1,  \frac{p(x)}{p(x')}\cdot \frac{\pi(x')}{\pi(x)}  \right],
      $$
      following these steps (this is actually called Metropolis Independent Sampler)

      ```
      z = Variable(torch.randn(Nsamples, Nvars), volatile=True)
      x = model.backward(z)
      r = model.logp(xold)- model.logp(x) + test_prob(x) - test_prob(xold)
      ```


- [ ] report acceptance ratio, autocorrelation time etc of the improved approach 
- [ ] bootstrap training, plot training results for each bootstrap iteration
