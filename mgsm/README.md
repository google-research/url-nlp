# Multilingual Grade School Math Benchmark (MGSM)

MGSM is a benchmark of grade-school math problems, proposed in the paper [Language models are multilingual chain-of-thought reasoners](http://arxiv.org/abs/2210.03057).

The same 250 problems from [GSM8K](https://arxiv.org/abs/2110.14168) are each translated via human annotators in 10 languages. The 10 languages are:
- Spanish
- French
- German
- Russian
- Chinese
- Japanese
- Thai
- Swahili
- Bengali
- Telugu

You can find the input and targets for each of the ten languages (and English) as `.tsv` files.
We also include few-shot exemplars that are also manually translated from each language in `exemplars.py`.