# LinguaMeta: Unified metadata for thousands of languages

This folder contains data related to the LREC-COLING 2024 paper *[LinguaMeta: Unified metadata for thousands of languages](https://aclanthology.org/2024.lrec-main.921/)*.

## Structure of LinguaMeta

We make LinguaMeta available as a series of JSON files, as well as an overview TSV. The JSON version contains the full set of metadata; the TSV is provided for convenience and contains only the most important information, as discussed in more detail below.


### JSON files

The ``data`` folder contains a JSON file for each language, named according to its BCP-47 code (e.g. ``en.json`` for English, ``pa.json`` for Punjabi, ``zu.json`` for Zulu). Each JSON file contains metadata for the language as a whole followed by a repeated field ``language_script_locale``, which contains language metadata specific to a particular script and locale combination (e.g. Punjabi written in Gurmukhi script and spoken in India).

The structure of the language JSON files is as follows. Fields are absent when they are not filled except for unknown scripts and locales, which are represented by the placeholder string 'xxxx'.

* ``bcp_47_code``
* ``deprecated_bcp_47_code``
* ``iso_639_3_code``
* ``iso_639_2b_code``
* ``glottocode``
* ``wikidata_id``
* ``total_population``
* ``language_scope``
    * ``scope``
    * ``source``
* ``macrolanguage_bcp_47_code``
* ``individual_language_bcp_47_codes`` (repeated)
* ``endangerment_status``
    * ``endangerment``
    * ``source``
* ``language_description``
    * ``description``
    * ``source``
* ``name_data`` (repeated)
    * ``name``
    * ``bcp_47_code``
    * ``is_canonical``
    * ``source``
* ``language_script_locale`` (repeated)
    * ``script``
        * ``iso_15924_code``
        * ``is_canonical``
        * ``is_historical``
        * ``is_religious``
        * ``is_for_transliteration``
        * ``is_for_accessibility``
        * ``is_in_widespread_use``
        * ``has_official_status``
        * ``has_symbolic_value``
        * ``source``
    * ``locale``
        * ``iso_3166_code``
        * ``source``
    * ``speaker_data``
        * ``number_of_speakers``
        * ``source``
    * ``official_status``
        * ``has_official_status``
        * ``has_regional_official_status``
        * ``has_de_facto_official_status``
        * ``source``
    * ``geolocation``
        * ``latitude``
        * ``longitude``
        * ``source``

The ``data`` folder also contains a file ``locales.json``, which provides a mapping between ISO 3166 locale codes and the full name of the locale or region. It also provides mappings from a locale to its corresponding region, subregion, and regional group, if applicable. The structure of ``locales.json`` is as follows:

* ``locale_map`` (repeated)
    * ``locale``
        * ``locale_code``
        * ``locale_name``
        * ``locale_population``
            * ``population``
            * ``source``
    * ``region``
    * ``subregion``
    * ``regional_group``

### TSV file

The TSV file is organized by BCP-47 code (i.e. by language) and is intended as an accessible summary of LinguaMeta. The TSV **is not comprehensive**, as it lacks the following information:

* Source information
* Extended language name metadata (aside from English names and endonyms)
* Script use tags
* Official statuses researched by Google
* Geographic coordinates

This information is available in JSON format only.


## Limitations

1. LinguaMeta is not suitable for those looking for a comprehensive set of ISO 639 codes: we focus on living, spoken languages, and thus exclude many constructed, signed, and historical languages. 
    * For the comprehensive set of ISO 639 codes, visit the [ISO 639 Code Tables](https://iso639-3.sil.org/code_tables/639/data/all?title=ksb).
2. Not every field is complete for every language: e.g. only about 83% of languages in LinguaMeta have a value for speaker population, and other fields are more limited still. 
    * See Table 3 in the paper for more details about LinguaMeta's coverage by field.
3. LinguaMeta does not collate all information available in each data source: e.g. Glottolog contains academic publication information for many languages, which we do not include here. 
    * You can use the codes provided for each language (e.g. Glottocode, Wikidata ID) as a key to retrieve more information from individual sources.

## Notes on specific categories

### Speaker population

LinguaMeta provides two kinds of speaker population data: speaker population by locale, and total speaker population. The total speaker population is calculated from the sum of its populations broken down by locale. We recognize that this metadata category is prone to error, and performing such calculations may magnify errors in some cases. 

Since LinguaMeta includes locales as well as broader regions, we calculate total populations carefully to avoid double-counting speakers. If a language has available population statistics for broader regions (e.g. West Africa) in addition to locales (e.g. Senegal), we take the sum of all regional populations and the sum of all locale populations and choose the larger of the two sums.

To avoid a false sense of exactness, all speaker population data is rounded by order of magnitude:

* **0-100:** Reported as-is (no rounding)
* **100-1,000:** Rounded to the nearest 10
* **1,000-10,000:** Rounded to the nearest 100
* **10,000-100,000:** Rounded to the nearest 1K
* **100,000-1,000,000:** Rounded to the nearest 10K
* **1,000,000-10,000,000:** Rounded to the nearest 100K
* **10,000,000+:** Rounded to the nearest 1M

### Scope

LinguaMeta includes both individual languages and macrolanguages, following ISO 639-3 convention where both are identified with separate codes. The two possible values of the ``scope`` field are:

* ``LANGUAGE``: An individual language
    * May be part of a larger macrolanguage
* ``MACROLANGUAGE``: A broader language group or continuum
    * Subsumes two or more individual languages

On a more granular level, individual languages are often comprised of several language *varieties*, which are not included in the ISO 639-3 standard. Language varieties are currently not represented in LinguaMeta.

### Endangerment status

LinguaMeta uses the six-point endangerment scale developed for the UNESCO Atlas of the World's Languages (Moseley 2010). In our JSON files, the possible values of the ``endangerment`` field are:

* ``SAFE``: Safe; not endangered
* ``VULNERABLE``: Vulnerable
* ``DEFINITE``: Definitely endangered
* ``SEVERE``: Severely endangered
* ``CRITICAL``: Critically endangered
* ``EXTINCT``: Extinct; no longer spoken by L1 speakers

See Moseley (2010) for a more detailed description of this scale and how its values are determined. 

### Script use tags

LinguaMeta uses a set of tags to indicate the context(s) that a writing system is used in for a particular language. We identify the following contexts, which are non-exhaustive and may be overlapping:

* ``is_canonical``: Scripts that have a current,
significant cultural life for the language
    * Exactly one script is
designated as the canonical script for each
language-locale combination in our database
* ``is_historical``: Scripts that were previously,
but are no longer, used for the language
* ``is_religious``: Scripts that are used primarily
in religious or liturgical contexts
* ``is_for_transliteration``: Scripts that are not canonical for a language, but are used in certain contexts (e.g. in smartphone keyboards) for transliteration or text input
* ``is_for_accessibility``: Scripts that are used to accommodate disabled users (e.g. Braille)
* ``is_in_widespread_use``: Scripts that are not designated as “canonical”, but are in widespread community use
* ``has_official_status``: Scripts that are officially
used to write the language, as designated by
a governing body
* ``has_symbolic_value``: Scripts that have particular symbolic value for a language community (e.g. as a marker of community identity)

## Sources and licensing

LinguaMeta compiles language metadata from a variety of sources, each with their own open-access license. Each source is provided below along with its respective licensing information.

| JSON value          | Source                                     | License type      | Link                                                                                |
|---------------------|--------------------------------------------|-------------------|-------------------------------------------------------------------------------------|
| ``CLDR``            | Unicode CLDR                               | non-standard      | [License](https://www.unicode.org/license.txt)                                      |
| ``GLOTTOLOG``       | Glottolog                                  | CC BY 4.0         | [Site homepage](https://glottolog.org/)                                             |
| ``GOOGLE_RESEARCH`` | Language research conducted at Google (including by present authors) | CC BY 4.0         | [License](https://github.com/google-research/url-nlp/blob/main/LICENSE)             |
| ``IETF``            | IETF                                       | CC BY 4.0         | [License](https://trustee.ietf.org/assets/the-ietf-trusts-copyrights-and-licenses/) |
| ``ISO_639``         | SIL ISO 639 Registration Authority         | non-standard      | [Terms of use](https://iso639-3.sil.org/code_tables/download_tables#termsofuse)     |
| ``WIKIDATA``        | Wikidata                                   | CC0, CC BY-SA 3.0 | [Copyright info](https://www.wikidata.org/wiki/Wikidata:Copyright)                  |
| ``WIKIPEDIA``       | Wikipedia                                  | CC BY-SA 4.0      | [Copyright info](https://en.wikipedia.org/wiki/Wikipedia:Copyrights)                |
| ``WIKTIONARY``      | Wiktionary                                 | CC BY-SA 4.0      | [Copyright info](https://en.wiktionary.org/wiki/Wiktionary:Copyrights)              |

## Change requests

As our paper describes, gathering this information was a challenging process. We
did our best to ensure the correctness of the data, but we recognize that there
may be inaccuracies in the data. If you spot an inaccuracy or an error, please
raise an issue with the change. To help us incorporate fixes
quickly, please reference the source of your information. We also welcome issues to add additional information to the repository, e.g. adding endonyms or alternative names that are not yet included.

For corrections to information pulled in from an external repository (e.g. Glottolog, CLDR), please incorporate those changes upstream if possible, and then raise an issue here for the changes to be pulled in.

## How to cite

If you found this data helpful, please consider citing it as follows:

```
@InProceedings{ritchie-etal-2024-linguameta-unified,
  author    = {Ritchie, Sandy and van Esch, Daan and Okonkwo, Uche and Vashishth, Shikhar and Drummond, Emily},
  title     = {LinguaMeta: Unified metadata for thousands of languages},
  booktitle      = {Proceedings of the Joint International Conference on Computational Linguistics, Language Resources and Evaluation},
  month          = {May},
  year           = {2024},
  address        = {Torino, Italy},
  publisher      = {European Language Resources Association},
  pages     = {10530–-10538},
  abstract  = {We introduce LinguaMeta, a unified resource for language metadata for thousands of languages, including language codes, names, number of speakers, writing systems, countries, official status, and geographic coordinates. The resources are drawn from various existing repositories and supplemented with our own research. Each data point is tagged for its origin, allowing us to easily trace back to and improve existing resources with more up-to-date and complete metadata. The resource is intended for use by researchers and organizations who aim to extend technology to thousands of languages.},
  url       = {https://aclanthology.org/2024.lrec-main.921},
}
```

## Citations

Moseley, Christopher (ed.). 2010. *Atlas of the World's Languages in Danger.* Paris: UNESCO.