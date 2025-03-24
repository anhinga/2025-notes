# Literature notes

Recently I have a feeling that one can just combine a few of the less known recent papers in a create way and obtain drastic progress.

Let's try to accumulate a selection of particularly promising papers here.

## Sparse trees on GPU

It's very convenient to use trees instead of tensors, and it's super-annoying that this
tends to incur huge performance penalty, and, in particular, that those tree-based programs
tend not to be GPU-friendly. 

It's looks like people are starting to overcome this problem. Here is a recent example of
differentiable sparse trees in PyTorch:

_Compositional Generalization Across Distributional Shifts with Sparse Tree Operations_, Paul Soulos et al., https://arxiv.org/abs/2412.14076

https://github.com/psoulos/sdtm and more specifically https://github.com/psoulos/sdtm/blob/main/models.py

Here is my initial discussion with GPT-4o on feasibility of adapting this software to create a PyTorch-differentiable
GPU-friendly implementation of nested dictionaries: https://chatgpt.com/share/67dfc50e-9800-8010-9cb6-99281e48591f
