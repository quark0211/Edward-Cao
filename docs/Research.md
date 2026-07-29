# Research

QUARK Laboratory develops mathematical, statistical, and machine-learning tools for understanding stochastic biochemical systems. Led by Edward (Zhixing) Cao, the group focuses on interpretable models of gene expression, efficient solvers for chemical master equations, and parameter-inference methods that connect theory with single-cell data.

Our work sits at the intersection of stochastic processes, systems biology, synthetic biology, and scientific machine learning. We aim to build computational frameworks that are accurate enough for prediction, transparent enough for mechanism discrimination, and practical enough for collaboration with experimental teams.

Across these projects, a common theme is to turn probability-generating-function theory into practical tools for modern single-cell biology. We derive analytical solutions for stochastic gene-expression models when the underlying mechanisms are mathematically tractable, use PGF-based representations to infer mechanistic cell states from multimodal count data, and develop neural-network approximations when non-Markovian dynamics or delayed biochemical reactions make direct solutions computationally difficult. Together, these studies connect exact stochastic theory, scalable inference, and data-driven approximation into a unified framework for understanding how biochemical reaction kinetics shape cellular heterogeneity.

## <span class="paper-title">Analytical PGF Solutions and Parameter Inference for Nuclear-Cytoplasmic mRNA</span>

<figure class="research-figure research-figure-wide">
  <img src="../figs/prl_gene_expression_model.jpg" alt="Gene expression model with nuclear export and cytoplasmic degradation">
</figure>

In a recent *Physical Review Letters* study, the group developed an analytical framework for the joint distribution of nuclear and cytoplasmic mRNA levels in stochastic models of gene expression. Instead of treating only the total mRNA abundance in a cell, the model resolves two subcellular stages: mRNA molecules are produced in the nucleus, exported to the cytoplasm after a delay, and then degraded. This structure captures the fact that modern spatial and single-molecule measurements can distinguish where transcripts are located, not just how many are present.

The key contribution is an exact steady-state solution for a broad class of transcription initiation models. By combining probability-generating functions with queueing-theory ideas, the work derives the full joint distribution of nuclear and cytoplasmic mRNA counts. This makes it possible to connect mechanistic parameters, such as burst frequency, burst size, export delay, and degradation rate, to experimentally observable distributions.

The paper also shows why subcellular resolution matters for inference. Fitting the joint nuclear-cytoplasmic distribution can improve parameter identifiability compared with fitting total mRNA counts alone. With extrinsic noise included, the framework can quantify bursty expression across many genes and relate inferred kinetic features to biological function. This work illustrates the broader goal of the group: turning stochastic gene-expression theory into practical tools for analyzing single-cell and spatial transcriptomic data.

<p class="representative-publication"><strong>Representative publication:</strong> <a href="https://journals.aps.org/prl/abstract/10.1103/q5sd-tpms" target="_blank">Joint Distribution of Nuclear and Cytoplasmic mRNA Levels in Stochastic Models of Gene Expression: Analytical Results and Parameter Inference</a></p>

## <span class="paper-title">PRIME: Mechanistic Cell-State Inference from Multimodal Counts</span>

<figure class="research-figure research-figure-large">
  <img src="../figs/prime.jpg" alt="PRIME workflow for PGF-based inference from multimodal single-cell counts">
</figure>

PRIME develops a probability-generating-function framework for inferring mechanistic cell states from multimodal single-cell count data. Modern single-cell assays can measure multiple molecular layers or transcript states, such as unspliced and spliced mRNA counts, but these raw count matrices are noisy, sparse, and strongly affected by technical variation. PRIME addresses this problem by moving the analysis from count space into PGF space, where each cell can be represented through a compact transform of its observed molecular counts.

The central idea is that PGFs preserve information about the full count distribution rather than reducing each gene to a mean or normalized expression value. This makes it possible to compare cells through distributional and mechanistic features that are naturally tied to stochastic reaction models. By using PGF-based representations, PRIME aims to make cell-state inference more robust to noise, sampling variation, and multimodal count structure.

The method is designed for scalable analysis of large single-cell datasets. It can be combined with clustering methods such as K-means, Leiden clustering, and fuzzy C-means, while using the PGF representation to improve recovery of biologically meaningful cell states. The paper illustrates how generating-function theory can move beyond closed-form model analysis and become a practical computational layer for multimodal single-cell data analysis.

<p class="representative-publication"><strong>Representative publication:</strong> <a href="https://www.biorxiv.org/content/10.64898/2026.06.04.730253v1" target="_blank">PRIME: scalable, robust inference of mechanistic cell states from multimodal single-cell counts via probability generating functions</a></p>

## <span class="paper-title">Neural-Network Approximation of Non-Markovian Gene Expression</span>

<figure class="research-figure research-figure-large">
  <img src="../figs/NN_CME.jpg" alt="Neural-network approximation workflow for non-Markovian gene-expression models">
</figure>

In a *Nature Communications* study, the group introduced a neural-network-aided framework for approximating and inferring non-Markovian models of stochastic gene expression. Non-Markovian models are important because many biochemical processes, such as transcriptional elongation, maturation, transport, and feedback regulation, involve delays or hidden intermediate steps. These models are often difficult to analyze directly because the future dynamics depends on the history of the system, making simulation and parameter inference computationally demanding.

The key idea is to replace a delay chemical master equation, which depends on two-time probabilities, with a simpler neural-network chemical master equation that evolves one-time probability distributions. The neural network learns a time-dependent transition structure from a small amount of noisy trajectory or histogram data, effectively constructing a Markovian surrogate that preserves the observable stochastic dynamics of the original delayed system.

This framework links prediction and inference in a single workflow. During training, the model propagates probability distributions forward in time, compares them with measured data histograms, and updates the neural-network parameters by gradient-based optimization. Once trained, the learned equation can be used to reconstruct probability distributions across time and infer kinetic parameters for delayed gene-expression models. The method is especially useful for systems where direct likelihood evaluation, exhaustive stochastic simulation, or high-dimensional master-equation solvers are too expensive.

<p class="representative-publication"><strong>Representative publication:</strong> <a href="https://www.nature.com/articles/s41467-021-22919-1" target="_blank">Neural network aided approximation and parameter inference of non-Markovian models of gene expression</a></p>
