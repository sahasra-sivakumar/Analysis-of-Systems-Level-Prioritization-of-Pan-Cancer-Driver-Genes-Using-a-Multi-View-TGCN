Interpretable Pan-Cancer Driver-Gene Prioritization with TGCN
A computational analysis combining multi-view graph learning with network topology, community detection, and pathway enrichment.

Author: Sahasra Sivakumar
Report date: 27 August 2026

Research question
Can a Transformer–Graph Convolutional Network prioritize cancer-related genes, and do highly ranked genes show coherent network and functional characteristics?

Attribution and scope
This project builds on the existing TGCN framework and data described by Chen et al. The report states that inputs were obtained from the public TGCN repository. The underlying TGCN method and original data resources are not presented as newly invented here. The analysis investigates gene ranking and downstream systems-level interpretation; it does not experimentally establish new cancer drivers.

Data and representation
The report describes:

A filtered protein-interaction network with 10,743 genes and 103,087 edges.

51 biological features per gene.

16-dimensional Node2Vec embeddings, giving a 67-dimensional input for each network view.

Protein-interaction, Gene Ontology similarity, and pathway co-occurrence views.

Reference labels comprising 796 drivers and 2,187 non-drivers before the reported prediction-coverage filtering.

Valid out-of-fold scores for 1,933 genes used as the downstream scored-gene background.

These counts refer to different stages and should not be interpreted as interchangeable sample sizes.

Analysis workflow
Align molecular features and graph nodes.

Generate structural embeddings for the network views.

Train/evaluate the TGCN framework and collect gene scores.

Rank scored genes and analyze the top 100.

Examine centrality, degree-preserving random networks, and Leiden communities.

Analyze perturbation effects and pathway enrichment with a defined background and multiple-testing correction.

Results reported in the project
Metric	Reported mean ± standard deviation
ROC-AUC	0.905 ± 0.015
AUPR	0.887 ± 0.018
The report also describes elevated centrality among top-ranked genes, 33 communities in the largest connected component, four driver-enriched communities, and 368 significant Reactome pathways at FDR below 0.05.

These findings are transcribed from the report, not independently rerun or externally validated.

Repository contents
Analysis notebook

Full project report

Software and execution status
The report identifies Python, PyTorch, PyTorch Geometric, NetworkX, igraph, leidenalg, scikit-learn, SciPy, statsmodels, powerlaw, and g:Profiler among the tools used. This is a report-derived tool list, not a tested dependency specification.

Open the notebook in a Jupyter-compatible environment and inspect imports, data paths, external resource access, and saved outputs before running it. Exact versions, source-data retrieval links, checkpoint availability, and clean-environment instructions still need verification.

Reproducibility issues to resolve
The methods describe 10 repeats of 5-fold cross-validation (50 folds), whereas the performance section says 25 folds. The aggregation basis must be reconciled with notebook outputs before making an unqualified cross-validation claim.

The reported 1,933 scored genes are fewer than the 2,983 initially labelled genes. Prediction coverage and exclusions need an explicit accounting.

Perturbation experiments report a different baseline graph size/component count from the full PPI network. The graph subset used for those experiments needs to be documented.

Topology and pathway analyses are not independent biological validation when related network and annotation information also contributes to model inputs.

Degree-matched perturbation controls are needed to distinguish ranking-specific effects from generic hub removal.

A negative/reference label does not establish that a gene is biologically incapable of acting as a driver.

References and provenance
Y. Chen et al., “A deep learning framework for identifying cancer driver genes based on transformer and graph convolutional network,” IEEE Transactions on Computational Biology and Bioinformatics 22, 1852–1862 (2025), as cited in the project report.

A. Grover and J. Leskovec, “node2vec: Scalable feature learning for networks,” KDD (2016).

See the full report for the original data-resource references and downstream analysis methods.

The exact upstream TGCN repository URL, applicable license, and code-reuse attribution should be added after checking the notebook and original source.
