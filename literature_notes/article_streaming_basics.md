

# Artcile link
https://huyenchip.com/2022/08/03/stream-processing-for-data-scientists.html


historical data and streaming data


batch processing and stream processing

- It talks about online prediction and batch prediction. 

Imagine you work for an ecommerce site and want to predict the optimal discount to give a user for a given product to encourage them to buy it. One of the features you might use is the average price of all the items this user has looked at in the last 30 minutes. This is an online feature – it needs to be computed on online data (as opposed to being pre-computed on historical data).

One “easy” way to do this is to spin up a service like AWS Lambda and Google Cloud Function to compute this feature whenever requests arrive. This is how many companies are doing it and it works in many simple cases. However, it doesn’t scale if you want to use complex online features.

This “easy” way is stateless, which means that each computation is independent from the previous one. Every time you compute this feature, you have to process all the data from the last 30 minutes, e.g:

To compute this feature at 10:33am, you’ll have to process data from 10:03 to 10:33.
To compute this feature again at 10:35, you’ll have to process data from 10:05 to 10:35.
The data from 10:05 to 10:33 is processed twice!

## Real time streaming usecases

- Online prediction 
- Realtime monitoring for ML models or for predictions
- Continual learning

Continual learning refers to the ability to update your models whenever needed and to deploy this update quickly. Fast model updates enable our models to adapt to changing environments and business requirements, especially to data distribution shifts.

I’ve talked to ML engineers / data scientists at over 100 companies. Almost everyone told me that continual learning is too “far out”. Most companies are still struggling with dependency management and monitoring to think about continual learning.


## components of streaming system

There are two components of a streaming system: the real-time transport and the computation engine.

The real-time transport, which are basically distributed logs. Data in real-time transports are called streaming data, or “data in motion” as coined by Confluent. Examples: Kafka, AWS Kinesis, GCP Dataflow.
The computation engine performs computation (e.g. joining, aggregation, filtering, etc.) on the data being transported. Examples: Flink, KSQL, Beam, Materialize, Decodable, Spark Streaming.
Transports usually have capacity for simple computation. For example, Kafka is a transport that also has an API called Kafka Streams that provides basic stream processing capacity. However, if you want to perform complex computation, you might want an optimized stream computation engine (similar to how bars usually have some food options but if you want real food you’ll want to go to a restaurant).

### Internal state and checkpoints

Internal state is similar to table snapshot. It capture the state of the system at a given point in time. i.e. If you are using price as feature 


If the log is large (in 2021, Netflix was processing 20 trillion events a day!), replaying the log from the beginning can be prohibitively slow. To mitigate this, we can occasionally save the internal state of the job, e.g. once every hour. The saved internal state is called a checkpoint (or savepoint), and this job can resume from any checkpoint. 

```
# Pseudocode
def average_price(log):
    find the latest checkpoint X
    load total_price, item_count from X
    for each event in the log after X:
update total_price, item_count
avg_price = total_price / item_count
return avg_price
```

### Materialized view
The computed average price value, if saved, will become a materialized view of the feature average price. Each time we query from the materialized view, we don’t recompute the value, but read the saved value.

You might wonder: “Why must we come up with a new term like materialized view instead of saying saved copy or cache?”

Because “saved copy” or “cache” implies that the computed value will never change. Materialized views can change due to late arrivals. If an event that happened at 10.15am got delayed and arrived at 11.10am, all the materialized views that might be affected by this update should be recomputed to account for this delayed event. I say “should” because not all implementations do this.

Reading from a materialized view is great for latency, since we don’t need to recompute the feature. However, the materialized view will eventually become outdated. Materialized views will need to be refreshed (recomputed) either periodically (every few minutes) or based on a change stream.

When refreshing a materialized view, you can recompute it from scratch (e.g. using all the items to compute their average price). Or you can update it using only the new information (e.g. using the latest materialized average price + the prices of updated items). The latter is called incremental materialized.

## Time travel and backfilling

We’ve talked about how to compute a feature on the latest data. Next, we’ll discuss how to compute a feature in the past.

### Time travel in ML workflows

There are many scenarios in an ML workflow where time travel is necessary, but here are the two major ones:

to ensure the train-predict consistency for online features (also known as online-offline skew or training-serving skew)
to compare two models on historical data

## Why is streaming hard?

