# Square One Bias in NLP: Towards a Multi-Dimensional Exploration of the Research Manifold

This folder contains data related to the paper Square One Bias in NLP. As part of
a study investigating trends and popular directions in natural language processing (NLP) research,
we annotated the 461 research papers that were presented orally at ACL 2021 (the main NLP conference)
with information on whether they make contributions to 4 different dimensions of research (multilinguality, fairness or bias, efficiency, and interpretability)
as well as the languages and the metrics each paper uses for evaluation.

We make these annotations available in the form of a .csv file.

Each entry contains the following fields:

- *Paper name*: string; name of paper
- *Session*: string; session where paper was presented
- *ID*: string; short-form ID of the paper
- *URL*: string; URL of the paper in the ACL Anthology
- *Language(s)*: string
- *Main metric*: string
- *Other metrics*: string
- *Multilingual?*: boolean
- *Fairness or bias?*: boolean
- *Efficiency?*: boolean
- *Interpretability?*: boolean

## Change requests
We annotated the papers to the best of our knowledge. Nevertheless, there may be inaccuracies in the data. For instance,
some contributions may be difficult to assign to a specific dimension.

If you spot an inaccuracy or an error, please raise an issue or submit a PR with the change.

## Citation

If you found the annotations helpful, please consider citing them as follows:

```
@inproceedings{ruder-etal-2022-square,
    title = "Square One Bias in {NLP}: Towards a Multi-Dimensional Exploration of the Research Manifold",
    author = "Ruder, Sebastian  and
      Vuli{\'c}, Ivan  and
      S{\o}gaard, Anders",
    booktitle = "Findings of the Association for Computational Linguistics: ACL 2022",
    month = may,
    year = "2022",
    address = "Dublin, Ireland",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2022.findings-acl.184",
    doi = "10.18653/v1/2022.findings-acl.184",
    pages = "2340--2354",
    abstract = "The prototypical NLP experiment trains a standard architecture on labeled English data and optimizes for accuracy, without accounting for other dimensions such as fairness, interpretability, or computational efficiency. We show through a manual classification of recent NLP research papers that this is indeed the case and refer to it as the square one experimental setup. We observe that NLP research often goes beyond the square one setup, e.g, focusing not only on accuracy, but also on fairness or interpretability, but typically only along a single dimension. Most work targeting multilinguality, for example, considers only accuracy; most work on fairness or interpretability considers only English; and so on. Such one-dimensionality of most research means we are only exploring a fraction of the NLP research search space. We provide historical and recent examples of how the square one bias has led researchers to draw false conclusions or make unwise choices, point to promising yet unexplored directions on the research manifold, and make practical recommendations to enable more multi-dimensional research. We open-source the results of our annotations to enable further analysis.",
}
```
