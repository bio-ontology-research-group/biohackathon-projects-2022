---
title: 'MOWL: machine learning library with ontologies'
tags:
  - Machine Learning
  - OWL ontologies
  - Knowledge representation
authors:
  - name: Fernando Zhapa
    orcid: 0000-0002-0710-2259
    affiliation: 1
  - name: Maxat Kulmanov
    orcid: 
    affiliation: 1
  - name: Dominik Martinát
    orcid: 0000-0001-6611-7883
    affiliation: 2
  - name: Nelson Quinones-Virgen
    orcid: 0000-0002-5037-0443
    affiliation: 3
  - name: Robert Hoehndorf
    orcid: 0000-0001-8149-5890
    affiliation: 1
affiliations:
 - name: Computational Bioscience Research Center, Computer Electrical and Mathematical Sciences & Engineering Division, King Abdullah University of Science and Technology, Thuwal, Saudi Arabia
   index: 1
 - name: Faculty of Science, Palacký University, Olomouc, Czech Republic
   index: 2
 - name: Information Centre for Life Sciences, ZB Med, Cologne, Germany
   index: 3

date: 11 November 2022
bibliography: paper.bib
authors_short: Zhapa et al. (2022)
group: MOWL
event: BioHackathon Europe 2022
---

# Introduction or Background

mOWL is a software library that incorporates several methods to
generate embeddings of entities in ontologies. The current state of
mOWL contains several methods categorized into graph-based, syntactic,
and semantic models [@Kulmanov:2020]. We provide
benchmark datasets describing biological phenomena such as
protein-protein interactions and gene-disease associations. Moreover,
we provide Jupyter notebooks tutorials describing how mOWL can be used
to implement some of the current methods. 

In this edition, the outcomes consisted on implementing the transformation of OWL ontologies ALC axioms into lists of entities that later can be transformed into PyTorch datasets. Furthermore, in order to show the use of mOWL,  we worked on the implementation of current machine learning models that used ontologies.

In terms of usability, we performed some user testing with people that met the library for the first time. Finally, we explored the compatibility across different operative systems.


# ALC Dataset and FALCON


# DeepGOZero implementation

We implemented DeepGOZero [@Kulmanov:2002], a model that performs protein-fuction prediction for functions that are not annotated with proteins in the training set. To implement this model in mOWL, we first transformed all the input data into a mOWL dataset that had the following structure:

* Training ontology: 
  * Gene Ontology
  * Axioms of the form $$\exists has\_function. go\_class (protein)$$, which encodes protein function annotations. 
  * Axioms of the form $has\_interpro (protein, interpro)$, which encodes interpro features for proteins.
* Validation ontology:
  * Axioms of the form $\exists has\_function. go\_class (protein)$
  * Axioms of the form $has\_interpro (protein, interpro)$

* Testing ontology:
  * Axioms of the form $\exists has\_function. go\_class (protein)$
  * Axioms of the form $has\_interpro (protein, interpro)$

Secondly, since DeepGOZero utilized another model called ELEmbeddings, we replaced all that portion of code the mOWL implementation of ELEmbeddings.

In the end, we have an implementation where the data is better structured and easier to understand.

## Usability and cross-platform compatibility


# Discussion and/or Conclusion

# Future work

Future work in mOWL will consist on implementing an inference module that allows to score the plausability of a particular axiom given a trained model.


# Jupyter notebooks, GitHub repositories and data repositories

The source code of MOWL is accesible via our [mOWL GitHub repository](https://github.com/bio-ontology-research-group/mowl). The corresponding documentation can be found at [mOWL ReadTheDocs website](https://mowl.readthedocs.io/en/latest/).

The links for the outcomes of this year are in the following:

* ALC dataset and FALCON: [link to the documentation]()
* DeepGOZero example: [link to the documentation]()
* Windows compatibility test: [link to the documentation]()


# Acknowledgements

This work was done during the BioHackathon Europe 2022 organized by ELIXIR in November 2022. We thank the organizers and fellow participants. mOWL development is supported by the Bio-Ontology Research Group in KAUST.

# References

Leave thise section blank, create a paper.bib with all your references.
