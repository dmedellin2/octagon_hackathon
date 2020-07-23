# GAxOctagon Hackathon: Contact-less Check In
#### Danielle Medellin, Sally Huang, Stephen Burnett, Pierce Butler, Katherine Lough

## Problem Statement
With Octagon being in the events business, they are looking for a way for consumers to "check-in" contactless onsite at events. Our goal is to build a platform that allows for efficient contact-less check-ins that is both easy and quick for attendees.

Due to the recent COVID-19 pandemic, safety precautions at future events are of incredible importance. In order to inform the creation of our product, we wanted to gauge public opinion on attending events related to the sports and entertainment industries in a post-COVID world.

## Executive Summary
Due to the fact that the COVID-19 pandemic is still ongoing, it was difficult to nail down data to use for this exploration. After much consideration and searching for open data resources, we decided our data could come from the subreddit r/Coronavirus. We collected data using the [Pushshift API](https://github.com/pushshift/api). The work for our data collection can be found in the [`01_data_collection`](./code/01_data_collection.ipynb) notebook. We collected comments from posts in the r/Coronavirus [subreddit](https://www.reddit.com/r/coronavirus). Comments from the past 60 days were looked at in an effort to get recent opinions. We queried 16 different key words related to COVID and events to filter the comments that came through.

The data collected included the following features: author, body, created_utc, subreddit, permalink, query, and timestamp. More information can be found in the data dictionary below.

### Data Dictionary
|Feature|Type|Description|
|---|:---:|:---|
|author|object|Username of the author of the comment|
|body|object|Full comment text|
|created_utc|integer|Coordinated Universal Time of comment|
|subreddit|object|Subreddit where comment was found (Coronavirus)|
|permalink|object|Partial link to the original comment|
|query|object|Query word that pulled in the comment|
|timestamp|datetime|Date of comment (YYYY-MM-DD)|

We collected a total of 1600 comments. Using Natural Language Processing we stripped all comments of their non-alphanumeric characters and removed stop words. Our custom stop words list comprised of mostly the standard stop words from Sci-Kit Learn, with some exceptions, as well as some additional words that were added after a few iterations of analysis.

Each comment was put through a count vectorizer to determine the most frequently found words and phrases. A minimum n-gram of 2 was used in order to give more context to the comments.

We analyzed the most commonly used phrases among all the comments as well as each individual query. Analysis can be found in the [`02_data_analysis`](./code/02_data_analysis.ipynb) notebook.

## Conclusions & Next Steps
Most of the phrases found throughout the comments made sense and directly referenced topics related to coronavirus such as "social distancing" and "wearing masks". It was difficult to gauge overall positive or negative context from this initial analysis and most phrases were seen as neutral. The common theme found within the comments was regarding taking proper safety precautions such as wearing masks and that there was concern of a "second wave." This gave our team the insight that thinking ahead for the future of events and the process of checking in attendees was absolutely necessary and would be something that consumers would be looking out for. Further research and analysis would cover many more query words, and possibly other subreddits or even other social media platforms such as Twitter or Facebook. 

## References
[Pushshift API](https://github.com/pushshift/api)

[Reddit: r/coronavirus](https://www.reddit.com/r/coronavirus)
