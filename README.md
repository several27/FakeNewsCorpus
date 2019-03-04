[![OpenSources Data](https://img.shields.io/badge/Data-OpenSources-blue.svg)](http://opensources.co)

# Fake News Corpus

This is an open source dataset composed of millions of news articles mostly scraped from a curated list of 1001 domains from http://www.opensources.co/. Because the list does not contain many reliable websites, additionally [NYTimes](https://developer.nytimes.com/) and [WebHose English News Articles](https://webhose.io/datasets) articles has been included to better balance the classes. Corpus is mainly intended for use in training deep learning algorithms for purpose of fake news recognition. The dataset is still work in progress and for now, the public version includes only 9,408,908 articles (745 out of 1001 domains).

## Downloading 

The dataset is currently hosted on a public GCP Storage bucket and is about 9.1GB in size. To download it just click on the link below: 

    https://storage.googleapis.com/researchably-fake-news-recognition/news_cleaned_2018_02_13.csv.zip

or simply run the following command with installed wget.

    wget https://storage.googleapis.com/researchably-fake-news-recognition/news_cleaned_2018_02_13.csv.zip

## How was the corpus created?

The corpus was created by scraping (using [scrapy](https://github.com/scrapy/scrapy)) all the domains as provided by http://www.opensources.co/. Then all the pure HTML content was processed to extract the article text with some additional fields (listed below) using the [newspaper](https://github.com/codelucas/newspaper) library. Each article has been attributed the same label as the label associated with its domain. All the source code is available at [FakeNewsRecognition](https://github.com/several27/FakeNewsRecognition) and will be made more “usable” in the next few months. 

## Formatting

The corpus is formatted as a CSV and contains the following fields: 


- id
- domain
- type
- url
- content
- scraped_at
- inserted_at
- updated_at
- title
- authors
- keywords
- meta_keywords
- meta_description
- tags
- summary
- source (opensources, nytimes, or webhose)

**Available types**
More information on http://www.opensources.co 

| Type | Tag | Count (so far) | Description|
| ------------- |:-------------:|:-------------:|:-------------:|
| **Fake News** | fake | 928,083 | Sources that entirely fabricate information, disseminate deceptive content, or grossly distort actual news reports |
| **Satire** | satire | 146,080 | Sources that use humor, irony, exaggeration, ridicule, and false information to comment on current events. |
| **Extreme Bias** | bias | 1,300,444 | Sources that come from a particular point of view and may rely on propaganda, decontextualized information, and opinions distorted as facts. |
| **Conspiracy Theory** | conspiracy | 905,981 | Sources that are well-known promoters of kooky conspiracy theories. |
| **State News** | state | 0 | Sources in repressive states operating under government sanction. |
| **Junk Science** | junksci | 144,939 | Sources that promote pseudoscience, metaphysics, naturalistic fallacies, and other scientifically dubious claims. |
| **Hate News** | hate | 117,374 | Sources that actively promote racism, misogyny, homophobia, and other forms of discrimination. |
| **Clickbait** | clickbait | 292,201 | Sources that provide generally credible content, but use exaggerated, misleading, or questionable headlines, social media descriptions, and/or images. |
| **Proceed With Caution** | unreliable | 319,830 | Sources that may be reliable but whose contents require further verification. |
| **Political** | political | 2,435,471 | Sources that provide generally verifiable information in support of certain points of view or political orientations. |
| **Credible** | reliable | 1,920,139 | Sources that circulate news and information in a manner consistent with traditional and ethical practices in journalism (Remember: even credible sources sometimes rely on clickbait-style headlines or occasionally make mistakes. No news organization is perfect, which is why a healthy news diet consists of multiple sources of information). |

**List of domains**
You can find the full list of domains in `websites.csv`. 

## Limitations

The dataset was not manually filtered, therefore some of the labels might not be correct and some of the URLs might not point to the actual articles but other pages on the website. However, because the corpus is intended for use in training machine learning algorithms, those problems should not pose a practical issue.  

Additionally, when the dataset will be finalised (as for now only about 80% was cleaned and published), I do not intend to update it, therefore it might quickly become outdated for other purposes than content-based algorithms. However, any contributions are welcome!

## Contributing

Because there’s currently only myself working on this corpus, I’d really appreciate all the contributions. If you have found wrong labels associated with any articles, weirdly formatted content or URLs that are not pointing to any articles, feel free to post an issue with the problem and exact article id and I will do my best to respond promptly. Because of the size of the corpus, I could not host it on GitHub, therefore, unfortunately, for now, pull requests cannot be used to collaboratively work on the data, however, I’m open to any ideas 🙂 

## Acknowledgments
- [http://www.opensources.co/](http://www.opensources.co/)
- [NYTimes Developer](https://developer.nytimes.com/)
- [WebHose](https://webhose.io/datasets)
