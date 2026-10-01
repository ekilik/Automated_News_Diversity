# Data

This folder contains the manually annotated data used to train and evaluate the models. Article texts are not included, as NOS.nl news content is copyrighted. Each file lists the title, publication date and URL of the annotated articles, so the texts can be retrieved from NOS.nl.

## Processing pipeline

The raw annotations are collected in Qualtrics (`.sav` format) and processed by scripts in `Scripts/5_Annotation_Reliability/` into the cleaned CSV files listed below. The Qualtrics files (`nos_coded_*.sav`) are the source data; the CSV files are the cleaned, deduplicated versions used throughout the analysis pipeline.

## Files

| File | Content | Coders |
| --- | --- | --- |
| `coded_df_topics_full.csv` | Main-topic and sub-topic annotations (796 articles) | main_coder, second_coder |
| `coded_df_actors_full.csv` | Actor annotations: actor, type, function, quotation and stance towards Covid-19 measures | main_coder, second_coder |
| `reliability_topics_researcher.csv` | Topic annotations of the 120 held-out articles by all three coders | researcher, main_coder, second_coder |
| `reliability_actors_final_cleaned_researcher.csv` | Actor annotations of the held-out articles by all three coders; used for the reported inter-coder reliability (main_coder vs second_coder) and as the gold standard for model evaluation (researcher) | researcher, main_coder, second_coder |
| `reliability_topics_final_extra.csv` | Double-coded topic annotations used for inter-coder reliability | main_coder, second_coder |
| `reliability_actors_final_extra.csv` | Double-coded actor annotations prepared from the raw annotation exports (intermediate output of `2_prepare_reliability_data.ipynb`; not used for the reported reliability) | main_coder, second_coder |

### Manual validation of model outputs

| File | Content |
| --- | --- |
| `actor_names_researcher_SVM_manual.xlsx` | Manual validation of SVM actor extraction results against gold-standard researcher annotations |
| `actor_names_researcher_ROBBERT_manual.xlsx` | Manual validation of RobBERT actor extraction results against gold-standard researcher annotations |
| `actor_names_researcher_mistral_manual.xlsx` | Manual validation of Mistral-7B actor extraction results against gold-standard researcher annotations |
| `actor_names_researcher_starling_manual.xlsx` | Manual validation of Starling-7B actor extraction results against gold-standard researcher annotations |

These files document the researcher's manual review of each model's actor extraction performance, flagging false positives, false negatives, and boundary cases.

## Coders

- `researcher`: annotations used as the gold standard for model evaluation
- `main_coder`: annotated the training set
- `second_coder`: independently annotated the held-out articles to assess reliability

## Columns

- `article_id`: NOS article identifier
- `title`, `date`, `url`: article metadata
- `reliability_article`: 1 for the held-out articles used for reliability and evaluation, 0 for the training set
- `about_covid`: 1 if the pandemic is the main topic of the article
- `topic_a` to `topic_n`: sub-topic present (1) or absent (0); categories are defined in Appendix A of the paper
- `actor_name`, `actor_type`, `actor_function` (`actor_function_text` for "other"), `actor_pp` (party affiliation)
- `directly_quoted`, `indirectly_quoted`: whether the actor is quoted or paraphrased
- `talks_covid_measures`, `measure_1` to `measure_17`, `measure_other`: whether the actor mentions a Covid-19 measure; the `_positive`, `_negative` and `_neutral` columns give the actor's stance towards that measure.

## Running notebooks without full text

**Most notebooks require the article text** to train or apply models. Specifically:

- **Sections 1–4**: All analysis, model training, and model application notebooks require the full article text. This includes topic modeling, actor extraction, and stance detection across all approaches.

- **Section 5 (Annotation Reliability)**:
  - **Notebooks 1–2** (`1_prep_sample_annotation.ipynb`, `2_prepare_reliability_data.ipynb`): These read the raw Qualtrics `.sav` files (`nos_coded_*.sav`) and produce the cleaned CSV files. They require access to the original Qualtrics exports and intermediate data files (`final_nosarticles.csv`, `ALLcorona_keywords_list_final_v2.csv`).
  - **Notebooks 3–4** (`3_reliability_topics.ipynb`, `4_reliability_actors.ipynb`): These analyze inter-coder reliability using only the cleaned annotated CSVs listed above. They compare human annotations across coders and require no article text, Qualtrics files, or intermediate results.

To run the full pipeline, you will need to obtain the article texts from NOS.nl using the URLs and dates in the CSV files. To run only the reliability analysis (notebooks 3–4), no additional data is required beyond what is in the `data/` folder. 
