# Diabetes-CGM-Consumer-Posts-Analysis


# Project Overview
This project analyzes consumer posts, comments, and reviews about Continuous Glucose Monitoring (CGM) devices for diabetes management, sourced from social media platforms (e.g., Twitter, Instagram, Facebook, forums, blogs) between April 1, 2021, and September 9, 2021. The dataset, provided by 113 Industries, contains natural language data in the Sound Bite and Title columns, along with structured metadata (e.g., Source, Author Gender, Sentiment, No. of Followers). The goal is to extract insights into consumer preferences, product performance, and audience segments to inform product development and marketing strategies for CGM manufacturers (e.g., Dexcom, FreeStyle Libre, Medtronic, Senseonics) or potential market entrants.
The analysis employs Natural Language Processing (NLP) techniques, including text preprocessing, topic modeling, sentiment analysis, clustering, and visualization, to understand market trends, competitive landscapes, consumer pain points, and feature requests. The project is executed in a Jupyter Notebook (CGM_Consumer_Post_Analysis.ipynb) and aligns with product management objectives, such as improving CGM adoption, enhancing product features, and targeting specific consumer segments.
Methodology
The methodology is structured around competition/product analysis, audience analysis, and feedback categorization, with preprocessing and NLP techniques ensuring data quality and actionable insights. It is implemented in Python using libraries like pandas, nltk, sklearn, TextBlob, transformers, matplotlib, seaborn, and networkx. Below, we detail the key steps, followed by a critical commentary on the methodology’s strengths, limitations, and potential improvements.

# Methodology Steps

## Data Preprocessing:

Load the dataset (Dataset.csv) and remove duplicates using pandas.drop_duplicates() to ensure unique posts.
Eliminate non-relevant data, including footer details (e.g., "113 INDUSTRIES.COM"), posts from high-follower authors (using IQR-based outlier detection on No. of Followers/Daily Unique Visitors), and promotional content (filtered by keywords like "promotional").
Clean the Sound Bite and Title columns by tokenizing, removing stopwords, punctuation, and applying lemmatization using nltk or spaCy. For topic modeling, use a processed dataset (Unstructured_Data__Tokenized_and_Stemmed_.csv) with stemmed text.
Handle missing values and exclude columns with over 90% missing data (e.g., ratings, author location details).


## Competition and Product Analysis:

### Product Extraction: Identify mentions of CGM products (e.g., Dexcom, FreeStyle Libre, Medtronic, Senseonics) in Sound Bite and Title using keyword matching and regex.

### Topic Modeling: Apply Latent Dirichlet Allocation (LDA) with sklearn to extract key attributes (e.g., accuracy, cost, app usability) for each product, using a document-term matrix from CountVectorizer (max 5,000 features, 5 topics).

### Attribute Sentiment: Analyze consumer preferences (e.g., liked: Dexcom accuracy, FreeStyle Libre affordability; disliked: Medtronic sensor reliability, FreeStyle Libre app issues) using custom sentiment analysis with RoBERTa (transformers) and compare with the dataset’s Sentiment column. Use TextBlob for cluster-level sentiment scoring.

### Price, Performance, Accuracy, Quality, Value: Quantify sentiment for these attributes by keyword-based filtering and RoBERTa sentiment scoring.

### Twitter vs. Non-Twitter Analysis: Process Twitter and non-Twitter data separately to compare ease and accuracy (Twitter: real-time but noisy; non-Twitter: detailed but less timely).
### Positive/Negative Objects: Attribute sentiment to specific objects (e.g., "sensor," "app") using keyword co-occurrence and validate against dataset columns (Positive Objects, Negative Objects).


## Audience Analysis:

### Demographic Profiling: Extract attributes like age (adult, child), gender, medical conditions (Type 1, Type 2, gestational diabetes), and professions/interests from Sound Bite, Title, Professions, and Interests columns using keyword matching and regex.
### Diabetes Type Classification: Categorize authors by diabetes type (Type 1: 12,019 authors; Type 2: 503 authors) using explicit mentions (e.g., "T1D", "Type 2") and contextual keywords (e.g., "insulin pump" for Type 1, "metformin" for Type 2) via the classify_diabetes_type function.
### Persona Creation: Develop 5-10 consumer segments (e.g., Dexcom Enthusiasts, FreeStyle Libre Users, Health-Conscious Generalists) via K-means clustering (5 clusters) on TF-IDF vectors, incorporating sentiment, engagement (author_reddit_karma), and influence (followers/daily_unique_visitors/subscribers).
### Influence Analysis: Analyze Reddit karma and followers to quantify author influence, binning followers into categories (Low, Medium, High, Very High).


### Pain Points and Feature Requests:

Categorize posts as pain points (e.g., sensor discomfort) or feature requests (e.g., longer sensor lifespan) using keyword-based classification (issue, problem for pain points; wish, need for feature requests).
Use an LLM (e.g., GPT-3.5 via get_completion) to identify the top 5 pain points and feature requests from summarized feedback, limited to 10 examples per category for readability.


Visualizations:

Generate bar charts for diabetes type distribution (e.g., Type 1 vs. Type 2), pie charts for sentiment distribution, and scatter plots for clusters using PCA or t-SNE with seaborn.
Create network graphs with networkx to visualize persona relationships (e.g., sentiment, gender, influence, karma), including an advanced mind map with Reddit karma and follower nodes.
Save plots (e.g., topic_model_results.csv for topic modeling outputs) for stakeholder review.




# Conclusion
The methodology effectively combines traditional and advanced NLP techniques to deliver actionable insights for CGM product development and marketing. While robust, it can be enhanced by addressing keyword limitations, optimizing clustering and topic modeling, and improving LLM transparency. These refinements would ensure even deeper and more reliable insights for stakeholders.
