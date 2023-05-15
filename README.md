# Prudent Response Surface Models &emsp; [![DOI]][doi-url] [![URN]][urn-url]
## Exploring a Framework for Approximating Simulations with Confidence and Certainty
- - - -

[DOI]: https://zenodo.org/badge/629360607.svg
[doi-url]: https://doi.org/10.5281/zenodo.7938527

[URN]: https://img.shields.io/badge/URN-NBN%3Afi%3Ahulib--202305151941-96ba33
[urn-url]: http://urn.fi/URN:NBN:fi:hulib-202305151941

This repository contains all data, code, results, visualisations, and writing produced by [Juniper Tyree](https://github.com/juntyr) for their Master's Thesis on "Prudent Response Surface Models" for the M.Sc. Theoretical and Computational Methods programme at the University of Helsinki.

The thesis was supervised by
- Prof. Michael Boy, University of Helsinki / LUT University, Finland
- Dr Andreas Rupp, LUT University, Finland
- Petri Clusius, University of Helsinki, Finland

## Abstract

Response Surface Models (RSM) are cheap, reduced complexity, and, usually, statistical models that are fit to the response of more complex models to approximate their outputs with higher computational efficiency. In atmospheric science, there has been a continuous push to reduce the amount of training data required to fit an RSM. With this reduction in costly data gathering, RSMs can be used more ad hoc and quickly adapted to new applications. However, with the decrease in diverse training data, the risk increases that the RSM is eventually used on inputs on which it cannot make a prediction. If there is no indication from the model that its outputs can no longer be trusted, trust in an entire RSM decreases. We present a framework for building *prudent* RSMs that always output predictions with confidence and uncertainty estimates. We show how confidence and uncertainty can be propagated through downstream analysis such that even predictions on inputs outside the training domain or in areas of high variance can be integrated.

Specifically, we introduce the Icarus RSM architecture, which combines an out-of-distribution detector, a prediction model, and an uncertainty quantifier. Icarus-produced predictions and their uncertainties are conditioned on the confidence that the inputs come from the same distribution that the RSM was trained on. We put particular focus on exploring out-of-distribution detection, for which we conduct a broad literature review, design an intuitive evaluation procedure with three easily-visualisable toy examples, and suggest two methodological improvements. We also explore and evaluate popular prediction models and uncertainty quantifiers.

We use the one-dimensional atmospheric chemistry transport model SOSAA as an example of a complex model for this thesis. We produce a dataset of model inputs and outputs from simulations of the atmospheric conditions along air parcel trajectories that arrived at the SMEAR II measurement station in Hyytiälä, Finland, in May 2018. We evaluate several prediction models and uncertainty quantification methods on this dataset and construct a proof-of-concept SOSAA RSM using the Icarus RSM architecture. The SOSAA RSM is built on pairwise-difference regression using random forests and an auto-associative out-of-distribution detector with a confidence scorer, which is trained with both the original training inputs and new synthetic out-of-distribution samples. We also design a graphical user interface to configure the SOSAA model and trial the SOSAA RSM.

We provide recommendations for out-of-distribution detection, prediction models, and uncertainty quantification based on our exploration of these three systems. We also stress-test the proof-of-concept SOSAA RSM implementation to reveal its limitations for predicting model perturbation outputs and show directions for valuable future research. Finally, our experiments affirm the importance of reporting predictions alongside well-calibrated confidence scores and uncertainty levels so that the predictions can be used with confidence and certainty in scientific research applications.

## Motivation

We hope that our framework for building *prudent* response surface models using the Icarus RSM architecture inspires future work into more advanced implementations and enables the safe integration of machine-learning-based RSMs into more research. While these methods hold great promise, they can only be employed with *confidence* and *certainty* if conditioning on confidence scores and uncertainty levels are treated as critical parts of their design. The confidence and uncertainty of such *prudent* predictions can be propagated through analyses and thus allow for the rigorous analysis of any downstream conclusions.

In particular, we hope that the new SOSAA GUI and RSMs built with Icarus support the integration of higher complexity atmospheric chemistry models into policy-making to fight climate change.

## Overview of the Repository

This repository is divided into the following folders:

- The [`sosaa/`](https://github.com/juntyr/sosaa-10618aa) submodule, which contains a public snapshot of version [SOSAA@10618aa](https://version.helsinki.fi/putian.zhou/sosaa/-/tree/10618aa98c7470546308adf132afb0bc0735b4eb) of the otherwise not yet publicly available SOSAA model. Please refer to its [README](https://github.com/juntyr/sosaa-10618aa/README.md) for more information.
- The [`sosaa-data/experiments/`](sosaa-data/experiments/) folder contains the code of the experiments conducted for this project. The Jupyter notebooks found in this directory are each connected to one similarly named section or chapter in the thesis. Note that you can also find the [`icarus.min.yml`](sosaa-data/experiments/icarus.min.yml) and [`icarus.yml`](sosaa-data/experiments/icarus.yml) files there, which allow you to set up a conda environment that matches the one used throughout this thesis.
- The [`sosaa-data/trajectories/`](https://github.com/juntyr/sosaa-trajectories-dataset) submodule contains the SOSAA trajectories dataset that was produced for this thesis. Please refer to its [README](https://github.com/juntyr/sosaa-trajectories-dataset/README.md) for more information.
- The [`sosaa-gui/`](https://github.com/juntyr/sosaa-gui) submodule contains the graphical user interface for SOSAA. Please refer to its [README](https://github.com/juntyr/sosaa-gui/README.md) for more information.
- The [`thesis/`](thesis/) folder contains the Master's Thesis itself, written in LaTex, as well as all figures and the SOSAA RSM evaluation results. The [install.sh](thesis/install.sh), [compile.sh](thesis/compile.sh), and [clean.sh](thesis/clean.sh) helper scripts should allow you to reproduce the thesis PDF, [main.pdf](thesis/main.pdf).

## Citation

Please refer to the [CITATION.cff](CITATION.cff) file and refer to https://citation-file-format.github.io to extract the citation in a format of your choice.

## License

Unless specified otherwise below, this repository is licensed under the CC BY 4.0 license ([`LICENSE`](LICENSE) or https://creativecommons.org/licenses/by/4.0/).

---

- The [`sosaa/`](https://github.com/juntyr/sosaa-10618aa) submodule, which contains a snapshot of version SOSAA@10618aa, is licensed under the GPL-3.0 license ([`sosaa/LICENSE-GPL`](https://github.com/juntyr/sosaa-10618aa/blob/main/LICENSE-GPL) or https://www.gnu.org/licenses/gpl-3.0.html).

- The [`sosaa-data/experiments/`](sosaa-data/experiments/) folder, which contains the code of the experiments conducted for this project, is licensed under either of

  - Apache License, Version 2.0 ([`sosaa-data/experiments/LICENSE-APACHE`](sosaa-data/experiments/LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
  - MIT license ([`sosaa-data/experiments/LICENSE-MIT`](sosaa-data/experiments/LICENSE-MIT) or http://opensource.org/licenses/MIT)

  at your option.

- The [`sosaa-data/trajectories/`](https://github.com/juntyr/sosaa-trajectories-dataset) submodule, which contains the SOSAA trajectories dataset, is licensed under the CC0 1.0 license ([`sosaa-data/trajectories/LICENSE`](https://github.com/juntyr/sosaa-trajectories-dataset/blob/main/LICENSE) or https://creativecommons.org/publicdomain/zero/1.0/).

- The [`sosaa-gui/`](https://github.com/juntyr/sosaa-gui) submodule, which contains the graphical user interface for SOSAA, is licensed under the GPL-3.0 license ([`sosaa-gui/LICENSE-GPL`](https://github.com/juntyr/sosaa-gui/blob/main/LICENSE-GPL) or https://www.gnu.org/licenses/gpl-3.0.html).

- The [`thesis/`](thesis/) folder, which contains the Master's Thesis document, figures, and LaTex source code, is licensed under the CC BY 4.0 license ([`thesis/LICENSE`](thesis/LICENSE) or https://creativecommons.org/licenses/by/4.0/).
