# Writing System and Speaker Metadata for 2,800+ Language Varieties

This folder contains data related to the LREC 2022 paper *Writing System and
Speaker Metadata for 2,800+ Language Varieties*.

We make this data available in the form of a .tsv file.

**Note:** We are no longer making updates to this repository. Our new canonical source for language metadata is LinguaMeta (available [here](https://github.com/google-research/url-nlp/tree/main/linguameta)) which should be used instead.

## Change requests

As our paper describes, gathering this information was a challenging process. We
did our best to ensure the correctness of the data, but we recognize that there
may be inaccuracies in the data. If you spot an inaccuracy or an error, please
raise an issue or submit a PR with the change. To help us incorporate fixes
quickly, please reference the source of your information. Of course, please feel
free to raise issues or submit PRs to add information on additional languages
as well. We also welcome issues or PRs to add additional information on existing
languages, e.g. adding endonyms or alternative names that are not yet included.

For fields that were pulled in from Glottolog, please incorporate changes
upstream and then raise an issue or submit a PR for the changes to be pulled in.

Disclaimer: This is not an officially supported Google product.

## Citation

If you found this data helpful, please consider citing it as follows:

```
@InProceedings{vanesch-EtAl:2022:LREC,
  author    = {van Esch, Daan  and  Lucassen, Tamar  and  Ruder, Sebastian  and  Caswell, Isaac  and  Rivera, Clara},
  title     = {Writing System and Speaker Metadata for 2,800+ Language Varieties},
  booktitle      = {Proceedings of the Language Resources and Evaluation Conference},
  month          = {June},
  year           = {2022},
  address        = {Marseille, France},
  publisher      = {European Language Resources Association},
  pages     = {5035--5046},
  abstract  = {We describe an open-source dataset providing metadata for about 2,800 language varieties used in the world today. Specifically, the dataset provides the attested writing system(s) for each of these 2,800+ varieties, as well as an estimated speaker count for each variety. This dataset was developed through internal research and has been used for analyses around language technologies. This is the largest publicly-available, machine-readable resource with writing system and speaker information for the world's languages. We analyze the distribution of languages and writing systems in our data and compare it to their representation in current NLP. We hope the availability of this data will catalyze research in under-represented languages.},
  url       = {https://aclanthology.org/2022.lrec-1.538}
}
```
