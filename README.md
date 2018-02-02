[![OpenSources Data](https://img.shields.io/badge/Data-OpenSources-blue.svg)](http://opensources.co)

# Fake News Corpus

This is an open source dataset composed of millions of news articles scraped from a curated list of 1001 domains from http://www.opensources.co/. Corpus is mainly intended for use in training deep learning algorithms for purpose of fake news recognition. The dataset is still work in progress and for now, the public version includes only around a million of articles (out of predicted at least 10 million) from 422 domains (out of 1001). 

## Downloading 

The dataset is currently hosted on a public S3 bucket and is about 1.1GB in size. 

    s3://researchably-fake-news-recognition/public_corpus/news_cleaned_2018_01_29.csv.zip

To download it simple run the following command with installed [awscli](https://github.com/aws/aws-cli) and configured with a (free) AWS account.

    aws s3 cp s3://researchably-fake-news-recognition/public_corpus/news_cleaned_2018_01_29.csv.zip news_corpus.csv

## How was the corpus created?

The corpus was simply created by scraping (using [scrapy](https://github.com/scrapy/scrapy)) all the domains as provided by http://www.opensources.co/. Then all the pure HTML content was processed and the content and the fields below were extracted using a great [newspaper](https://github.com/codelucas/newspaper) library. Each article has been attributed the same label as the label associated with its domain. All the source code is available at [FakeNewsRecognition](https://github.com/several27/FakeNewsRecognition) and will be made more “usable” in the next few months. 

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

**Available types**
More information on http://www.opensources.co 


- **Fake News (tag fake)** Sources that entirely fabricate information, disseminate deceptive content, or grossly distort actual news reports
- **Satire (tag satire)** Sources that use humor, irony, exaggeration, ridicule, and false information to comment on current events.
- **Extreme Bias (tag bias)** Sources that come from a particular point of view and may rely on propaganda, decontextualized information, and opinions distorted as facts.
- **Conspiracy Theory (tag conspiracy):** Sources that are well-known promoters of kooky conspiracy theories.
- **Rumor Mill (tag rumor)** Sources that traffic in rumors, gossip, innuendo, and unverified claims.
- **State News (tag state)** Sources in repressive states operating under government sanction.
- **Junk Science (tag junksci)** Sources that promote pseudoscience, metaphysics, naturalistic fallacies, and other scientifically dubious claims.
- **Hate News (tag hate)** Sources that actively promote racism, misogyny, homophobia, and other forms of discrimination.
- **Clickbait (tag clickbait)** Sources that provide generally credible content, but use exaggerated, misleading, or questionable headlines, social media descriptions, and/or images.
- **Proceed With Caution (tag unreliable)** Sources that may be reliable but whose contents require further verification.
- **Political (tag political)** Sources that provide generally verifiable information in support of certain points of view or political orientations.
- **Credible (tag reliable)** Sources that circulate news and information in a manner consistent with traditional and ethical practices in journalism (Remember: even credible sources sometimes rely on clickbait-style headlines or occasionally make mistakes. No news organization is perfect, which is why a healthy news diet consists of multiple sources of information).

**List of domains**
You can find the full list of domains in `websites.csv`. 

## Limitations

The dataset was not fully manually filtered, therefore some of the labels might not be correct and some of the URLs might not point to the actual articles but other pages on the website. However, because the corpus is intended for use in training machine learning algorithms, those problems should not pose a practical issue.  

Currently the public version of the dataset has highly unbalanced classes, especially `reliable` (only 7k) vs rest (~ 1mln). That problem will be soon addressed by including additional sources from reliable public API’s. 

Additionally, when the dataset will be finalised (as for now only about 5% was cleaned and published), I do not intend to update it, therefore it might quickly become outdated for other purposes than content-based algorithms. However, any contributions are welcome!

## Contributing

Because there’s currently only myself working on this corpus, I’d really appreciate all the contributions. If you have found wrong labels associated with any articles, weirdly formatted content or URLs that are not pointing to any articles, feel free to post an issue with the problem and exact article id and I will do my best to respond promptly. Because of the size of the corpus, I could not host it on GitHub, therefore, unfortunately, for now, pull requests cannot be used to collaborative work on the data, however, I’m open to any ideas 🙂 

## Acknowledgments
- [http://www.opensources.co/](http://www.opensources.co/)
