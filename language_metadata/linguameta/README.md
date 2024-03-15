# LinguaMeta: Unified metadata for thousands of languages

This folder contains data related to the LREC-COLING 2024 paper *LinguaMeta: Unified metadata for thousands of languages*.

We make LinguaMeta available as a series of .json files for each language and language-script-locale combination, as well as a .tsv file. The structure of these files is described in more detail below.

## Structure of LinguaMeta

### .json files

This folder contains a directory for each BCP-47 code, which in turn contains directories for each associated script and locale. Unknown scripts and locales are represented by the placeholder string 'xxxx'.

Each language has two types of metadata files, stored at different levels in the directory:

* ``lang_metadata.json``: language-level metadata, stored in the language directory
* ``lang_loc_metadata.json``: metadata specific to a language-script-locale

The following metadata is stored at the language level (e.g. ``pa/lang_metadata.json``):

* Language codes (BCP-47, ISO 639-3, ISO 639-2b, deprecated BCP-47, Glottocode, Wikidata ID, GRN ID)
* Macrolanguage BCP-47 code (if applicable)
* Scope
* Language type
* Endangerment status
* Description
* Language names (including English names and endonyms)
* Language varieties

The remaining metadata is stored at the level of the language-script-locale (e.g. ``pa/guru/in/lang_loc_metadata.json``):

* Number of speakers
* Writing system
* Locale
* Official status (if applicable)
* Geolocation (latitude and longitude)

### .tsv file

The .tsv file is organized by BCP-47 code and is intended as an accessible summary of LinguaMeta.

Since speaker population information is stored in LinguaMeta by language-locale, the total speaker population for a language is calculated as the sum of the number of speakers in each locale. If a language has an available population statistic for a broader region (e.g. West Africa), we use that speaker count in the .tsv instead of a sum.

Note that the .tsv file does not include all of the information included in LinguaMeta. Specifically, the .tsv file excludes source information for each data point, extended language name metadata (aside from English names and endonyms), as well as extended script metadata (e.g. script use tags). This information is available in .json format only.

## Change requests

As our paper describes, gathering this information was a challenging process. We
did our best to ensure the correctness of the data, but we recognize that there
may be inaccuracies in the data. If you spot an inaccuracy or an error, please
raise an issue with the change. To help us incorporate fixes
quickly, please reference the source of your information. We also welcome issues to add additional information to the repository, e.g. adding endonyms or alternative names that are not yet included.

For corrections to information pulled in from an external repository (e.g. Glottolog, CLDR), please incorporate those changes upstream if possible, and then raise an issue here for the changes to be pulled in.
