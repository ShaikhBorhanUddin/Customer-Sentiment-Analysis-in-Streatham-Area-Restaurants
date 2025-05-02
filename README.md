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

There are **3,010** null values in the `text` column out of a total of **8,599** reviews, meaning that approximately **35%** of the reviews lack textual content. However, all 3,010 entries with a null text column do have a star rating. Including a sentiment proxy mapping for the reviews with null text entries (based on their star ratings) will provide a complete sentiment analysis across all 8,599 reviews. The process of sentiment proxy mapping will be discussed in the Experiments section.

## Folder Structure

## Project Workflow

## Experiments

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

The DistilBERT sentiment analysis (above table) presents a refined but slightly stricter view compared to VADER, highlighting more critical customer perceptions. Paratha Inn (Streatham) and Roots Restaurant remain the top performers, each with over 94% positive sentiment. These restaurants continue to demonstrate consistent quality and strong customer satisfaction, even under the more nuanced scrutiny of a transformer-based model. SW16 Bar & Kitchen and Italian Bistro follow closely, maintaining high positive ratios around 90%. This indicates that despite the stricter classification, their customer experiences are still largely favorable. These venues likely benefit from strong service and food quality that stand up well to detailed textual analysis. In the mid-range, Putt Putt & Karaoke Bar, La Casita, and Slurp show slightly reduced positive ratios compared to VADER, with more critical sentiment identified by DistilBERT. While still mostly positive, the model picks up on more nuanced dissatisfaction, likely tied to inconsistent service or environment. Toward the bottom, Nando’s Streatham, Starbucks Coffee, and Marinatto reveal further dips in sentiment. These establishments have significant portions of negative or neutral reviews, suggesting recurring issues or underwhelming experiences. KFC London stands out again as the poorest performer, with less than half of the reviews rated as positive. This confirms serious shortcomings in customer satisfaction, especially under the deeper linguistic interpretation of a transformer model. The distinctions between the results of these two models are effectively highlighted in the pie charts below. The left image showcases the VADER model, while the right image features the DistilBERT model, making it easy to compare their performances.

![Dashboard](https://github.com/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants/blob/main/Images/pie_vader.png?raw=true)
![Dashboard](https://github.com/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants/blob/main/Images/pie_distilbert.png?raw=true)


Overall, DistilBERT amplifies sentiment polarity, providing sharper insight into where customer experience truly excels and where it falls short. The top restaurants remain strong, while those in the lower tier appear even more in need of attention.

## Decision Visualization

In the Visualization section, the three VADER and distilBERT sentiment breakdown plots provide insight into how these models interprets individual reviews.

![Dashboard](https://github.com/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants/blob/main/Images/vader_viz.png?raw=true)

The first and third reviews (Entry Rows: 0 and 4612) have compound scores of 0.95, indicating highly positive sentiment overall. However, both display a greater neutral score (0.55 and 0.54 respectively) than positive (0.45 and 0.46), showing that VADER sometimes classifies parts of strongly positive text as neutral due to its rule-based approach. The second review (Entry Row: 3022) has a compound score of 0.60, which is still positive, but lower in intensity. Here, the model assigns 80% to positive sentiment, reflecting a clearer alignment between the compound score and the label distribution. These visualizations suggest that while VADER effectively identifies positive sentiment overall, it may underrepresent positivity when neutral language is present, highlighting its limitations in capturing nuance compared to transformer models like DistilBERT.

![Dashboard](https://github.com/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants/blob/main/Images/distilbert_viz.png?raw=true)

The three DistilBERT sentiment visualizations (above 3 images) show consistent and decisive classifications across all selected reviews (Entry Rows: 2301, 4022, and 999). Each review is labeled as POSITIVE with a confidence score of 1.00, and all sentiment probability is assigned entirely to the positive class, with 0.00 for both negative and neutral. This reflects DistilBERT’s ability to interpret contextual cues and nuanced expressions more confidently than VADER. Unlike VADER, which may split scores between neutral and positive even in clearly favorable reviews, DistilBERT shows no ambiguity. It identifies strong positive sentiment with full certainty, which indicates a more assertive and context-aware classification style, especially useful for business insights drawn from natural customer language.

## Technology Used

This project leverages several NLP frameworks, along with essential web scrapping, data processing and visualization libraries, which are listed here.
- Programming Language: `Python 3.10+`
- Web Scrapping: `Apify`
- NLP Frameworks: `VADER` `DistilBERT`
- Deep Learning Frameworks: `TensorFlow` `Keras` `NumPy` `Pandas`
- NLTK: `sentimentIntensityAnalyzer`
- Visualization: `Matplotlib` `Seaborn`
- Development Environment: `Google Colab`

## Practical Application

## Licence

This project is licensed under the MIT License — a permissive open-source license that allows reuse, modification, and distribution with attribution. You are free to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the project, provided that the original copyright and license notice are included in all copies or substantial portions of the software.

For more details, refer to the LICENSE file in this repository.

## Contact

If you have any questions or would like to connect, feel free to reach out!

**Shaikh Borhan Uddin**  
📧 Email: [`shaikhborhanuddin@gmail.com`](mailto:shaikhborhanuddin@gmail.com)  
🔗 [`LinkedIn`](https://www.linkedin.com/in/shaikh-borhan-uddin-905566253/)  
🌐 [`Portfolio`](https://github.com/ShaikhBorhanUddin)

Feel free to fork the repository, experiment with new models, datasets or add visualizations!

