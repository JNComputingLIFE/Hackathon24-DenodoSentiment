# Hackathon24-DenodoSentiment

# Denodo Sentiment Analysis

This repository hosts a real-time sentiment analysis site that leverages data from **Oracle XE**, accessed via **Denodo**, and processed in **Google Colab**. The primary focus of this project is on data analysis using sentiment analysis to process customer feedback, specifically reviews about different banks. The goal is to provide insights into customer sentiment in real-time, reflecting changes in the data sources.

## 1. Data Set Overview

The dataset used for sentiment analysis consists of customer reviews for various banks, where each review provides valuable feedback regarding customer experiences with the banks.

### Sample Data:

| **author**  | **date**    | **address** | **bank** | **rating** | **review_title_by_user** | **review**                                                                                                                                                                | **bank_image**                                                                  | **rating_title_by_user** | **useful_count** |
|-------------|-------------|-------------|----------|------------|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|--------------------------|------------------|
| AMRENDRA T  | Mar 21, 2020 | New Delhi   | SBI      | 4          | Best saving               | State Bank Of India is located nearby in our area so I opened my saving account from that bank. Customer service was good, I got my bank statement on time...             | ![SBI Image](https://static.bankbazaar.com/images/common/bank-logo/sbi-4.png)  | Great!                   | 133              |
| BISHWA      | Mar 20, 2020 | Kolkata     | SBI      | 5          | Good service              | I have my salary account in SBI, when I applied for the card I got my statement on time. I am very much satisfied with the account...                                    | ![SBI Image](https://static.bankbazaar.com/images/common/bank-logo/sbi-4.png)  | Blown Away!              | 89               |
| SANTOSH     | Mar 20, 2020 | Hooghly     | Axis Bank| 5          | Excellent Service         | I am using Axis bank saving account for the past 3 years. Each transaction is safe and secure...                                                                          | ![Axis Bank](https://static.bankbazaar.com/images/common/bank-logo/axis.png)  | Blown Away!              | 48               |
| MAHADEV     | Mar 20, 2020 | Pune        | HDFC Bank| 5          | Excellent service         | I have my salary bank account in HDFC bank for many years. I got my bank statement on time...                                                                            | ![HDFC](https://static.bankbazaar.com/images/common/bank-logo/hdfc.png)       | Blown Away!              | 52               |

### Key Attributes:

- **author**: Name of the person giving the review.
- **date**: Date of the review.
- **address**: Location of the reviewer.
- **bank**: The bank associated with the review (e.g., SBI, Axis Bank).
- **rating**: Rating (out of 5) given by the reviewer.
- **review_title_by_user**: Title of the review provided by the user.
- **review**: Full review text provided by the user.
- **bank_image**: Image URL representing the bank.
- **rating_title_by_user**: Sentiment title assigned by the user (e.g., "Blown Away!").
- **useful_count**: Number of users who found the review helpful.

---

## 2. Methods of Analyzing the Dataset

There are two primary ways to analyze the dataset for sentiment analysis: **General Overview of All Banks** and **Analysis of Specific Banks**.

### 2.1 General Overview of All Banks

For a broader view, we analyze the dataset across **all banks** to determine the overall sentiment trends. This approach helps in understanding how customers feel across different banks in general. We aggregate and visualize the **useful_count**, **ratings**, and sentiment classification (positive/negative) for each review.

- **Key insights**: Overall satisfaction trends, distribution of positive and negative sentiment, most frequently mentioned words, and overall helpfulness (useful_count).

### 2.2 Analysis of Specific Banks

Alternatively, the dataset can be filtered to focus on specific banks. This analysis zooms into reviews of one bank, allowing for deeper insights into customer sentiment for a particular institution. For example, by filtering for **SBI** or **Axis Bank**, you can explore:
- The most useful reviews for each bank.
- Words that frequently appear in the most useful reviews.
- The sentiment breakdown for each bank.

This method provides granular insights into customer experiences with specific banks.

---

## 3. Architecture: Real-time Data Access via Denodo Virtualization

### 3.1 Data Flow Overview

The sentiment analysis system is designed to be **real-time**, processing data as it changes in the database (Oracle XE) and reflecting those changes in the sentiment analysis results. Here is a step-by-step breakdown of the architecture:

1. **Oracle XE Database**: This is the source of the raw data, containing customer reviews and related information for different banks.
2. **Denodo Virtualization**: Denodo acts as an abstraction layer, providing **real-time data virtualization** between Oracle XE and the Google Colab environment. It pulls data from Oracle XE, processes it, and serves it to the Colab instance without physically moving the data.
3. **Google Colab**: Colab is used for the data analysis part, where Python libraries (such as `nltk`, `pandas`, `seaborn`, `matplotlib`) are used to:
   - Perform **sentiment analysis** using `SentimentIntensityAnalyzer`.
   - **Visualize** sentiment trends and review details (e.g., most useful reviews, most common words in reviews).
   - Analyze both **positive and negative sentiment** based on useful count metrics and other relevant attributes.

### 3.2 Real-Time Integration

The Denodo layer enables real-time data access, so the sentiment analysis model reflects the latest data from Oracle XE as soon as it is updated in the database. This ensures that:
- **New reviews** are incorporated into the sentiment analysis instantly.
- **Real-time sentiment trends** and visualizations are available for immediate analysis.

### 3.3 Data Flow:

- **Step 1**: Data from **Oracle XE** is pulled into **Denodo** for virtualization.
- **Step 2**: The virtualized data is processed by the **Google Colab** instance.
- **Step 3**: The sentiment analysis is performed in **real-time** based on the latest data available from Denodo.
- **Step 4**: Visualizations of sentiment, useful counts, and review analysis are presented to the user.

This architecture ensures the system is **scalable**, **flexible**, and capable of providing up-to-the-minute insights based on the most recent data available.

---

## Conclusion

This repository offers a powerful sentiment analysis engine that integrates data from Oracle XE, virtualized via Denodo, and processed through Google Colab. The system enables **real-time data access** and provides actionable insights into customer sentiment across different banks. The analysis can be tailored for specific banks or provide a general overview, making this tool flexible for different use cases.

For a detailed walkthrough on setting up and running this project, please refer to the **Installation** and **Usage** sections in the repository.

---

