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

The dataset contains **8,599 customer** reviews for **12 restaurants** located in the **Streatham area**. The reviews were extracted from Google Maps using the web scraping tool **Apify**. The dataset is comprehensive, featuring **93 columns** that provide a wide range of information, from metadata to sentiment-related details. Below is a unified overview of the most relevant columns used in this project, categorized into restaurant tags, location/context metadata, structured review feedback, and sentiment-related fields.

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

## Decision Visualization

![Dashboard](https://github.com/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants/blob/main/Images/vader_viz.png?raw=true)

![Dashboard](https://github.com/ShaikhBorhanUddin/Customer-Sentiment-Analysis-in-Streatham-Area-Restaurants/blob/main/Images/distilbert_viz.png?raw=true)

## Technology Used

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

