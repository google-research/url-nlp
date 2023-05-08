# GATITOS Multilingual Lexicon

The GATITOS (Google's Additional Translations Into Tail-languages: Often Short)
dataset is a high-quality, multi-way parallel dataset of tokens and short
phrases, intended for training and improving machine translation models. Experiments on this dataset and Panlex focusing on unsupervised translation in a 208-language model can be found in [BiLex Rx: Lexical Data Augmentation for Massively Multilingual Machine Translation](https://arxiv.org/pdf/2303.15265.pdf).

### About the Data and Data Collection

This dataset consists in 4,000 English segments (4,500 tokens) that have been
translated into each of 113 languages, 110 of which are low-resource, and three
of which are mid-high resource (es, fr, hi). All translations were made
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
polysemy. Some languages in this dataset only provide one translation per
source token; others provide multiple translations. When multiple translations
are given, they are broken up into multiple lines. Therefore, you can get the
average number of translations per token by looking at the number of lines in
the file versus the number of deduplicated English lines in the file. The three
languages with the most average translations per English token are Betawi,
Kachin, and Occitan, each with over 1.5 on average.

Sometimes translators have left annotations like "pike (verb)", "او (مونث)", "фамили(я)", "أسوأ(repeated)" etc..
Wolof is particularly noticeable in this regard, with notes like "xont (verb) which means to feed an animal". Several languages also give definitions instead of translations for some words, e.g. Tok Pisin translation of mole" to "wanpela liklik animal we i save stap long hol long graun".


| BCP-47 code | Language Name | Endonym      | Alternate names       | script |
| ----------- | ------------- | ------------ | --------------------- | ------ |
| aa       | Afar |  Qafar | | Latn
| ace      | Achenese |  Aceh | Achinese | Latn
| ach      | Acholi |  Acholi | | Latn
| ady      | Adyghe |  Черкес | West Circassian | Cyrl
| aeb      | Tunisian Arabic |  اللغة العربيّة التونسيّة | | Arab
| ak       | Twi           | Twi          | Akan (See note below)  | Latn   |
| apd-SD   | Sudanese Arabic |  عربي سوداني |  | Arab
| arn      | Mapudungun |  Mapudungun | Mapuche | Latn
| arz      | Egyptian Arabic |  اللهجة المصرية | Masri | Arab
| as       | Assamese      | অসমীয়া      | Asamiya, Asomiya      | Beng   |
| awa      | Awadhi |  अवधी | | Deva
| ay       | Aymara        | Aymar aru    |                       | Latn   |
| ayl      | Libyan Arabic |  العربية الليبية | | Arab
| ba       | Bashkir |  Башҡорт | | Cyrl
| bal      | Baluchi |  بلوچی |  Balochi | Arab
| ban      | Balinese |  Basa Bali | | Latn
| bbc      | Batak Toba |  Batak Toba | Toba Batak | Latn
| ber      | Tamazight (Tifinagh script) |  ⵜⴰⵎⴰⵣⵉⵖⵜ | Berber Languages | Tfng
| ber-Latn | Tamazight (Latin Script) |  Tamaziɣt | the Berber languages | Latn
| bew      | Betawi |  Betawi | Betawi Malay, Jakartan Malay, Batavian Malay | Latn
| bho      | Bhojpuri      | भोजपुरी      |                       | Deva   |
| bik      | Central Bikol |  Sentral Bikol |  Bikol Naga; Bikol | Latn
| bm       | Bambara       | Bámánánkán   |                       | Latn   |
| bo       | Tibetan |  བོད་མི།; བོད་ཀྱི།; བོད་སྐད།; བོད་ཡིག། | Lhasa Tibetan, Standard Tibetan | Tibt
| br       | Breton |  brezhoneg | | Latn
| brx      | Bodo |  बोडो | Boro | Deva
| bts      | Batak Simalungun |  Bahasa Simalungun | Simalungun | Latn
| bug      | Buginese |  basa Ugi | Bugis | Latn
| ce       | Chechen |  Нохчийн | | Cyrl
| chk      | Chuukese |  Trukese | Trukese | Latn
| chm      | Meadow Mari |  олык марий | Eastern Mari | Cyrl
| ckb      | Kurdish  (Sorani)   | سۆرانی       | Central Kurdish       | Arab   |
| cnh      | Hakha Chin |  Laica | Laiholh | Latn
| crs      | Seselwa Creole French |  kreol seselwa | Seychellois Creole, kreol| Latn
| ctg      | Chittagonian |  Chittagonian | | Beng
| cv       | Chuvash |  Чăваш | | Cyrl
| doi      | Dogri         | डोगरी        |                       | Deva   |
| dv       | Dhivehi       | ދިވެހި       | Maldivian, Divehi     | Thaa   |
| dyu      | Dyula |  Julakan | Dioula, Jula| Latn
| dz       | Dzongkha |  རྫོང་ཁ | | Tibt
| ee       | Ewe           | Eʋegbe       | Eve, Anlo, Anwona     | Latn   |
| es       | Spanish       | español, castellano    | Castilian             | Latn   |
| fa-AF    | Dari |  دری | | Arab
| ff       | Fulfulde      | [many]       | Fula, Fulah, Fulbe, Fulani, Pular, Pulaar | Latn   |
| fo       | Faroese |  Føroysk | | Latn
| fr       | French        | français     |                       | Latn   |
| gaa      | Ga |  Gã |  | Latn
| gn       | Guarani       | avañeʼẽ      | Guaraní               | Latn   |
| gom      | Konkani       | कोंकणी       |                       | Deva   |
| hi       | Hindi         | हिन्दी       |                       | Deva   |
| hil      | Hiligaynon |  Hiligaynon | | Latn
| iba      | Iban |  Iban | | Latn
| ilo      | Ilocano       | Iloko        | Iloko, Iluko, Ilokano | Latn   |
| iu       | Inuktitut |  ᐃᓄᒃᑎᑐᑦ | Eastern Canadian Inuktitut | Cans
| jam      | Jamaican Patois |  Jamayiken kreyòl angle |  Patwah, Jamaican Creole English| Latn
| kaa      | Kara-Kalpak |  Қарақалпақ; Қарақалпақша | Qaraqalpaq | Cyrl
| kac      | Kachin |  Jinghpaw | Jingpho | Latn
| kbd      | Kabardian |  Къэбэрдей; Адыгэ | East Circassian | Cyrl
| kha      | Khasi |  khasi | | Latn
| kl       | Kalaallisut   | Kalaallisut  | Greenlandic           | Latn   |
| kri      | Krio          | Krio         | Sierra Leonean Creole | Latn   |
| ktu      | Kituba |  Kituba | | Latn
| lg       | Luganda       | Oluganda     | Ganda                 | Latn   |
| ln       | Lingala       | Lingála      | Ngala                 | Latn   |
| lus      | Mizo          | Mizo ṭawng   | Lushai, Duhlian       | Latn   |
| mad      | Madurese |  Madurâ | | Latn
| mai      | Maithili      | मैथिली       |                       | Deva   |
| mak      | Makasar |  Mangkasara | Makassarese, Makassar, Macassar | Latn
| meo      | Kedah Malay |  Siti | | Latn
| mfe      | Morisien |  Morisien | Mauritian Creole | Latn
| mh       | Marshallese |  Majol | Ebon | Latn
| min      | Minangkabau |  Minangkabau | | Latn
| mni-Mtei | Meiteilon (Manipuri)    | ꯃꯤꯇꯩꯂꯣꯟ      | Meitei, Meetei, Meitheilon, Meeteilon     | Mtei   |
| ms-Arab  | Malay (Jawi script) |  ملايو | | Arab
| mwr      | Marwari |  मारवाड़ी | Marwadi; Merwari, Mewari (usually ref. dialects) | Deva
| nd       | North Ndebele |  IsiNdebele | Ndebele, isiNdebele saseNyakatho, Zimbabwean Ndebele | Latn
| new      | Newari |  नेवाः | Nepal Bhasa, Newar| Deva
| nhe      | Eastern Huasteca Nahuatl |  Nahuatlajtoli Kuextekan ikisayo | | Latn
| nr       | South Ndebele |  Isindebele | Transvaal Ndebele | Latn
| nso      | Sepedi        | Sepedi       | Pedi, Northern Sotho  | Latn   |
| nv       | Navajo |  Diné; Naabeehó | Navaho | Latn
| oc       | Occitan |  Occitan | Provençal | Latn
| om       | Oromo         | Afaan Oromoo | Oromiffa, Oromigna, Afaan Oromoo  | Latn   |
| os       | Ossetian |  Ирон | Iron, Ossetic| Cyrl
| pa-Arab  | Lahnda Punjabi (Pakistan) |  لہندا پنجابی | | Arab
| pam      | Pampanga |  Kapampangan | Kapampangan | Latn
| pcm      | Nigerian Pidgin |  Naijá, Pidgin for Nigerian | Naijá, Pijin, Broken| Latn
| qu       | Quechua       | Runa Simi    |                       | Latn   |
| quc      | K'iche' |  K'iche' | Quiché | Latn
| rhg-Latn | Rohingya |  Ruháingga | | Latn
| rom      | Romani |  Rromani ćhib | Romany, Romanes, Roma | Latn
| sa       | Sanskrit      | संस्कृतम्    |                       | Deva   |
| sah      | Yakut |  Саха | Yakutian, Sakha, Saqa, Saxa | Cyrl
| scn      | Sicilian |  Sicilianu | | Latn
| se       | Northern Sami |  davvisámegiella | | Latn
| shn      | Shan |  တႆး; လိၵ်ႈတႆး | | Mymr
| skr      | Saraiki |  سرائیکی |Multani | Arab
| tcy      | Tulu |  ತುಳು | | Knda
| tet      | Tetum |  Tetun | | Latn
| ti       | Tigrinya      | ትግርኛ         | Tigrigna              | Ethi   |
| tn       | Tswana |  Setswana |Setswana | Latn
| to       | Tongan |  Tonga | | Latn
| tpi      | Tok Pisin |  Tok Pisin | New Guinea Pidgin | Latn
| ts       | Tsonga        | Xitsonga     | Xitsonga              | Latn   |
| udm      | Udmurt |  Удмурт кыл | | Cyrl
| ve       | Venda |  Tshivenḓa | Tshivenda, Setswetla | Latn
| vec      | Venetian |  Veneto | | Latn
| war      | Waray |  Waray | Waray-Waray | Latn
| wo       | Wolof |  Wolof | | Latn
| yua      | Yucateco |  Maayat'aan | Yucatec Maya | Latn
| yue      | Cantonese |  廣東話 | Yue Chinese (technically a superset) | Hant
| zap      | Zapotec |  Diidxazá |  | Latn
| zza      | Zaza |  Kirmanckî; Kirdkî; Dimilî | Dimli | Latn

Please note that the language name can be a point of considerable tension, and
there is rarely a "right" name for a language! This said, here are some
non-exhaustive notes that went into the names in the second column above, based
on conversations with speakers:

*   **ak:** Calling this language "Twi" instead of "Akan" here is reflective of
    the corresponding translation models active on Google Translate. These are
    likely to mix different Akan dialects, including Twi proper, Fante, Akuapem Twi, etc.. Therefore, from a linguistic perspective, one would call this "Akan" and use the corresponding code "ak". However, this is a more academic word for the language; according to native speaker consultants, "Akan" is usually used to describe the ethnic group rather than the language, so they suggested simply calling this "Twi", which is most likely accurate for the large majority of model outputs.
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
*   **zap:** Linguists usually talk about the Zapotec *languages*, rather than considering Zapotec a single language. However, just as with Quechua above, conversations with a native speaker indicated that they perceived Zapotec as one language, with a variety of local variants that are all easy enough to understand (excepting one or two). A broader survey would help resolve this question.
*   Those languages in this dataset that are not on Google Translate have yet to
    undergo a more careful name review; if you see a name in the list above that
    you want to correct, please contact us!

Note on language codes:

  * we use `chm` for Meadow Mari, although `chm` is properly the superset, and `mhr` is the individual code for Meadow Mari.
  * Similarly, we use `rom` for all Romani dialects and `ak` for Twi (see note above).
  * We use `fa-AF` for Dari. The specific code `prs` is probably more precise.
  * `apd-SD` is probably redundant; `apd` alone refers to Sudanese Arabic

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

We welcome contributions, corrections, and suggestions, especially from speakers
of these languages. Please file bugs on this repo or contact
icaswell꩜google.com if you have suggestions or corrections. This
repository may be updated sporadically with corrections or additional
translations.


## License

This data is released with the `CC-BY-4.0` license.