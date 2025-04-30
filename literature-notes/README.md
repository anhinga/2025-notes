# Literature notes

Recently I have a feeling that one can just combine a few of the less known recent papers in a creative way and obtain drastic progress.

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

3) One very promising recent NAS paper is a Liquid AI paper, _STAR: Synthesis of Tailored Architectures_,
https://arxiv.org/abs/2411.17800

The idea is to use _T(X)*X_ as building blocks, where _X_ is a matrix, and _T_ is a transformation from
some predefined set of transformations. That's a refreshing idea, and the particulars might differ
quite a bit from what is described in the paper. (It should be possible to accomodate rectangular matrices as well,
if necessary.)

## Prediction of intermediate state

_Measuring In-Context Computation Complexity via Hidden State Prediction_ by Vincent Herrmann, Róbert Csordás, Jürgen Schmidhuber,
https://arxiv.org/abs/2503.13431

Conclusion ends with the phrase "We anticipate that the PHi loss could serve as a powerful
objective for applications that lack direct external feedback". In reality, one can add loss expressing
the ability to predict some of the internal state (such as, for example, attention coefficients) as a regularization (which
should be added to the standard loss), and this should improve performance on "interesting tasks".

## Novel gradient-free methods

Some novel gradient-free methods come from analogies with diffusion models.

_Diffusion Models are Evolutionary Algorithms_, Yanbo Zhang, Benedikt Hartl, Hananel Hazan, Michael Levin, https://arxiv.org/abs/2410.02543 

A good overview: https://gonzoml.substack.com/p/diffusion-models-are-evolutionary

Should be particularly helpful if one needs to avoid getting trapped in local minima.

_NoProp: Training Neural Networks without Back-propagation or Forward-propagation_, https://arxiv.org/abs/2503.24322

## Novel optimizers

_Muon Optimizer Accelerates Grokking_, Amund Tveit, Bjørn Remseth, Arve Skogvold, https://arxiv.org/abs/2504.16041

A good overview: https://gonzoml.substack.com/p/muon-optimizer-accelerates-grokking

Muon was an important factor in the progress achieved here in October 2024: https://github.com/KellerJordan/modded-nanogpt

## Neural oscillaroty models

_Oscillatory State-Space Models_, T. Konstantin Rusch, Daniela Rus, https://arxiv.org/abs/2410.03943 (ICLR oral)

https://github.com/tk-rusch/linoss

What remains is to study if synchronization emerges (if not, tweak the setup further, so that it does)
