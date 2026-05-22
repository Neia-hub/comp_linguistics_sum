- [[#~={orange}1. Data Acquisition=~|~={orange}1. Data Acquisition=~]]
	- [[#~={orange}1. Data Acquisition=~#~={yellow}Data Available Scenarios=~|~={yellow}Data Available Scenarios=~]]
	- [[#~={orange}1. Data Acquisition=~#~={yellow}Data from Other Resources=~|~={yellow}Data from Other Resources=~]]
	- [[#~={orange}1. Data Acquisition=~#~={yellow}Nobody has the Data=~|~={yellow}Nobody has the Data=~]]
- [[#~={orange}2. Text preprocessing (broad)=~|~={orange}2. Text preprocessing (broad)=~]]
	- [[#~={orange}2. Text preprocessing (broad)=~#~={yellow}Cleaning & normalization=~|~={yellow}Cleaning & normalization=~]]
	- [[#~={orange}2. Text preprocessing (broad)=~#~={yellow}Text preprocessing=~|~={yellow}Text preprocessing=~]]
- [[#~={orange}3. Feature engineering=~|~={orange}3. Feature engineering=~]]
- [[#~={orange}4. Modeling=~|~={orange}4. Modeling=~]]
	- [[#~={orange}4. Modeling=~#~={yellow}Heuristic Approaches=~|~={yellow}Heuristic Approaches=~]]
	- [[#~={orange}4. Modeling=~#~={yellow}Machine Learning (ML) Approaches=~|~={yellow}Machine Learning (ML) Approaches=~]]
	- [[#~={orange}4. Modeling=~#~={yellow}Deep Learning (DL) Approaches=~|~={yellow}Deep Learning (DL) Approaches=~]]
	- [[#~={orange}4. Modeling=~#~={yellow}Cloud APIs=~|~={yellow}Cloud APIs=~]]
	- [[#~={orange}4. Modeling=~#~={yellow}Selection Criteria=~|~={yellow}Selection Criteria=~]]
- [[#~={orange}5. Evaluation=~|~={orange}5. Evaluation=~]]
	- [[#~={orange}5. Evaluation=~#~={yellow}Intrinsic Evaluation=~|~={yellow}Intrinsic Evaluation=~]]
	- [[#~={orange}5. Evaluation=~#~={yellow}Extrinsic Evaluation=~|~={yellow}Extrinsic Evaluation=~]]
	- [[#~={orange}5. Evaluation=~#~={yellow}Importance of Intrinsic and Extrinsic Evaluation=~|~={yellow}Importance of Intrinsic and Extrinsic Evaluation=~]]
- [[#~={orange}6. Deployment=~|~={orange}6. Deployment=~]]
	- [[#~={orange}6. Deployment=~#~={yellow}Deployment=~|~={yellow}Deployment=~]]
	- [[#~={orange}6. Deployment=~#~={yellow}Monitoring=~|~={yellow}Monitoring=~]]
	- [[#~={orange}6. Deployment=~#~={yellow}Update=~|~={yellow}Update=~]]
	- [[#~={orange}6. Deployment=~#~={yellow}Challenges and Considerations=~|~={yellow}Challenges and Considerations=~]]
- [[#~={orange}Examples of Downstreak tasks=~|~={orange}Examples of Downstreak tasks=~]]
	- [[#~={orange}Examples of Downstreak tasks=~#~={yellow}Text Classification=~|~={yellow}Text Classification=~]]
	- [[#~={orange}Examples of Downstreak tasks=~#~={yellow}Named Entity Recognition (NER)=~|~={yellow}Named Entity Recognition (NER)=~]]
	- [[#~={orange}Examples of Downstreak tasks=~#~={yellow}Question Answering (QA)=~|~={yellow}Question Answering (QA)=~]]
	- [[#~={orange}Examples of Downstreak tasks=~#~={yellow}Machine Translation=~|~={yellow}Machine Translation=~]]
	- [[#~={orange}Examples of Downstreak tasks=~#~={yellow}Text Summarization=~|~={yellow}Text Summarization=~]]
	- [[#~={orange}Examples of Downstreak tasks=~#~={yellow}Chatbots and Virtual Assistants=~|~={yellow}Chatbots and Virtual Assistants=~]]
	- [[#~={orange}Examples of Downstreak tasks=~#~={yellow}Speech Recognition=~|~={yellow}Speech Recognition=~]]
	- [[#~={orange}Examples of Downstreak tasks=~#~={yellow}Text Generation=~|~={yellow}Text Generation=~]]
- [[#~={orange}Resumo em tabela=~|~={orange}Resumo em tabela=~]]

---
# NLP Pipeline
Resumindo:
[[#~={orange}1. Data Acquisition=~]]
[[#~={orange}2. Text preprocessing (broad)=~]]
[[#~={orange}3. Feature engineering=~]]
[[#~={orange}4. Modeling=~]]
[[#~={orange}5. Evaluation=~]]
[[#~={orange}6. Deployment=~]]

The order for the `2. Text Preprocessing` can be changed, however, **cleaning and normalization should never be skipped and should be the first step in the pipeline**.
## ~={orange}1. Data Acquisition=~
Data acquisition involves obtaining raw textual data from various sources to create a robust dataset for NLP tasks. It involves assessing the availability and accessibility of data, whether it’s readily available, needs supplementation, or requires creation from scratch.

While data acquisition, you will always face one of three situations:
### ~={yellow}Data Available Scenarios=~
Here, you can further have three situations:
- **Data on Your Desk:** The data needed for the NLP task is already in possession. Initiate the text preprocessing stage immediately.
- **Data in Databases:** The required data resides within company databases or repositories. Collaborate with data engineers to retrieve the data.
- **Less Data:** Insufficient data volume for robust model training or analysis. Employ data augmentation techniques to enhance the dataset.

**Data Augmentation Techniques**:
- **Synonym Replacement:** Replace words with their synonyms to diversify the dataset without altering the context significantly.
- **Bigram Flip:** Alter word sequences by flipping [bigrams](https://en.wikipedia.org/wiki/Bigram) to create variations.
- **Back Translation:** Translate text to another language and then back to the original language, introducing diverse phrasing.
- **Adding Noise:** Introduce random [noise](https://www.techtarget.com/searchbusinessanalytics/definition/noisy-data) or perturbations to augment data.

### ~={yellow}Data from Other Resources=~
In scenarios where data isn’t readily available or needs supplementation, several strategies come into play:
- **Public Datasets:** Utilize publicly available datasets from repositories like [Kaggle](https://www.kaggle.com/), [UCI Machine Learning Repository](https://archive.ics.uci.edu/), or government databases, aligning them with the project’s requirements.
- **Web Scraping:** Extract data from websites or forums by scraping relevant information. Tools like [BeautifulSoup](https://pypi.org/project/beautifulsoup4/) or [Scrapy](https://scrapy.org/) assist in collecting data from various websites.
- **APIs:** Access data through Application Programming Interfaces (APIs) offered by various platforms such as social media APIs (Twitter/X, Reddit, news aggregators, or linguistic databases.
- **PDFs:** Extract text from PDF documents relevant to the project using libraries like [PyPDF2](https://pypdf2.readthedocs.io/) or [PDFMiner](https://pdfminersix.readthedocs.io/).

### ~={yellow}Nobody has the Data=~
In cases where data isn’t available through conventional means, organizations might resort to alternate strategies:
- **Engaging Trusted Clients:** Collaborate with trustworthy clients or users willing to share anonymized data relevant to the project’s goals.
- **Data Generation:** If viable, companies can generate synthetic data or collect information through surveys, interviews, or user-generated content to build a dataset from scratch.

## ~={orange}2. Text preprocessing (broad)=~
### ~={yellow}Cleaning & normalization=~
- **Unicode normalization**.
- **Spelling corrections**.
- Taking out information like **email**, **URLs**, **phone numbers**, **emojis**, **html tags**, etc.
### ~={yellow}Text preprocessing=~
- **Tokenization**: dividing a string or text into a list of smaller units known as *tokens* (words, sentences, etc).
- **Stop Word Removal**: eliminating common and less meaningful words (stop words) like “the,” “is,” etc., which don’t contribute significantly to the meaning of the text.
- **Stemming/Lemmatization:** reducing words to their root forms - stemming removes prefixes/suffixes, while lemmatization maps words to their base or dictionary form, aiding in standardization.
- **Lowercasing:** converting all text to lowercase to ensure uniformity in text analysis, as case sensitivity can affect certain NLP tasks.
- **Language Detection:** identifying the language of the text, is especially useful when dealing with multilingual content.
- **Part-of-Speech (POS)**: assigning grammatical categories (like nouns, verbs, adjectives) to words in the text, providing insights into the syntactic structure.
- **Coreference Resolution:** resolving references within the text, linking pronouns or noun phrases to their respective entities for coherent understanding and analysis.
- **Named Entity Recognition (NER)**: identifying and categorizing important information known as entities in text. These entities can be names of people, places, organizations, dates, etc. It helps in transforming unstructured text into structured information which helps in tasks like text summarization, knowledge graph creation and question answering.
- **Removing punctuation/digits**
## ~={orange}3. Feature engineering=~
Feature engineering in Natural Language Processing (NLP) involves transforming raw text data into numerical features that machine learning models can comprehend and utilize effectively. The goal is to represent text in a format that captures semantic meaning, contextual information, and relationships between words. It can be done through various techniques:

**Bag of Words (BoW)**:
Represents text as a collection of unique words disregarding grammar or word order. It creates a **matrix where rows represent documents and columns represent unique words**, with **values indicating word occurrence frequencies**. It's simple yet effective, but loses sequence information and context.

**Term Frequency-Inverse Document Frequency (TF-IDF)**:
Measures the importance of words in a document relative to a corpus:
- Considers both the frequency of a term in a document and its rarity across the corpus;
- Assigns higher weights to rare terms that are more discriminative.

**One-Hot Encoding**:
- Represents words as **binary vectors**, where each word has a unique index in the vector;
- Converts words into a high-dimensional space, with each dimension corresponding to a unique word;
-  Effective for small vocabularies but leads to high dimensionality and sparsity issues for large datasets.

**Word Embeddings (Word2Vec, GloVe, FastText)**:
Techniques that map words or phrases to dense **vector representations** in a continuous vector space:
- Capture semantic relationships between words by placing similar words closer in the vector space;
-  Retain semantic meaning and context, useful for capturing word analogies and semantic similarities.

**N-Gram Models**:
Captures sequences of adjacent words (**bigrams**, **trigrams**, etc.) as features, and preserves some sequence information, aiding in capturing context in language.

**Dependency Parsing**:
Represents the grammatical structure of sentences as features. It captures relationships between words through **syntactic dependencies**.
## ~={orange}4. Modeling=~
The heart of the pipeline, where models are applied and evaluated using different approaches:
### ~={yellow}Heuristic Approaches=~
Heuristic models rely on predefined rules or strategies based on expert knowledge to make decisions.

**Application:** Commonly used in simple text-based tasks where rule-based systems can effectively handle specific patterns or tasks, like keyword matching for sentiment analysis or rule-based chatbots.
### ~={yellow}Machine Learning (ML) Approaches=~
ML models learn patterns and relationships from data to make predictions or classifications.

**Applications**:
- **Support Vector Machines (SVM):** Effective for text classification tasks by finding the best separation between classes in a high-dimensional space.
- **Random Forests:** Suitable for tasks like sentiment analysis or text categorization, leveraging ensemble learning for improved accuracy.
### ~={yellow}Deep Learning (DL) Approaches=~
DL models use neural networks with multiple layers to learn complex patterns and representations from raw data.

**Applications:**
- **Recurrent Neural Networks (RNNs):** Effective for sequence-based tasks like **language modelling**, **sentiment analysis**, or **machine translation**.
- **Transformers:** Particularly potent for attention-based mechanisms, excelling in tasks like **language translation**, **text generation**, and **summarization** due to their ability to capture long-range dependencies efficiently.
### ~={yellow}Cloud APIs=~
Cloud-based APIs offer pre-built, scalable models accessible via APIs, saving time and resources.

**Applications:**
- **Google Cloud Natural Language API:** Offers sentiment analysis, entity recognition, and language detection.
- **Microsoft Azure Text Analytics API:** Provides sentiment analysis, key phrase extraction, and named entity recognition.
### ~={yellow}Selection Criteria=~
- **Problem Domain:** Different tasks require different model architectures. Heuristic methods suit specific, rule-based tasks, while ML and DL excel in learning from data.
- **Data Volume and Complexity:** ML and DL approaches often require substantial data volumes for effective learning, with DL being more data-hungry for complex tasks.
- **Resource Availability:** Cloud APIs are convenient for quick prototyping or when resources for training and maintaining models are limited.
## ~={orange}5. Evaluation=~
Evaluation in the NLP pipeline is pivotal, encompassing intrinsic and extrinsic assessments to comprehensively gauge model performance from both technical and practical standpoints.
### ~={yellow}Intrinsic Evaluation=~
Intrinsic evaluation focuses on assessing the technical aspects and capabilities of the model in isolation, without considering its real-world application.

**Examples of Intrinsic Metrics**:
- **Accuracy:** Measures the ratio of correctly predicted instances to the total instances in the dataset.
- **Precision, Recall, F1-score:** Assess the model’s performance in binary or multi-class classification tasks.
- **Perplexity:** Evaluates the language model’s predictive capability in language generation tasks.
- **BLEU Score:** Measures the quality of machine-translated text against a reference translation.
### ~={yellow}Extrinsic Evaluation=~
Extrinsic evaluation measures the model’s performance in real-world applications or business contexts, considering its impact and utility in practical scenarios.

**Examples of Extrinsic Evaluation Metrics**:
- **Business Metrics:** Metrics aligned with specific business goals or outcomes, such as customer satisfaction scores, revenue impact, or user engagement rates.
- **Task-Specific Metrics:** Metrics directly relevant to the NLP task at hand, like sentiment analysis accuracy for customer feedback or document classification precision for information retrieval systems.
- **User-Centric Evaluation:** Soliciting user feedback, surveys, or usability testing to assess user satisfaction and experience with the NLP application.
### ~={yellow}Importance of Intrinsic and Extrinsic Evaluation=~
- **Technical Assessment (Intrinsic):** Intrinsic metrics provide insights into the model’s performance on specific tasks or benchmarks, helping fine-tune model parameters and architectures.
- **Real-world Applicability (Extrinsic):** Extrinsic evaluation ensures that the model’s performance aligns with practical requirements, determining its effectiveness and impact in real-world settings.
## ~={orange}6. Deployment=~
The deployment phase in the NLP pipeline marks the transition of the developed model from the development environment to a production environment, followed by continuous monitoring and adaptation to ensure sustained performance and relevance.
### ~={yellow}Deployment=~
- **Rolling out the Model:** Moving the trained NLP model from the development environment to a production environment where it can be utilized in real-world applications.
- **Infrastructure Setup:** Configuring the necessary infrastructure, integrating the model into the existing systems, and ensuring scalability and reliability.
- **Testing and Validation:** Thoroughly testing the deployed model to ensure it functions as expected and delivers accurate results in the production environment.
### ~={yellow}Monitoring=~
- **Continuous Performance Oversight:** Constantly monitoring the model’s performance, including its accuracy, efficiency, and response time in real-time or at regular intervals.
- **Alert Systems:** Implementing alert systems or triggers to notify about deviations or anomalies in the model’s behaviour, ensuring timely interventions.
### ~={yellow}Update=~
- **Adaptation to Dynamic Data:** Adapting the model to changing data patterns or evolving requirements by periodically updating and retraining the model.
- **Improvement Iterations:** Incorporating feedback, identifying areas for improvement, and fine-tuning the model to enhance its performance or address changing user needs.
- **Version Control:** Maintaining version control to track model iterations and changes, ensuring transparency and reproducibility.
### ~={yellow}Challenges and Considerations=~
- **Data Drift:** Evolving data patterns might lead to data drift, impacting model performance. Regular updates help mitigate this challenge.
- **Ethical and Legal Compliance:** Models must comply with ethical standards and legal regulations, especially when handling sensitive data or influencing critical decisions.
- **Resource Management:** Effective deployment requires resource management to ensure optimal utilization of computational resources and cost efficiency.
# Downstream Tasks
**Downstream tasks** are specific, practical applications of NLP that solve real-world problems by leveraging the outputs of upstream (foundational) tasks. They are the "end goals" of NLP systems, designed to directly assist users, businesses, or researchers. By contrast, **upstream tasks** are low-level, general-purpose tasks that process raw text to extract structure, meaning, or features.
## ~={orange}Examples of Downstreak tasks=~
### ~={yellow}Text Classification=~
 Categorizing text into predefined labels or classes. Uses features like word frequency, embeddings, or syntax to assign labels.
 
Real-world examples:
- **Sentiment Analysis**: Classifying product reviews as positive, negative, or neutral (e.g., "This phone battery dies in 2 hours" → Negative).
- **Spam Detection**: Labeling emails as "spam" or "not spam" (e.g., "Win $1M now!" → Spam).
- **Topic Classification**: Tagging news articles as "politics," "sports," or "technology."
### ~={yellow}Named Entity Recognition (NER)=~
Identifying and classifying named entities (people, organizations, locations, etc.) in text. It detects proper nouns and labels them (e.g., "Apple is based in Cupertino" → "Apple" = Organization, "Cupertino" = Location).

Real-world examples:
- **News Analytics**: Extracting company names or event locations from news articles for market research.
- **Medical Records**: Identifying patient names, diseases, or medications in clinical notes (e.g., "Patient has diabetes" → "diabetes" = Medical Condition).
### ~={yellow}Question Answering (QA)=~
Generating or extracting answers to user questions from a given text (context). It models like BERT or T5 read the context and question, then predict the answer span or generate a response.

Real-world examples:
- **Siri/Google Assistant**: Answering "What’s the weather today?" by extracting data from weather APIs.
- **FAQ Bots**: Helping users find answers in documentation (e.g., "How do I reset my password?" → Directing to the reset link).
### ~={yellow}Machine Translation=~
Translating text from one language to another (e.g., English → Spanish). It uses sequence-to-sequence models (like transformers) to map input text in one language to output text in another.

Real-world examples:
- **Google Translate**: Translating websites, messages, or documents in real time.
- **Localization Tools**: Adapting app interfaces or marketing content for global audiences.
### ~={yellow}Text Summarization=~
Condensing long text into a shorter summary while retaining key information. Extractive (pulling key sentences) or abstractive (generating new, concise sentences).

Real-world examples:
- **News Summaries**: Tools like TL;DR (Too Long; Didn’t Read) that summarize articles.
- **Business Reports**: Automatically summarizing meeting notes or financial reports for executives.
### ~={yellow}Chatbots and Virtual Assistants=~
Conversational AI systems that interact with users via text or speech. It combines NLP tasks like intent recognition (understanding user goals), entity extraction, and response generation.

Real-world examples:
- **Customer Service Bots**: Answering FAQs (e.g., "Where is my order?") on e-commerce sites.
- **Smart Home Assistants**: Controlling devices via voice (e.g., "Hey Alexa, turn on the lights").
### ~={yellow}Speech Recognition=~
Converting spoken language into text (speech-to-text). It uses acoustic modeling and language modeling to transcribe audio.

Real-world examples:
- **Dictation Tools**: Apps like Dragon NaturallySpeaking that let you type by speaking.
- **Subtitle Generation**: Automatically adding captions to videos (e.g., YouTube’s auto-subtitles).
### ~={yellow}Text Generation=~
Creating human-like text from prompts or inputs. Generative models (like GPT-4, Llama, or PaLM) predict the next word in a sequence to build coherent text.

Real-world examples:
- **Content Creation**: Writing blog outlines, social media posts, or marketing copy.
- **Code Generation**: Tools like GitHub Copilot that suggest code snippets based on comments.
# NLP python libraries and tools
## ~={orange}Resumo em tabela=~

| Library      | Applications                                    |     |
| ------------ | ----------------------------------------------- | --- |
| pandas       | Cleaning and normalization                      |     |
| spaCy        | Cleaning and normalization, Linguístic analysis |     |
| scikit-learn | Vectorization                                   |     |
| VADER        | Sentiment analysis                              |     |
| scikit-learn | Text classification, Topic modeling             |     |
| scikit-learn | Classification and Regression                   |     |
| Transformers | Text summarization, Text Generation, etc        |     |
