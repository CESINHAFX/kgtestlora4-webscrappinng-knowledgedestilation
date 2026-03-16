# Adaptation Instructions for kaggle_web_scraping_6celulas_executed.ipynb

This document outlines the necessary adaptations made to the existing `kaggle_web_scraping_6celulas_executed.ipynb` notebook for AIMO knowledge distillation.

## Adaptation Summary

1. **Setting Configuration:** The notebook has been updated to configure AIMO/AIMO2/AIMO3/GSM8K/Kaggle sources, temporal split settings, and extraction targets.
2. **Scraping Mechanism:** Implemented Selenium-compatible helpers to discover relevant notebook and writeup URLs.
3. **HTML Download:** The functionality to download notebook iframe HTML and writeup HTML has been added, with sanitized filenames and metadata stored in the `results/` directory.
4. **HTML Parsing:** BeautifulSoup is utilized with `find_all` to extract relevant components, including problems, solutions, code blocks, tables, images, and AIMO-relevant strategy signals.
5. **Dataset Creation:** A structured dataset/DataFrame is built for knowledge distillation, containing fields such as:
   - `source_url`
   - `source_type`
   - `source_date`
   - `author`
   - `title`
   - `competition`
   - `problem_text`
   - `final_answer`
   - `solution_text`
   - `code_blocks`
   - `strategy_tags`
   - `preprocessing_signals`
   - `modeling_signals`
   - `training_signals`
   - `validation_signals`
   - `inference_signals`
   - `cost_signals`
   - `temporal_split`
   - `license_note`
   - `extraction_quality`
   - `raw_html_path`
6. **Data Persistence:** The dataset is now persisted in SQLite and JSONL formats for subsequent LoRA/SFT training.

## Running the Adapted Pipeline

To run the adapted scraping pipeline in a virtual environment:
1. Activate your virtual environment.
2. Ensure all required packages are installed as per the repository requirements.
3. Run the `kaggle_web_scraping_6celulas_executed.ipynb` notebook in Jupyter or JupyterLab.
4. Follow the prompts to initiate the scraping and data extraction process.
5. After completion, the outputs can be fed into the LoRA workflow from `test4loracomguia.ipynb`.