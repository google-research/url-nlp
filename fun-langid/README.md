# FUN-LangID


**Welcome to FUN-LangID (Frequently Used N-grams Language ID model), a very
simple, character 4-gram LangID classifier recognizing up to 1633 languages!**
This model is great if you want something simple, scalable, and without
dependencies! All you need is this one python file. This model is not the best
if you want high-quality guarantees.

Good Language Identification (LangID) is hard. If you aren't convinced, read
[this paper](https://arxiv.org/pdf/2010.14571.pdf). However, if you don't care
about very high quality, and you just want something maximally simple to check
your data or prototype, then this module may be for you! It can get about 90%
precision on 1000+ languages. Almost any other LangID model you find or train
will have higher quality on the languages it supports, but very few will beat
this in easy of use, extensibility, and language coverage! In summary:

This model is great when:

*   You want to quickly check something, eg. what language a document is likely
    to be in
*   You have long inputs, e.g. paragraphs
*   You don't have a technical background, or just don't want to deal with
    virtual environments etc.
*   You want something that will work for as long as Python works
*   You want easy customization -- just modify `fun_langid.py`!
*   You want to add your own languages (Just add 150 tokens into `self._lexicon`!)
*   You want LangID on 1000s of languages
*   You want to quickly change which subset of languages you care about
*   You want a ranked list of which languages a piece of text might be in,
    instead of a single class prediction

This model is not great when:

  * You want a very high-quality model
  * You want a very low-latency (fast) model
  * Your inputs are short, e.g. single words or sentence fragments
  * Your inputs are noisy, especially if they have repeating n-grams
  * You want to differentiate dialects or close languages

_This is not an officially supported Google product._

## How does it work?

This model simply reports the percentage of substrings in an input that are
common in a given language. So if it gives a score of 30% to `cv` for some input
paragraph, this means that 30% of the input is in the Chuvash language (BCP-47
code `cv`)

The substrings in question are character 4-grams. For instance, the 4-grams
in the word `"wombat"`` are `"womb"``, `"omba"``, and `"mbat"``. These 4-grams
may contain spaces, e.g. `"a cat"``. There is however one innovation on top of
this: this model actually operates on **stripped** character 4-grams, i.e.
4-grams with leading and trailing spaces removed. As an example:

  * Sentence: "I am not a cat"
  * standard 4-grams: `['I am', ' am ', 'am n', 'm no', ' not', 'not ', 'ot a', 't a ', ' a c', 'a ca', ' cat']`
  * stripped 4-grams: `['I am', 'am', 'am n', 'm no', 'not', 'not', 'ot a', 't a', 'a c', 'a ca', 'cat']`

The advantage of this is that it will also capture some 2-grams and 3-grams. And
incorporating token boundaries has been proven to be effective for approaches
like [ChrF++](https://www.statmt.org/wmt17/pdf/WMT70.pdf).

If a person wanted to improve the accuracy of this model, one could use a
combination of 1-grams, 2-grams, and so on. This would certainly get higher
accuracy, and is more or less exactly what the
[CLD](https://github.com/mzsanford/cld) models do. However, the goal of the
present model is purely simplicity, and stripped 4-grams get us most of the way
there. The justification for 4-grams is given below.

## Performance

Experiments were done to determine the accuracy of this model. Using all 1633
languages, the model gets an average precision of 90.8% on the training data.
This went up to 91.8% with the top 200 4-grams, and 93.0% with the top 300
4-grams, and fell to 84.6% with the top 50. Stripped 4-grams were much more
effective than stripped 3-grams or stripped 5-grams. Here is the precision on
1633 languages for stripped n-grams of different flavors. The score for the
present model is bolded:

n-gram  | top-50 |top-100 | **top-150** |top-200 |top-300 |
--------|--------|--------|--------|--------|--------|
3-grams | 77.8   | 	83.1  | 	85.3 | 	86.6  | 	88.0 |
**4-grams** | 84.6   | 	88.9  | 	**90.8** | 	91.8  | 	93.0 |
5-grams | 74.5   | 	79.7  | 	82.2 | 	83.6  | 	85.4 |

The results above are on sentences. This model is much more effective for longer
content. Here are results for paragraphs (sets of 5 sentences), where even the
top 10 ngrams give good results:

n-gram  | top-10 |top-50 |top-100 | **top-150**
--------|--------|--------|---------|--------|
**4-grams** | 92.9   | 	98.2  | 	98.9 | 	**99.2**  |

Note that LangID performance is notoriously hard to measure well, largely due to
out-of-domain effects (e.g. web noise or nonstandard characters) and the class
imbalance problem. LangID is also much more difficult for closer dialects.
Fun-LangID has the lowest quality on close dialects; for close dialect
detection, a more expressive neural model is even more important.


### Other notes

**Normalization:** The model first applies lower-casing and removes the
characters `'` and `/`; no other normalization is applied.

**Special cases:** Although the approach outlined above would work fine for most
languages, including languages that don't use whitespace, like `th` (Thai), 
`lo` (Lao), `km` (Khmer), `bo` (Tibetan), and `dz` (Dzongkha), it will not work
well for ideographic languages such as Chinese and Japanese. Therefore, `zh`, 
`zh-Hant`, `yue`, and `ja` are special-cased, and use 1-grams only.

**Special languages:** There are a few unusual languages in this model, chiefly:

1. non-unicode fonts of other languages, denoted with a script tag starting in
`Z`: `ee-Zewe, nv-Znav, mni-Zepa, mni-Zrat, ber-Zber` and

2. "noise"
languages of web noise that looks like e.g. mis-rendered PDFs, bad OCR on Arabic
text, etc.: `zxx-x-arabocr, zxx-x-nonuni, zxx-x-pdf, zxx-x-creative, zxx-x-latnunk, zxx-x-arabunk`


## How to Use

Here are examples of how to make a `FunLangID` class and use it to predict the
language of a text sample.

```python
# Make a LangID model on 1633 languages
langid = FunLangID()
print(langid.predict_top("Situs puniki kasayagayang olih Wikimédia Foundation tur bebas cingakin olih parajanané makasami."))

# Make a LangID model only on the top 200 most common languages on the web
langid = FunLangID(n_langs=200)

# Make a LangID model only on the top 200 most common languages on the web,
# but also include `ban`
langid = FunLangID(n_langs=200, include_langs={"ban"})
```

### Note for the non-technical:

If you have no technical background, your
eyes may have glazed over at this point. Here are the simplest instructions:

1.  Download `fun_langid.py`
2.  Uncomment the last two lines of that file (after "QUICKSTART")
3.  Open the Terminal app (Mac) or some other command-line app
4.  Type the following line and hit enter: `python3 ~/Downloads/fun_langid.py`
5.  If you have issues with this, e.g. it says `"python3 not found"`, ask someone
    for help.

## Understanding results
Say you run the model on a sentence and you get this result:

```
[('ban', 0.1595744680851064), ('la', 0.0851063829787234), ('mkn', 0.0851063829787234), ('pam', 0.0851063829787234), ('jv', 0.07446808510638298)]
```

This means that the sentence is most likely in the language `ban`. Looking at
the full results, roughly 16% of the sentence is common stripped 4-grams in
`ban`, 8.5% in the language `la`, `mkn`, and `pam`, and 7.4% in `jv`.

But what are these languages? These are BCP-47 language codes. You can check
what code `XYZ` means by going to
https://en.wikipedia.org/w/index.php?title=ISO_639:XYZ. For instance, if you
want to know what this language `ban` is, you can go to
https://en.wikipedia.org/w/index.php?title=ISO_639:ban, and see that the
language is Balinese.

Going back to the results, this means that the sentence is most likely to be
Balinese, second most likely to be `la` (Latin), `mkn` (Kupang Malay), or `pam`
(Kapampangan), and third most likely to be `jv` (Javanese). As it turns out,
this sentence is Balinese! And the others are all related languages, except 
Latin.

## Known Issues

* The major language upon which this model has the worst performance is Zulu,
  (`zu`).  This model usually predicts it as Northern Ndebele (`nd`), a related
  Zunda language.
* This could be implemented in a much more efficient way. Do you want to make
  a C++ version??

