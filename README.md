# financial-news-sentiment-analysis

Please run the 'project.ipynb' notebook.
Change the dataset path accordingly.

### **1. Methodology**

### Selection of Dataset

An integral part of our methodology involved selecting a suitable dataset that could provide a rich source of financial news headlines along with corresponding stock market data. After thorough research, we chose the "[Daily News for Stock Market Prediction](https://www.kaggle.com/datasets/aaron7sun/stocknews?select=Combined_News_DJIA.csv)" dataset available on Kaggle.

- **Dataset Description**: This dataset uniquely combines financial news headlines with stock market data. It consists of historical news headlines sourced from Reddit's WorldNews channel, ranked by user votes. Each record in the dataset contains the date, 25 top-ranked news headlines for the day, and a binary label indicating whether the Dow Jones Industrial Average (DJIA) adjusted close value rose or fell on that day. This design allowed us to directly correlate news sentiments with market movements.
- **Utilization in the Project**: The dataset's structure was particularly well-suited for our project's objectives. The news headlines provided a substantial corpus for sentiment analysis, while the accompanying stock market labels (rise or fall) enabled us to correlate the sentiment analysis results with actual market movements. This direct linkage was vital for our goal of predicting market events based on news sentiments.

### Data Processing

Data preprocessing was a critical step in our methodology, ensuring that our model received clean, well-structured input data.

- **Data Cleaning**: Given the format of the dataset, we performed additional cleaning steps, such as removing unwanted characters and formatting issues (e.g., the 'b' character present at the start of each headline), ensuring the cleanliness and consistency of the textual data.
- **Preprocessing Steps**: Our preprocessing pipeline included tokenizing the text data, converting it into numerical sequences, and padding these sequences to ensure consistent input lengths. This standardization was crucial for the effective training and functioning of our LSTM model.
- **Text Aggregation**: To analyze the overall sentiment for each day, we aggregated the 25 headlines into a single text block per date. This aggregation was crucial in assessing the day's collective sentiment, which we then correlated with the stock market's movement for that day.
- **Training and Testing Sets**: We divided our dataset into training and testing sets, maintaining a balance that would allow our model to learn effectively from the training data while ensuring reliable evaluation using the test data.

### Model Development

We developed a Natural Language Processing (NLP) model, integrating a Long Short-Term Memory (LSTM) network with an attention mechanism. This model was designed to perform sentiment analysis on financial news headlines, aiming to predict market movements based on the sentiments expressed in the news.

- **LSTM with Attention Mechanism**: The core of our model was an LSTM layer, which is effective in processing sequential data and capturing temporal dependencies. To enhance its capability, we integrated an attention mechanism. This addition was intended to allow the model to focus on the most informative parts of the text, effectively identifying key words or phrases that significantly influence sentiment prediction.
- **Sentiment Intensity Scoring**: We adopted a sentiment intensity scoring approach, which diverges from traditional categorical sentiment labels. This method allowed us to capture a more nuanced and continuous spectrum of sentiment, ranging from strongly negative to strongly positive, thereby providing a more refined analysis of sentiment in financial news. We used the VADER (Valence Aware Dictionary and sEntiment Reasoner) tool from the NLTK library.

### Attention Mechanism Analysis

A significant part of our methodology involved analyzing the outputs of the attention mechanism.

- **Extraction and Analysis**: We extracted the attention weights from the model, which provided insight into which parts of the text the model was focusing on when making predictions. By analyzing these weights, we identified the most influential words or phrases in the headlines, giving us a clearer understanding of what drives sentiment in financial news.

### **2. Results**

Our project's results encompassed both the performance metrics of the LSTM model with attention mechanism and the insights gained from the attention analysis.

### Model Performance Metrics

The model's performance was evaluated using standard classification metrics:

- **Accuracy**: The model achieved an accuracy of 50.5%, which indicates its ability to correctly classify the sentiment of the financial news headlines in relation to the market movements half the time.
- **Precision**: With a precision score of 48.3%, the model had a moderate rate of false positives, implying room for improvement in correctly predicting positive sentiments.
- **Recall**: The recall score of 50.5% mirrored the accuracy, suggesting an evenly distributed error rate across both classes.
- **F1 Score**: The F1 score, a balance between precision and recall, stood at 45.7%, indicating a need for improvement in the model's overall predictive performance.

### Attention Analysis Results

The attention mechanism highlighted key words and phrases that significantly influenced sentiment predictions. Some of the most attention-grabbing words included "halt," "mideast," "profits," and "emissions." These words suggest that the model was particularly attuned to economic terms, geopolitical references, financial performance indicators, and environmental factors.

### **3. Analysis**

The analysis of our results provides valuable insights into the model's performance and its ability to predict market movements based on financial news sentiment.

### Interpretation of Model Performance

- **Moderate Accuracy and Balanced Error Distribution**: The accuracy and recall scores suggest that the model's performance is just above random chance. This implies that while the model has learned to some extent to differentiate sentiments in financial news, its predictive power is limited.
- **Challenges in Precision**: The lower precision score indicates a tendency towards false positives, where the model incorrectly predicts positive sentiment. This could be due to the model overemphasizing certain words or failing to capture the overall sentiment accurately.
- **Need for Enhanced Sensitivity**: The F1 score, being below the desired threshold, points towards a need for the model to better balance precision and recall. This could involve improving its sensitivity to nuances in the financial news language.

### Insights from Attention Analysis

- **Relevance of Economic and Geopolitical Terms**: The attention mechanism's focus on specific words like "profits" and "mideast" suggests that the model is correctly identifying key terms that are likely significant in the context of financial news.
- **Impact of Environmental Factors**: The attention given to terms like "emissions" aligns with the increasing relevance of environmental concerns in financial decision-making, indicating the model's capability to capture contemporary market influencers.
- **Depth of Contextual Understanding**: While the model identifies key terms, its understanding of deeper context or the interplay of these terms within a complex news narrative remains a challenge.

### **4. Conclusions**

### Project Summary

This project aimed to predict market movements based on sentiment analysis of financial news using an LSTM model integrated with an attention mechanism. The approach combined advanced NLP techniques with deep learning to extract nuanced sentiment insights from news headlines.

### Strengths and Weaknesses

- **Strengths**: The model effectively identifies key words and phrases in financial news, demonstrating an understanding of significant market influencers.
- **Weaknesses**: The overall predictive accuracy is moderate, indicating a need for improvement in the model's ability to fully understand and classify complex financial sentiments.

### Limitations

- **Data Limitation**: The dataset, while comprehensive, may not fully represent the vast array of factors influencing stock markets. Additionally, the binary nature of the stock movement labels (up/down) oversimplifies the complex dynamics of market movements.
- **Model Complexity**: The current model may not sufficiently capture the intricacies of financial language, requiring more sophisticated or specialized NLP techniques.

### Future Work

- **Enhancing Data Quality**: Incorporating a wider range of financial news sources and more detailed market movement data could enrich the model's training and prediction capabilities.
- **Advanced NLP Models**: Exploring more advanced pre-trained models or custom NLP solutions tailored to financial language could enhance the model's understanding of sentiment.
- **Refining the Model Architecture**: Further tuning of the LSTM and attention mechanism, or experimenting with different model architectures, could improve the balance between precision and recall.
