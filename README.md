# Automated Analysis of News Content Diversity: A Comparison of Computational Techniques for Identifying Topics, Actors and Viewpoints in News Articles

This repository is for the paper "Automated Analysis of News Content Diversity: A Comparison of Computational Techniques for Identifying Topics, Actors and Viewpoints in News Articles"

In this paper, various computational techniques are compared for the analysis of news content diversity subdimensions. In the literature, three key subdimensions of content diversity is examined:

1. Topic diversity: encompasses the range of issues covered in news media
2. Actor diversity: captures the representation of various voices, their political affiliations and status positions
3. Viewpoint diversity: reflects the spectrum of social, political, and cultural perspectives presented

Through systematic comparison of supervised machine learning, topic modeling, Named Entity Recognition, and open-source Large Language Models (LLMs) against human annotations, this research assesses their effectiveness in capturing content diversity dimensions as conceptualized in journalism studies.

News articles from the NOS.nl (The Dutch Public News Broadcaster) mentioning Covid*, Corona* and Sars-cov* are collected as the test case.

The *"Scripts"* folder includes the Python notebooks that can be used to replicate the study. The *"Visualizations_Paper* folder includes the figures used in the paper. Figure1_AnalysisWorkflow shows the analyses that correspond to the scripts shared in the "Scripts" folder.

1. Folder *1_Filter_Covid_Articles* includes scripts for classifying the news articles mentioning pandemic related keywords to filter articles that do not discuss the pandemic as their main topic.
2. Folder *2a_Subtopic_Classifiers* encompasses scripts testing supervised classifiers and LLMs for binary classification of predefined subtopic categories.
3. Folder *2b_Subtopic_BERTopic* includes the script for running the BERTopic model using RobBERT Dutch model.
4. Folder *3_Actor_Extraction_Function_Classification* includes scripts for identifying news actors and classifying them into four function categories.
5. Folder *4_Stance_Detection* includes scripts of supervised classifiers as well as LLMs for classifying supportive and critical stance towards Covid-19 measures. 

For questions and other comments, you can contact me via the following e-mail address: e.kilik@uva.nl
