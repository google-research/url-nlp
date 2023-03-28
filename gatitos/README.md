# GATITOS Multilingual Lexicon

The GATITOS (Google's Additional Translations Into Tail-languages: Often Short)
dataset is a high-quality, multi-way parallel dataset of tokens and short
phrases, intended for training and improving machine translation models. Experiments on this dataset and Panlex focusing on unsupervised translation in a 208-language model can be found in [BiLex Rx: Lexical Data Augmentation for Massively Multilingual Machine Translation](https://arxiv.org/pdf/2303.15265.pdf).

### About the Data and Data Collection

This dataset consists in 4,000 English segments (4,500 tokens) that have been
translated into each of 26 low-resource languages, as well as three
higher-resource pivot languages (es, fr, hi). All translations were made
directly from English, with the exception of Aymara, which was translated from
the Spanish.

This dataset contains primarily short segments: 93% single tokens, and only 23
sentences (0.6%) have over 5 tokens. As such it is best thought of as a
multilingual lexicon, rather than a parallel training corpus. The source text is
frequent words in the English Language, along with some common phrases and short
sentences. Care has been taken to ensure that they include good coverage of
numbers, months, days of the week, swadesh words, and names of the languages
themselves (including the endonym).

Single tokens are remarkably fickle to translate because of the common issue of
polysemy. This dataset unfortunately usually only provides one translation per
source token, but some languages, like Konkani, sometimes provide several.

| BCP-47 code | Language Name | Endonym      | Alternate names       | script |
| ----------- | ------------- | ------------ | --------------------- | ------ |
| ak          | Twi           | Twi          | Akan (Fante, Ashanti, | Latn   |
:             :               :              : Akuapem, etc.)        :        :
| as          | Assamese      | অসমীয়া      | Asamiya, Asomiya      | Beng   |
| ay          | Aymara        | Aymar aru    |                       | Latn   |
| bho         | Bhojpuri      | भोजपुरी      |                       | Deva   |
| bm          | Bambara       | Bámánánkán   |                       | Latn   |
| ckb         | Kurdish       | سۆرانی       | Central Kurdish       | Arab   |
:             : (Sorani)      :              :                       :        :
| doi         | Dogri         | डोगरी        |                       | Deva   |
| dv          | Dhivehi       | ދިވެހި       | Maldivian, Divehi     | Thaa   |
| ee          | Ewe           | Eʋegbe       | Eve, Anlo, Anwona     | Latn   |
| es          | Spanish       | español,     | Castilian             | Latn   |
:             :               : castellano   :                       :        :
| fr          | French        | français     |                       | Latn   |
| gn          | Guarani       | avañeʼẽ      | Guaraní               | Latn   |
| gom         | Konkani       | कोंकणी       |                       | Deva   |
| hi          | Hindi         | हिन्दी       |                       | Deva   |
| ilo         | Ilocano       | Iloko        | Iloko, Iluko, Ilokano | Latn   |
| kri         | Krio          | Krio         | Sierra Leonean Creole | Latn   |
| lg          | Luganda       | Oluganda     | Ganda                 | Latn   |
| ln          | Lingala       | Lingála      | Ngala                 | Latn   |
| lus         | Mizo          | Mizo ṭawng   | Lushai, Duhlian       | Latn   |
| mai         | Maithili      | मैथिली       |                       | Deva   |
| mni-Mtei    | Meiteilon     | ꯃꯤꯇꯩꯂꯣꯟ      | Meitei, Meetei,       | Mtei   |
:             : (Manipuri)    :              : Meitheilon, Meeteilon :        :
| nso         | Sepedi        | Sepedi       | Pedi, Northern Sotho  | Latn   |
| om          | Oromo         | Afaan Oromoo | Oromiffa, Oromigna,   | Latn   |
:             :               :              : Afaan Oromoo          :        :
| qu          | Quechua       | Runa Simi    |                       | Latn   |
| sa          | Sanskrit      | संस्कृतम्    |                       | Deva   |
| ti          | Tigrinya      | ትግርኛ         | Tigrigna              | Ethi   |
| ts          | Tsonga        | Xitsonga     | Xitsonga              | Latn   |
| ff          | Fulfulde      | [many]       | Fula, Fulah, Fulbe,   | Latn   |
:             :               :              : Fulani Pular, Pulaar  :        :
| kl          | Kalaallisut   | Kalaallisut  | Greenlandic           | Latn   |

Please note that the language name can be a point of considerable tension, and
there is rarely a "right" name for a language! This said, here are some
non-exhaustive notes that went into the names in the second column above, based
on conversations with speakers:

*   **ckb:** *Central Kurdish* is a more academic name that may not be as widely
    known to speakers of the language, so *Sorani* is preferred -- though they
    are both acceptable.
*   **dv:** There is not a consistent romanization of this language, and both
    *Divehi* and *Dhivehi* are common. The first consonant in this language is a
    dental, non-aspirated *d*. When transliterating Indian language names there is
    no standard about how to represent this sound. In the south, "dh" usually
    refers to the dental consonant; in the North, it just as often refers to the
    aspirated one. However, in both cases, it is common that "d" alone would
    represent the retroflex consonant, so it is possible that *Divehi* would be
    mispronounced more often.
*   **gom:** Technically, `gom` is the code for *Goan* Konkani only. Other
    varieties of Konkani, like Mangalore Konkani (which oddly enough does not
    have an ISO code), are mutually unintelligible! There is certainly dispute
    about whether to treat Konkani as one language or not.
*   **ilo:** Native speakers give a variety of different answers around the
    correct name. Some say that *Ilocano* is more formal, whereas *Ilokano* is
    more informal; some say that both of these actually refer to the people, and
    that *Iloko* is the only correct term for the language.
*   **lg:** Speakers usually refer to this language as "Luganda"; linguists sometimes call it
    "Ganda", but like Sepedi, this is not usually used by people
    familiar with the language.
*   **lus:** There is agreement that *Lushai* is an obsolete colonial name and
    should not be used. *Mizo* is the preferred name.
*   **mni-Mtei:** The conventional and most common name for this language is
    *Manipuri*. However, in reality, this is only the language of one of the
    many ethnicities in Manipur, so that name can be seen as offensive to some.
    Therefore, we use the endonym *Meiteilon*, with the conventional name
    (Manipuri) in parentheses.
*   **nso:** Although a linguist might say that Sepedi is a dialect of Northern
    Sotho, speakers often say that they call the whole language Sepedi, and that
    *Northern Sotho* has offensive colonial overtones. Others, however, may
    disagree with this. The endonym *Sesotho sa Leboa* is not uncommon. There is
    agreement that no-one uses *Pedi*.
*   **qu:** These translations are technically in *Southern* Quechua. However,
    this is a point of some contention. Some will opine that "Quechua" is not a
    language but a family of languages. Others, however, say that they all feel
    like one language, and that the regional differences are slight, and it's
    easy for Peruvians, Bolivians, and even Ecuadorians to understand each
    other. The majority opinion among the naive speakers we talked to seemed to
    be closer to the latter, so we have opted for the name "Quechua".
*   **ti:** In Tigray *Tigrigna* is the most common Romanization, and in Eritrea
    *Tigrinya* is.

Special note on Bantu languages: Bantu language names have a special noun-class
prefix for languages, like <i>xi</i>Tsonga, <i>se</i>Pedi, <i>ki</i>Swahili, <i>isi</i>Zulu,
<i>lu</i>Ganda, <i>si</i>Swati, <i>isi</i>Ndebele, <i>tshi</i>Venda, and so on. However, there is no
pattern as to whether this prefix is used in the conventional English form of
the name. For instance, Xhosa usually leaves off the <i>isi-</i> in English, whereas
Lingala almost never leaves off the <i>li-</i>. Others, like (xi)Tsonga, seem to be
frequently used in both forms. Linguistic resources occasionally strip the
prefixes, yielding names like "Ganda", "Pedi" and so on, perhaps out of a desire
for consistent handling of the noun class prefix. (Even the *ba* in *Bantu* is
such a prefix, so these languages are sometimes called the *Ntu* languages!)


### Contact

Please contact icaswell꩜google.com if you have suggestions or corrections. This
repository may be updated sporadically with corrections or additional
translations.

## License

This data is released with the `CC-BY-4.0` license.