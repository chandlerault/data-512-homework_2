# data-512-homework_2

## Summary

This repository is the code, data, and analysis for wikipedia articles of cities in the U.S. The files here are aim to facilitate reproducibility of my findings. Additionally, below can be found information for installation so that packages and versions of the same software can be used.

## Wikimedia

This analysis uses the wikimedia API which terms of use can be accessed [here](https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions). Additionally, the [API documentation](https://wikimedia.org/api/rest_v1/#/Pageviews%20data/get_metrics_pageviews_per_article__project___access___agent___article___granularity___start___end_) and [endpoint](https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews) can be found at the given links.

This project also uses [ORES Liftwing](https://ores.wikimedia.org/docs#/default/list_available_scores_v3_scores_get) for ML predictions of article scores.

To access these API's, it may be necessary to create an account and generate API keys which can be done [here](https://api.wikimedia.org/wiki/Special:AppManagement).

## Files

The code for generating the files for analysis can be found in wikipedia.ipynb and the files for the actual analysis can be found in analysis.ipynb. Wikipedia.ipynb generates a file called wp_scored_city_articles_by_state.csv which contains all the cities, revision id's, regions, state populations, and ORES quality scores.

Population.csv contains population breakdowns by state and is generated from census bureau data found [here](https://www.census.gov/data/tables/time-series/demo/popest/2020s-state-total.html#v2022).

"US States by Region - US Census Bureau - Sheet1.csv" contains a breakdown of what region each state falls into and the original file can be found [here](https://docs.google.com/spreadsheets/d/14Sjfd_u_7N9SSyQ7bmxfebF_2XpR8QamvmNntKDIQB0/edit?usp=sharing).

A breakdown of all articles looked at can be found in "us_cities_by_state_SEPT.2023.csv" and is sourced from [here](https://drive.google.com/file/d/1khouDmMaZyKo0y5WkFj4lu7g8o35x_98/view?usp=sharing)

## Considerations

Generating the quality predictions can take some time due to API restrictions. It would be wise to budget 45 minutes to rerun the wikipedia.ipynb notebook.

Additionally, you will need to add your own access token into the notebook as well.

## Installation

To utilize this repository, you must first clone it:

```bash
git clone https://github.com/Dreamweaver2k/data-512-homework_2.git
cd ./data-512-homework_2
```

Now, it is necessary to download the proper environment. Please make sure you have [conda](https://conda.io/projects/conda/en/latest/index.html) installed on your system for the next step.

```bash
conda env create -n <your-environment-name> -f environment.yml
```

## Usage

The wikipedia.ipynb file utilizes the Wikimedia API to collect information for files the U.S. cities csv. The analysis.ipynb loads the data generated from the previous file and creates tables for analysis.

## Research Implications

I was surprised by a number of the results found in analysis.ipynb, specifically in the representation in both per capita articles and per capita quality articles for small states like Wyoming and Alaska. I also expected a bias towards the east and west coasts, but the highest per capita region was the midwest which surprised me.

> **1. What biases did you expect to find in the data (before you started working with it), and why?**

I expected a few things going into this project. First, I expected that the original 13 colonies and some of the older states on the east coast to have both more articles and more quality articles. This is because during my time in New Jersey I noticed that there are many small burrows which I thought could drive up total numbers, but I am also aware that the 13 colonies have the longest history which could lead to there being more to write about which in turn leads to a higher quality prediciton. Additionally, I expected that western states would have more high quality articles since there are many tech people on the west coast who I deemed more likely to write for wikipedia.

> **2. What (potential) sources of bias did you discover in the course of your data processing and analysis?**

I am not sure that the tables I created revealed anything revolutionary about bias, but when I did an empircal dive into the data, I did see some possible evidence of bias. I randomly looked through some articles and it was fairly common that cities I had never heard of and that did not have subjectively good wikipedia pages were given a good grade by the ML model. This leads me to believe that the model has a bias in rating articles higher. This would mean that states or regions with more articles would probably have more "quality" articles too due to false positives.

> **3. How might a researcher supplement or transform this dataset to potentially correct for the limitations/biases you observed?**

I think one way a researcher could supplement this data is by crawling the individual pages talk section and pulling the human annotations where possible. Additionally, one could add in metrics like word count or encode common sections to capture the actual contents of the articles.

## License

MIT License
