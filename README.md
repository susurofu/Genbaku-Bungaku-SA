# *Gendered Emotions: Masculine and Feminine Emotional Modes of Writing in Japanese Atomic Bomb Literature*

This is a supplementary repository with the script and results for the article *Gendered Emotions: Masculine and Feminine Emotional Modes of Writing in Japanese Atomic Bomb Literature*, submitted to The Journal of the Japanese Association for Digital Humanities.

## Abstract
This article examines gendered emotional patterns in Japanese Atomic Bomb Literature through Sentiment Analysis (SA), challenging the assumption that women’s writing is inherently caregiving. Using the Oseti SA model, the study introduces sentiment protection, a measure of how authors shield their characters from trauma. Findings reveal that male authors exhibit stronger sentiment protection than female writers, reversing traditional gender expectations. Analyzing hibakusha and non-hibakusha authors, the study suggests that sentiment protection functions as a genre-defining feature, with male writers adhering to narrative conventions while female authors demonstrate greater variability. Bridging feminist literary criticism, digital humanities, and reception theory, the study formalizes gendered writing assumptions into computationally testable hypotheses. By integrating algorithmic criticism, this research provides a data-driven perspective on gender, trauma, and genre in Japanese war literature, offering new insights into the emotional structures of narratives depicting nuclear catastrophe.

## Repository Structure
This repository includes 4 folders:


1. *Figures*  
   The folder contains figures resulting from the analysis.

2. *Tables*  
   The folder contains tables resulting from the analysis, including some additional interim tables.

3. *Notebooks*

   *Notebook 1: Text Preprocessing*  
   This notebook preprocesses the texts and runs the script to replace frequent patterns of OCR errors in the corpus.

   *Notebook 2: Direct Speech Extraction*  
   This notebook presents the script for direct speech extraction and prepares a sample dataset of random extractions from the corpus, which is used for testing Oseti against transformer models.

   *Notebook 3: Test of Oseti against other SA models*  
   This notebook tests Oseti against transformer models.

   *Notebook 4: Results Evaluation*  
   This notebook contains tests for statistical significancy of the results (Mann-Whitney U test, permutation test, Chi-squared test) and discusses more detaily than in the text of the article the outcomes of these tests.

## Note on *Oseti* Usage
Oseti received its last update to the main Python script in 2023. Depending on the version of MeCab being used, there could be issues with the incompatibility of Oseti with newer MeCab versions. If you encounter an error, check the following line:

```python
lemma = feature[6] if feature[6] != '*' else node.surface
```

and replace it with:

```python
lemma = feature[-1] if feature[-1] != '*' else node.surface
```
in oseti.py in the library directory. The error occurs because the index of the lemma was changed in MeCab.Tagger(mecab_args). However, in this case, I recommend checking the MeCab parser output directly.