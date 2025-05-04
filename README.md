# Customer Sentiment Analysis in Streatham Area Restaurants
<p align="left">
  <img src="https://img.shields.io/badge/Made%20With-Colab-blue?logo=googlecolab&logoColor=white&label=Made%20With" alt="Made with Colab">
  <img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License: MIT">
  <img src="https://img.shields.io/github/repo-size/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants" alt="Repo Size">
  <img src="https://img.shields.io/github/last-commit/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants" alt="Last Commit">
  <img src="https://img.shields.io/github/issues/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants" alt="Issues">
  <img src="https://img.shields.io/badge/Sentiment%20Analysis-NLP-blueviolet?logo=spacy" alt="Sentiment Analysis: NLP">
  <img src="https://img.shields.io/badge/Result%20Visualization-NLTK-orange?logo=nltk" alt="Result Visualization: NLTK">
  <img src="https://img.shields.io/badge/Data%20Visualization-Matplotlib%20%7C%20Seaborn-yellow?logo=python" alt="Data Visualization: Python">
  <img src="https://img.shields.io/badge/Web%20Scraping-Apify-purple?logo=apify" alt="Web Scraping: Apify">
  <img src="https://img.shields.io/badge/Version%20Control-Git-orange?logo=git" alt="Version Control: Git">
  <img src="https://img.shields.io/badge/Host-GitHub-black?logo=github" alt="Host: GitHub">
  <img src="https://img.shields.io/github/forks/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants?style=social" alt="Forks">
  <img src="https://img.shields.io/badge/Project-Completed-brightgreen" alt="Project Status">
</p>

