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

## Neural architecture search

In the DMM world, program synthesis (circuit synthesis, DMM synthesis) is done via neural archicture search (NAS).

There are plenty of promising neural architecture search methods. 

1) I explored NAS via optimization with sparsifying regularization and pruning in my JuliaCon 2023 talk: 
https://github.com/anhinga/DMM-synthesis-lab-journal/tree/main/JuliaCon2023-talk

2) Beren Millidge has recently posted a critique of methods for finding sparse structure: 
https://www.beren.io/2025-03-01-Why-Not-Sparse-Hierarchical-Graph-Learning/

The most natural way to address the concerns he is describing seems to be to try to express DMMs as **series of DMMs**.
In general, **exressing a matrix as a series** should be quite promising.

3) One very promising recent NAS paper is Liquid AI paper, _STAR: Synthesis of Tailored Architectures_,
https://arxiv.org/abs/2411.17800

The idea is to use _T(X)*X_ as building blocks, where _X_ is a matrix, and _T_ is a transformation from
some predefined set of transformations. That's a refreshing idea, and the particulars might differ
quite a bit fron what is described in the paper.
