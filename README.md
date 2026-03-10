**[Türkçe](README.tr.md) | [English](README.md)**

# Stream-Graph: A Modernized Conda Environment (v1.0.0)

[![Travis Status](https://travis-ci.org/ysig/stream_graph.svg?branch=master)](https://travis-ci.org/ysig/stream_graph)
[![CircleCI Status](https://circleci.com/gh/ysig/stream_graph/tree/master.svg?style=shield)](https://circleci.com/gh/ysig/stream_graph/tree/master)
[![Appveyor status](https://ci.appveyor.com/api/projects/status/kqwkk8khh6btkaep?svg=true)](https://ci.appveyor.com/project/ysig/stream-graph)

> **Note:** This is a forked repository providing a modernized and reproducible Conda environment for the original `stream_graph` library. The build status badges above refer to the original repository and may not reflect the current state.

This project revives the powerful `stream_graph` library, originally developed by Yiannis Siglidis et al., by resolving critical dependency issues that prevented it from running in modern Python environments. This version, re-packaged as **v1.0.0**, provides a stable, easy-to-install Conda setup, allowing researchers and developers to once again leverage this library for temporal network analysis.

---

## About Stream Graphs

A Stream Graph is a graph whose nodes and links appear and disappear through time. It is a time-inclusive generalization of a static graph, formally defined in the paper:

*   **Stream graphs and link streams for the modeling of interactions in complex systems**  
    *Matthieu Latapy, Tiphaine Viard, Clémence Magnien.*  
    [[arXiv:1710.04177]](https://arxiv.org/abs/1710.04177)

This library is designed for the analysis of the temporal dimension of evolving networks, such as communication dynamics in social media.

## Modernization Details (v1.0.0)

The original `stream_graph` library was developed several years ago and relies on older versions of core Python data science libraries. Attempts to run it in a modern environment (e.g., Python 3.7+ with recent versions of Pandas) result in `AttributeError` and `ImportError` exceptions due to API changes in its dependencies.

This fork addresses these issues by creating a self-contained Conda environment with precisely version-pinned libraries, ensuring full compatibility and reproducibility.

**Key Fixes:**
*   **`pandas` Version:** Pinned to `pandas==0.24.2` to resolve `AttributeError: 'BlockManager' object has no attribute '_mgr'` and `FutureWarning` messages. The original library was not compatible with Pandas 1.0+ APIs.
*   **`jinja2` Version:** Pinned to `jinja2==3.0.3` to fix `ImportError: cannot import name 'contextfilter' from 'jinja2'`. The `contextfilter` was deprecated and removed in newer versions.
*   **Comprehensive Environment:** The `environment.yml` file now includes all necessary dependencies (`bokeh`, `networkx`, `wordcloud`, etc.) to run the included tutorials out-of-the-box with a single command.

## Installation

The recommended and easiest way to set up this project is by using the Anaconda or Miniconda distribution.

### Prerequisites

*   Anaconda or Miniconda
*   `git` command-line tool

### Steps

1.  **Clone the Repository:**
    Open your terminal or command prompt and clone this repository.
    ```bash
    git clone https://github.com/YOUR_USERNAME/stream_graph_modernizated.git
    cd stream_graph_modernizated
    ```
    *(Replace `YOUR_USERNAME` with your actual GitHub username)*

2.  **Create and Activate the Conda Environment:**
    This single command reads the `environment.yml` file and automatically creates a new Conda environment named `sg_env` with all the correct library versions.
    ```bash
    conda env create -f environment.yml
    ```
    Once the environment is created, activate it:
    ```bash
    conda activate sg_env
    ```

3.  **Verify Installation:**
    Your prompt should now be prefixed with `(sg_env)`. You are ready to run the project.

## Usage: Running the Tutorial

The repository includes the original tutorial from the ODYCCEUS summer school, which demonstrates the core functionalities of the library.

1.  **Launch Jupyter Notebook:**
    With the `sg_env` environment active, navigate to the project directory and start Jupyter:
    ```bash
    jupyter notebook
    ```

2.  **Open the Notebook:**
    Your web browser will open a new tab. Navigate to `tutorials/ODYCCEUS/` and open the `tutorial.ipynb` notebook.

3.  **Run the Analysis:**
    You can now run the cells in the notebook to replicate the original analysis.

---

## Original Project Information

*   **Original Source:** https://github.com/ysig/stream_graph
*   **Original Documentation:** https://ysig.github.io/stream_graph/doc/
*   **Lab Website:** http://www.complexnetworks.fr/

### Citation

If you use this library in your research, please cite the original paper:
```bibtex
@article{latapy2018stream,
  title={Stream graphs and link streams for the modeling of interactions in complex systems},
  author={Latapy, Matthieu and Viard, Tiphaine and Magnien, Cl{\'e}mence},
  journal={arXiv preprint arXiv:1710.04177},
  year={2018}
}
```

### Original Authors

This package was originally developed by researchers of the Complex Networks team, within the Computer Science Laboratory of Paris 6 (LIP6), for the ODYCCEUS project.

*   Yiannis Siglidis: `<Yiannis.Siglidis@lip6.fr>`
*   Robin Lamarche-Perrin: `<Robin.Lamarche-Perrin@lip6.fr>`


### Modernization Patch

Within the scope of the V1.0.0 version of this package, the library has been reusable as of 2025.

*   Talha Göktuğ Gönen `<talhagoktug.gonen@nisantasi.edu.tr>`


### License

`stream_graph` is free software under the terms of the **GNU General Public License v3.0**.
