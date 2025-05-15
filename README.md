# Diabetes-CGM-Consumer-Posts-Analysis


# Project Overview
This project analyzes consumer posts, comments, and reviews about Continuous Glucose Monitoring (CGM) devices for diabetes management, sourced from social media platforms (e.g., Twitter, Instagram, Facebook, forums, blogs) between April 1, 2021, and September 9, 2021. The dataset, provided by 113 Industries, contains natural language data in the Sound Bite and Title columns, along with structured metadata (e.g., Source, Author Gender, Sentiment, No. of Followers). The goal is to extract insights into consumer preferences, product performance, and audience segments to inform product development and marketing strategies for CGM manufacturers (e.g., Dexcom, FreeStyle Libre, Medtronic, Senseonics) or potential market entrants.
The analysis employs Natural Language Processing (NLP) techniques, including text preprocessing, topic modeling, sentiment analysis, and audience segmentation, to understand market trends, competitive landscapes, and consumer pain points. The project is executed in a Jupyter Notebook (113_Industries_Team_8.ipynb) and aligns with product management objectives, such as improving CGM adoption, enhancing product features, and targeting specific consumer segments.
# Methodology
The analysis is structured around competition/product analysis and audience analysis, with preprocessing and NLP techniques applied to ensure data quality and actionable insights. The methodology is implemented in Python using libraries like pandas, nltk, sklearn, TextBlob, and transformers.

## Data Preprocessing:

Load the dataset (Dataset.csv) and remove duplicates using pandas.drop_duplicates() to ensure unique posts.
Eliminate non-relevant data, including footer details (e.g., "113 INDUSTRIES.COM"), posts from high-follower authors (using IQR-based outlier detection on No. of Followers/Daily Unique Visitors), and promotional content (filtered by keywords like "promotional").
Clean the Sound Bite and Title columns by tokenizing, removing stopwords, punctuation, and applying lemmatization using nltk or spaCy.
Handle missing values and exclude columns with over 90% missing data (e.g., ratings, author location details).


## Competition and Product Analysis:

Product Extraction: Identify mentions of CGM products (e.g., Dexcom, FreeStyle Libre, Medtronic, Senseonics) in Sound Bite and Title using keyword matching and regex.
Topic Modeling: Apply Latent Dirichlet Allocation (LDA) with sklearn to extract key attributes (e.g., accuracy, cost, app usability) for each product, using a document-term matrix from CountVectorizer.
Attribute Sentiment: Analyze consumer preferences (liked: Dexcom accuracy, FreeStyle Libre affordability; disliked: Medtronic sensor reliability, FreeStyle Libre app issues) using custom sentiment analysis with RoBERTa (transformers) and compare with the dataset’s Sentiment column.
Price, Performance, Accuracy, Quality, Value: Quantify sentiment for these attributes by keyword-based filtering and RoBERTa sentiment scoring.
Twitter vs. Non-Twitter Analysis: Process Twitter and non-Twitter data separately to compare ease and accuracy (Twitter: real-time but noisy; non-Twitter: detailed but less timely).
Positive/Negative Objects: Attribute sentiment to specific objects (e.g., "sensor," "app") using keyword co-occurrence and validate against dataset columns (Positive Objects, Negative Objects).


## Audience Analysis:

Demographic Profiling: Extract attributes like age (adult, child), gender, medical conditions (Type 1, Type 2, gestational diabetes), and professions/interests from Sound Bite, Title, Professions, and Interests columns using keyword matching and regex.
Diabetes Type Classification: Categorize authors by diabetes type (Type 1: 12,019 authors; Type 2: 503 authors) using explicit mentions (e.g., "T1D", "Type 2") and contextual keywords (e.g., "insulin pump" for Type 1, "metformin" for Type 2).
Persona Creation: Develop 5-10 consumer segments (e.g., Dexcom Enthusiasts, FreeStyle Libre Users, Health-Conscious Generalists) via K-means clustering on TF-IDF vectors, incorporating sentiment, engagement (author_reddit_karma), and influence (followers/daily_unique_visitors/subscribers).
Visualizations: Generate bar charts for diabetes type distribution, pie charts for sentiment distribution, and network graphs for persona relationships using matplotlib and networkx.


## Pain Points and Feature Requests:

Categorize posts as pain points (e.g., sensor discomfort) or feature requests (e.g., longer sensor lifespan) using keyword-based classification (issue, problem for pain points; wish, need for feature requests).
Use LLM (e.g., GPT-3.5) to identify top 5 pain points and feature requests from summarized feedback.


## Strategic Recommendations:

Recommend product innovations (e.g., needle-free sensors, AI-driven predictive alerts, 30-90 day sensor lifespans) based on pain points and feature requests.
Suggest marketing strategies targeting specific segments (e.g., Type 1 diabetics for advanced CGM features, Type 2 for affordable options) and leveraging high-engagement users via community platforms.
Propose affordability enhancements like subscription models and insurance partnerships to increase adoption.



This methodology ensures a comprehensive analysis of consumer sentiment, product performance, and audience segments, providing actionable insights for CGM product managers to enhance market positioning and user experience.
