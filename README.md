# PetCircle Home Test


## Please describe

1. Your approach to capturing data from bestdogtoys.com.au. What will you capture,
how will this be done. Why did you choose this method and technique?
2. Now the data is in the DW. What will you do to make it usable? Please describe this
in some detail as we will follow up on this as part of the test. What schema will you
create to store any transformed data?
3. Now the data is ready to be reported on. What content will your reports have?

---

## My approach to capturing data:

### My findigs
After I researched a little bit about BigQuery, I found that it provides a [API](https://cloud.google.com/bigquery/streaming-data-into-bigquery#streaminginsertexamples) to push data from the website to it's tables. 

## How
Although, my prefered approach would be create a servless Api that would accept the data, so that we can process it if needed, than push it down to DW. 

The website can freely decide what and when to push the data to the specified API endpoint when it sees fit. Example would be when user interactions with the site.


### What
I would capture the user interaction with the website. An example is if we present a personalized content, does the user clicks on it? Does the user follows the assumed flow that would lead to the main site or drops it? From the homepage, does the user clicks on a product and buy it? (even though GoogleAnalyctics have all that data 😅 - maybe we can grab GA info into BigQuery? Found this doc [here.](https://support.google.com/analytics/answer/3416092?hl=en#zippy=%2Cin-this-article)


### Why
There are quite substantial benefits on having a centraled access point to push data to BigQuery. Example is monitoring, traceability, ci/cd, versioning, single documentation, single place to apply changes (new features and requirements), and more.


---

## Once in DW, What will you do to make it usable:
I would create some schemas/virtual tables that matches user sessions with interactions/pages/events. Don't know exaclty the best approach for this, but I heard people talking about Looker to analyse data, data manipulations, etc. Somehow we need to enable the other departments, such as the Data Scientists to consume a more friendly data set.  
---

## Data is ready to report on, this is what content the reports will have:
For webpage navigation content: 
- User session
- CorrelationId 
- Segment
- SourceFrom /Where it originated from
- User from page
- SourceTo/Where it landed on
- User landed on page
- DateCreated