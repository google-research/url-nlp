# TaTA: A Multilingual Table-to-Text Dataset for African Languages

TaTA (Table-to-Text in African languages) is the first large multilingual table-to-text
datasets with a focus on African languages. The dataset is parallel and covers nine languages,
eight of which are spoken in Africa: Arabic, English, French, Hausa, Igbo, Portuguese, Swahili,
Yorùbá, and Russian.

TaTa was created by extracting tables from charts in 71 PDF reports published between
1990 and 2021 by the [Demographic and Health Surveys Program](https://dhsprogram.com/).
The reports are published in English and commonly a second language. The extracted tables
were then translated from English by professional translators to all eight languages. The final dataset
comprises 8,479 tables. For more information on the dataset creation, refer to the paper
TaTA: A Multilingual Table-to-Text Dataset for African Languages.

We provide the data files in the corresponding splits in `train.json`, `dev.json`, and `test.json`. We include the data for the zero-shot test language in a separate file (`ru.json`). Each example json object contains the following features:

- `example_id`: The ID of the example. Each ID (e.g., `AB20-ar-1`) consists of three parts: the document ID, the language ISO 639-1 code, and the index of the table within the document.
- `title`: The title of the table.
- `unit_of_measure`: A description of the numerical value of the data. E.g., percentage of households with clean water.
- `chart_type`: The kind of chart associated with the data. We consider the following (normalized) types: horizontal bar chart, map chart, pie graph, tables, line chart, pie chart, vertical chart type, line graph, vertical bar chart, and other.
- `was_translated`: Whether the table was transcribed in the original language of the report or translated.
- `table_data`: The table content is a JSON-encoded string of a two-dimensional list, organized by row, from left to right, starting from the top of the table. Number of items varies per table. Empty cells are given as empty string values in the corresponding table cell.
- `table_text`: The sentences forming the description of each table are encoded as a JSON object. In the case of more than one sentence, these are separated by commas. Number of items varies per table.
- `linearized_input`:  A single string that contains the table content separated by vertical bars, i.e., |. Including title, unit of measurement, and the content of each cell including row and column headers in between brackets, i.e., (Medium Empowerment, Mali, 17.9).

We are planning to additionally release the original charts as screenshots.

We also provide the annotations of the human evaluation of system outputs in `all_human_annotations.csv`. Annotators answered a series of up to four questions for each output, which are based on a variant of [Attribution to Identifiable Sources](https://arxiv.org/abs/2112.12870) (AIS). The file consists of the following columns:

- `model`: The name of the model that was evaluated. This is `mt5_small`, `ssa_mt5`, `mt5_xxl`, or `reference` (in the case of the gold reference).
- `output`: The model output or gold reference that was evaluated.
- `interpretable`: Whether the sentence is overall understandable by an annotator, allowing minor grammatical mistakes. If the answer is no, the remaining questions are not answered.
- `attributable`: Whether *all* information in the sentence is attribute to the table or its meta data, i.e., whether every part of the sentence is grounded in the input. If the answer is no, the remaining questions are not answered.
- `cells`: The number of cells one has to look at to generate the information in the sentence.
- `reasoning`: Whether the generated text requires reasoning or comparison of two or more cells.
- `id`: The ID of the example. This is the same ID as in the data files above.
- `set`: The name of the split of the example (`dev` or `test`).
- `language`: Legacy field, ignore.
- `lang`: The ISO 639-1 code of the language of the sentence.


## How to load the data

We implemented a loader for the dataset in [Huggingface datasets](https://huggingface.co/datasets/GEM/TaTA). All you will need to do is run the following code:

```
import datasets
data = datasets.load_dataset('GEM/TaTA')
```


## Citation

If you are using the dataset, please cite:

```
@misc{gehrmann2022TaTA,
  Author = {Sebastian Gehrmann and Sebastian Ruder and Vitaly Nikolaev and Jan A. Botha and Michael Chavinda and Ankur Parikh and Clara Rivera},
  Title = {TaTa: A Multilingual Table-to-Text Dataset for African Languages},
  Year = {2022},
  Eprint = {arXiv:2211.00142},
}
```
