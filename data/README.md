# Data

This folder contains the manually annotated data used to train and evaluate the models. Article texts are not included, as NOS.nl news content is copyrighted. Each file lists the title, publication date and URL of the annotated articles, so the texts can be retrieved from NOS.nl.

## Files

| File | Content | Coders |
| --- | --- | --- |
| `coded_df_topics_full.csv` | Main-topic and sub-topic annotations (796 articles) | main_coder, second_coder |
| `coded_df_actors_full.csv` | Actor annotations: actor, type, function, quotation and stance towards Covid-19 measures | main_coder, second_coder |
| `reliability_topics_researcher.csv` | Topic annotations of the 120 held-out articles by all three coders | researcher, main_coder, second_coder |
| `reliability_actors_final_cleaned_researcher.csv` | Actor annotations of the held-out articles by all three coders | researcher, main_coder, second_coder |
| `reliability_topics_final_extra.csv` | Double-coded topic annotations used for inter-coder reliability | main_coder, second_coder |
| `reliability_actors_final_extra.csv` | Double-coded actor annotations used for inter-coder reliability | main_coder, second_coder |

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