![Dashboard](https://github.com/ShaikhBorhanUddin/SW16-Sentiment-Analysis/blob/main/Images/title_mod.png?raw=true)

## Project Overview

In the age of online reviews, star ratings are often treated as the definitive metric of customer satisfaction. But the reality is far more nuanced—what a customer *writes* often tells a richer, more emotional, and more actionable story than what they *click*. A 5-star rating might hide subtle complaints, while a 3-star review could still express strong loyalty and praise.

This project, **Customer Sentiment Analysis in Streatham Area Restaurants**, aims to go beyond surface-level metrics by applying Natural Language Processing (NLP) techniques to real Google Map reviews of 12 restaurants in the Streatham area. By combining structured data (like star ratings, review context, and categories) with unstructured review text, the project reveals:

- What customers *really* feel, not just what they rate.
- Which aspects of dining (e.g., service, noise, wait time) matter most to sentiment.
- How sentiment varies across restaurant types, time, and geography.
- The value of sentiment proxies where text is missing, using models like VADER and DistilBERT.

![Dashboard](https://github.com/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants/blob/main/Images/restaurants_loc.png?raw=true)

This deep dive into public opinion transforms scattered reviews into powerful insights for business owners, local analysts, and NLP researchers alike. It illustrates that text isn't just an accessory to a star—it’s often the main dish.

## Dataset

The [dataset](https://github.com/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants/blob/main/Dataset/combined_df.csv) contains **8,599 customer** reviews for **12 restaurants** located in the **Streatham area**. The individual reviews for every restaurants were extracted from Google Maps and merged using web scraping tool **Apify**. The dataset is comprehensive, featuring **93 columns** that provide a wide range of information, from metadata to sentiment-related details. Below is a unified overview of the most relevant columns used in this project, categorized into restaurant tags, location/context metadata, structured review feedback, and sentiment-related fields.

| Column Name                                     | Description                                                                                                                                     |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| **🍽️ Categories & Tags**                       |                                                                                                                                                 |
| `categoryName`                                 | The main business classification of the restaurant (e.g., "Cafe", "Fine Dining"). Helps segment sentiment by business type.                    |
| `categories/0` ~ `categories/9`                | A list of subcategories or tags describing cuisine type (e.g., "Italian", "Vegan"), dining style, ambiance, or amenities.                      |
|                                                |                                                                                                                                                 |
| **📍 Location & Metadata**                      |                                                                                                                                                 |
| `title`                                        | The **name of the restaurant** being reviewed. Serves as a primary identifier when grouping or filtering reviews.                              |
| `postalCode`                                   | Postal code of the restaurant's physical location. Useful for regional sentiment trends and geographic clustering.                             |
| `location/lat`, `location/lng`                 | Latitude and longitude coordinates of the restaurant. Enables map-based visualizations and geospatial analysis.                                |
| `publishAt`, `publishedAtDate`                 | Timestamps for when the review was posted. Enables time-based trend analysis (e.g., seasonal dips or spikes in sentiment).                     |
|                                                |                                                                                                                                                 |
| **🧾 Structured Review Feedback**               |                                                                                                                                                 |
| `reviewContext/Meal type`                      | Indicates the meal during which the reviewer dined (e.g., "Lunch", "Dinner"). Useful for segmenting sentiment based on meal context.           |
| `reviewContext/Noise level`                    | Describes how noisy the environment was during the visit (e.g., "Quiet", "Very Loud"). Important for assessing the comfort aspect.             |
| `reviewContext/Parking space`                  | Indicates whether parking was available and sufficient. Reflects on convenience and accessibility.                                              |
| `reviewContext/Price per person`               | Approximate cost per diner as reported. Can help correlate satisfaction or dissatisfaction with perceived value.                               |
| `reviewContext/Recommendation for vegetarians` | A boolean or categorical indicator of how suitable the menu is for vegetarians. Important for dietary-specific sentiment analysis.             |
| `reviewContext/Service`                        | Direct rating or commentary on service quality (e.g., attentiveness, speed). Helps in aspect-based analysis under "Service".                   |
| `reviewContext/Wait time`                      | Reviewer-reported time before being served or seated. Affects sentiment regarding efficiency and service experience.                           |
| `reviewDetailedRating/Atmosphere`              | A specific numerical rating for ambiance, décor, music, and overall vibe. Central to the "Atmosphere" aspect in sentiment modeling.            |
| `reviewDetailedRating/Food`                    | Numeric score for food quality (e.g., taste, presentation). A direct input into aspect-level sentiment under "Food Quality".                   |
| `reviewDetailedRating/Service`                 | Numeric score for service experience (e.g., staff friendliness, professionalism). Complements `reviewContext/Service` for stronger analysis.   |
|                                                |                                                                                                                                                 |
| **💬 Sentiment Input Fields**                   |                                                                                                                                                 |
| `text`                                         | The full body of the written review. Main source for sentiment classification and aspect-based opinion mining.                                 |
| `name`                                         | The **reviewer's name** or username. Useful for tracking repeat reviewers or studying reviewer credibility and bias patterns.                  |
| `stars`                                        | Star rating given by the reviewer (usually 1 to 5). Often used as a weak label for supervised sentiment model training.                        |
| `totalScore`                                   | The overall average Google rating for the restaurant. Useful as a benchmark to compare individual review sentiment with business reputation.    |

There are **3,010** null values in the `text` column out of a total of **8,599** reviews, meaning that approximately **35%** of the reviews lack textual content. However, all 3,010 entries with a null text column do have a star rating. Including a **sentiment proxy mapping** for the reviews with null text entries (based on their star ratings) will provide a complete sentiment analysis across all 8,599 reviews. The process of sentiment proxy mapping will be discussed in the Experiments section.

## Folder Structure
```bash
Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants/
|
├── 📁 Dataset/                    # Raw and processed datasets (cav format)
│
├── 📁 Src/                        # Dataset formation and model deployment
│
├── 📁 Images/                     # Output plots and charts
│
├── README.md                      # Project overview and documentation
|
├── requirements.txt               # Python dependencies
|
└── Licence                        # License file (MIT recommended)
```
Some .ipynb files may not run properly or output truncated in github environmet. So, original source code files from google drive are linked here.
- Dataset formation and visualization : [Link](https://colab.research.google.com/drive/1yUttPCkKmx5YWfSr_RveHCZP1sJaQcs3?usp=sharing)
- VADER Model : [Link](https://colab.research.google.com/drive/1byniC8gn1-SPfsdMAXmdpCEHlDQnilLp?usp=sharing)
- DistilBERT Model : [Link](https://colab.research.google.com/drive/10GSSzT5HxyQ3IyKSWDgKHR9Ybi3H2sw2?usp=sharing)

## Experiments

The sentiment analysis experiment followed a clear and systematic approach to processing and interpreting restaurant reviews. First, sentiment models were loaded: **VADER** from the NLTK library for lexicon-based scoring, and **DistilBERT** from the Hugging Face Transformers library for deep learning-based classification. These models were applied to all reviews containing non-null text entries, with each review classified into positive, neutral, or negative sentiment categories based on model predictions.

For reviews that lacked textual content, a proxy sentiment mapping strategy was employed using the star rating field as a surrogate for sentiment. Specifically:

- Reviews with 1–2 stars were treated as `negative`

- 3-star reviews were labeled `neutral`

- 4–5 star reviews were marked `positive`

Once both model-generated and proxy-derived sentiments were obtained, they were merged into a single sentiment label for each review to ensure full coverage. Sentiments were then aggregated by restaurant using the title column, which identified the venue each review was associated with. Finally, a sentiment summary was produced, showing sentiment distribution and positive sentiment ratio per restaurant, which served as a measure of customer satisfaction.

The models were fine-tuned and trained on NVIDIA A100 GPU in Google Colab. However, given the relatively small size of the dataset (approximately 8,600 entries), this was ultimately excessive—CPU execution would have been sufficient for this task.

## Result Analysis & Visualization

In this section, the results for both models will be analyzed. The table below presents the sentiment analysis outcomes from the VADER model, which offers a lexicon-based perspective on how each restaurant is perceived by customers based on the content of the reviews.

| Restaurant Title                      | Negative | Neutral | Positive | Total | Positive Ratio |
|--------------------------------------|----------|---------|----------|-------|----------------|
| Roots Restaurant                     | 19       | 24      | 693      | 736   | 0.941576       |
| Paratha Inn (Streatham)              | 7        | 13      | 291      | 311   | 0.935691       |
| SW16 Bar & Kitchen                   | 27       | 25      | 677      | 729   | 0.928669       |
| Italian Bistro (Italian Restaurant)  | 32       | 41      | 772      | 845   | 0.913609       |
| Putt Putt & Karaoke Bar              | 58       | 40      | 693      | 791   | 0.876106       |
| La Casita                            | 45       | 106     | 785      | 936   | 0.838675       |
| Slurp                                | 67       | 73      | 649      | 789   | 0.822560       |
| Porky's Wine Bar                     | 33       | 57      | 341      | 431   | 0.791183       |
| Nando's Streatham                    | 144      | 192     | 1097     | 1433  | 0.765527       |
| Starbucks Coffee                     | 60       | 43      | 302      | 405   | 0.745679       |
| Marinatto                            | 31       | 94      | 309      | 434   | 0.711982       |
| KFC London                           | 216      | 161     | 382      | 759   | 0.503294       |

The VADER sentiment analysis (above table) shows that Roots Restaurant and Paratha Inn (Streatham) are the top performers, with over 93% of reviews being positive. These restaurants consistently deliver satisfying experiences with minimal negative feedback. SW16 Bar & Kitchen and Italian Bistro also perform strongly, though with slightly more mixed opinions. Mid-range performers like Putt Putt & Karaoke Bar, La Casita, and Slurp still receive mostly positive feedback but show more variability. These restaurants may offer good experiences overall but likely struggle with consistency in service or food quality. On the lower end, Nando’s Streatham, Starbucks Coffee, and Marinatto show increasing levels of neutral and negative sentiment. The most concerning is KFC London, where positive sentiment barely exceeds 50%, pointing to significant customer dissatisfaction that likely stems from poor service, food quality, or both. In summary, while several restaurants excel in customer sentiment, a few face challenges that should be addressed to improve their overall reputation.

To provide a deeper, context-aware interpretation of customer sentiment, the same dataset was analyzed using the DistilBERT model—a transformer-based approach that captures nuanced expressions in reviews.

| Restaurant Title                      | Negative | Neutral | Positive | Total | Positive Ratio |
|--------------------------------------|----------|---------|----------|-------|----------------|
| Paratha Inn (Streatham)              | 14       | 0       | 297      | 311   | 0.954984       |
| Roots Restaurant                     | 34       | 7       | 695      | 736   | 0.944293       |
| SW16 Bar & Kitchen                   | 62       | 9       | 658      | 729   | 0.902606       |
| Italian Bistro (Italian Restaurant)  | 79       | 5       | 761      | 845   | 0.900592       |
| Putt Putt & Karaoke Bar              | 98       | 8       | 685      | 791   | 0.865992       |
| La Casita                            | 122      | 26      | 788      | 936   | 0.841880       |
| Slurp                                | 113      | 35      | 641      | 789   | 0.812421       |
| Porky's Wine Bar                     | 53       | 36      | 342      | 431   | 0.793503       |
| Nando's Streatham                    | 256      | 86      | 1091     | 1433  | 0.761340       |
| Starbucks Coffee                     | 102      | 21      | 282      | 405   | 0.696296       |
| Marinatto                            | 128      | 4       | 302      | 434   | 0.695853       |
| KFC London                           | 314      | 70      | 375      | 759   | 0.494071       |

The DistilBERT sentiment analysis (above table) presents a refined but slightly stricter view compared to VADER, highlighting more critical customer perceptions. Paratha Inn (Streatham) and Roots Restaurant remain the top performers, each with over 94% positive sentiment. These restaurants continue to demonstrate consistent quality and strong customer satisfaction, even under the more nuanced scrutiny of a transformer-based model. SW16 Bar & Kitchen and Italian Bistro follow closely, maintaining high positive ratios around 90%. This indicates that despite the stricter classification, their customer experiences are still largely favorable. These venues likely benefit from strong service and food quality that stand up well to detailed textual analysis. In the mid-range, Putt Putt & Karaoke Bar, La Casita, and Slurp show slightly reduced positive ratios compared to VADER, with more critical sentiment identified by DistilBERT. While still mostly positive, the model picks up on more nuanced dissatisfaction, likely tied to inconsistent service or environment. Toward the bottom, Nando’s Streatham, Starbucks Coffee, and Marinatto reveal further dips in sentiment. These establishments have significant portions of negative or neutral reviews, suggesting recurring issues or underwhelming experiences. KFC London stands out again as the poorest performer, with less than half of the reviews rated as positive. This confirms serious shortcomings in customer satisfaction, especially under the deeper linguistic interpretation of a transformer model. 

The distinctions between the results of these two models are effectively highlighted in the pie charts below. The left image showcases the VADER model, while the right image features the DistilBERT model, making it easy to compare their performances.

<p align="center">
  <img src="https://github.com/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants/blob/main/Images/pie_vader.png?raw=true" alt="VADER Sentiment Analysis" width="49%" />
  <img src="https://github.com/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants/blob/main/Images/pie_distilbert.png?raw=true" alt="DistilBERT Sentiment Analysis" width="49%" />
</p>

Overall, DistilBERT amplifies sentiment polarity, providing sharper insight into where customer experience truly excels and where it falls short. The top restaurants remain strong, while those in the lower tier appear even more in need of attention.

## Decision Visualization

In the Visualization section, the three VADER and distilBERT sentiment breakdown plots provide insight into how these models interprets individual reviews.

![Dashboard](https://github.com/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants/blob/main/Images/vader_viz.png?raw=true)

The first and third reviews (Entry Rows: 0 and 4612) have compound scores of 0.95, indicating highly positive sentiment overall. However, both display a greater neutral score (0.55 and 0.54 respectively) than positive (0.45 and 0.46), showing that VADER sometimes classifies parts of strongly positive text as neutral due to its rule-based approach. The second review (Entry Row: 3022) has a compound score of 0.60, which is still positive, but lower in intensity. Here, the model assigns 80% to positive sentiment, reflecting a clearer alignment between the compound score and the label distribution. These visualizations suggest that while VADER effectively identifies positive sentiment overall, it may underrepresent positivity when neutral language is present, highlighting its limitations in capturing nuance compared to transformer models like DistilBERT.

![Dashboard](https://github.com/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants/blob/main/Images/distilbert_viz.png?raw=true)

The three DistilBERT sentiment visualizations (above 3 images) show consistent and decisive classifications across all selected reviews (Entry Rows: 2301, 4022, and 999). Each review is labeled as POSITIVE with a confidence score of 1.00, and all sentiment probability is assigned entirely to the positive class, with 0.00 for both negative and neutral. This reflects DistilBERT’s ability to interpret contextual cues and nuanced expressions more confidently than VADER. Unlike VADER, which may split scores between neutral and positive even in clearly favorable reviews, DistilBERT shows no ambiguity. It identifies strong positive sentiment with full certainty, which indicates a more assertive and context-aware classification style, especially useful for business insights drawn from natural customer language.

## Key Takeaways

- Roots Restaurant and Paratha Inn are standout performers — their sentiment ratios show strong and consistent customer satisfaction.

- KFC London and Marinatto need urgent attention in service quality or experience optimization.

- Mid-range performers like Slurp and La Casita may benefit from focusing on specific aspects (e.g., wait times, food consistency) revealed in detailed reviews.

## Technology Used

This project integrates a range of modern tools and frameworks to perform comprehensive sentiment analysis on restaurant reviews, from data acquisition to deep learning-based interpretation and visualization.

- **👨‍💻 Programming Language:**
The entire workflow is developed using Python 3.10+, due to its rich ecosystem of libraries for natural language processing, machine learning, and data visualization.

- **🌐 Web Scraping:**
Apify was employed to scrape restaurant reviews and metadata efficiently. Its automation capabilities enabled large-scale, structured data collection from online platforms.

- **🧠 NLP Frameworks:**
Two different natural language processing techniques were used to assess sentiment:

   - VADER (Valence Aware Dictionary and sEntiment Reasoner), a lexicon and rule-based sentiment analysis tool optimized for social text.

   - DistilBERT, a transformer-based, context-aware sentiment classifier fine-tuned on large datasets to interpret nuanced expressions.

- **📚 Deep Learning & Data Handling:**
The backend sentiment classification, especially with DistilBERT, utilized:

   - TensorFlow and Keras for loading and applying pre-trained transformer models.

   - NumPy and Pandas for efficient numerical operations and structured data manipulation.

- **🗣️ NLTK Toolkit:**
Specifically, SentimentIntensityAnalyzer from NLTK was used for implementing VADER sentiment scoring, enabling quick polarity detection of review texts.

- **📊 Data Visualization:**
Matplotlib and Seaborn were used to create sentiment distribution plots, model breakdown visualizations, and other interpretive graphics to support the analysis.

- **💻 Development Environment:**
All development and experimentation were carried out on Google Colab Pro, providing access to high speed GPUs and a collaborative environment for executing and documenting experiments.

## Practical Applications

This project isn't just about modeling sentiment—it brings real-world insights into customer satisfaction and business profiling within the Streatham restaurant scene. Below are key ways the results can be applied in the real world:

| **Use Case**                                |**Description**                                                                                                                                                  |
|----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 📊 **Business Intelligence for Owners** | Restaurant managers can identify what customers praise (e.g., service, ambiance) or complain about (e.g., noise, price) and make data-driven improvements.   |
| 🌍 **Local Dining Trend Analysis**      | Urban planners, bloggers, or local foodies can discover how sentiment varies by restaurant type, area, or over time—fueling guides, reports, or investments. |
| 🔍 **Customer Feedback Clustering**    | Reviews are automatically grouped by recurring themes like "slow service", "delicious vegan options", or "long wait time" for faster interpretation.         |
| ⭐ **Rating-Sentiment Discrepancy**     | By comparing star ratings with textual sentiment, the system can flag cases where customers left 4+ stars but expressed dissatisfaction—or vice versa.       |
| 🧠 **NLP Model Training Dataset**       | The labeled reviews (via VADER/DistilBERT) serve as valuable training or evaluation data for sentiment models in other domains or future fine-tuning tasks.  |
| 📍 **Geo-Sentiment Heatmapping**       | Using geolocation data (`lat`, `lng`), one can build maps that show which parts of Streatham are perceived most positively or negatively by diners.          |
| 📆 **Temporal Sentiment Insights**     | Tracking sentiment over months/years helps restaurants evaluate changes like renovations, new menus, or staffing decisions in context.                       |
| 🏷️ **Category-Based Sentiment Insights** | Tags like "Takeaway", "Casual Dining", or "Romantic" help compare sentiment across different restaurant types, enhancing local competitive analysis.         |

## Licence

This project is licensed under the MIT License — a permissive open-source license that allows reuse, modification, and distribution with attribution. You are free to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the project, provided that the original copyright and license notice are included in all copies or substantial portions of the software.

For more details, refer to the [Licence](https://github.com/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants/blob/main/Licence) file in this repository.

## Contact

If you have any questions or would like to connect, feel free to reach out!

**Shaikh Borhan Uddin**  
📧 Email: [`shaikhborhanuddin@gmail.com`](mailto:shaikhborhanuddin@gmail.com)  
🔗 [`LinkedIn`](https://www.linkedin.com/in/shaikh-borhan-uddin-905566253/)  
🌐 [`Portfolio`](https://github.com/ShaikhBorhanUddin)

Feel free to fork the repository, experiment with new models, datasets or add visualizations!

