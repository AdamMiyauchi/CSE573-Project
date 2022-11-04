## Assigning a prediction date to each nes article:
Mehtod adapted from pg. 6 of the Professors paper https://www.public.asu.edu/~hdavulcu/wias2e.pdf.

News articles will be used to predict the next trading days price direction. Specifically,articles published before market open (14:30 UTC) are used for predicting the current days price direction. Articles published at or after market open are used for predicting the next trading days price direction. Articles published on a non-trading days (weekends & holidays) are used for predicting the next valid trading day.


</br>

## Generating prediction labels:
Direction for a given trading day $d$:
$$
Dir(d) = \left\{
    \begin{array}{ll}
        \ \ \ 1 \ \ \ \text{if} \ \ Open(d) \le Close(d) \\
        -1 \ \ \  \text{otherwise}
    \end{array}
\right.
$$

</br>

## Dataset Descriptions:

`data/news/preprocessed` : contains all preprocessed data ready for ML.

1. `AaplAmzn_NewsDateDirection.csv`: contains all individual news articles relating to Apple and Amazon, sentiment, and the direction label. 

2. `Aapl_NewsPriceHistDirection.csv`: contains all individual news articles relating to Apple, sentiment,and historical closing prices, and the direction label.

3. `Amzn_NewsPriceHistDirection.csv`: contains all individual news articles relating to Amazon, sentiment, and historical closing prices, and the direction label.

4. `Aapl_SentimentAggMeanPriceHistDirection.csv`: contains mean aggregated sentiment scores for news relating to Apple, historical sentiment, historical closing prices, and the direction label.

5. `Aapl_SentimentAggSumPriceHistDirection.csv`: contains sum aggregated sentiment scores for news relating to Apple, historical sentiment, historical closing prices, and the direction label.

6. `Amzn_SentimentAggMeanPriceHistDirection.csv`: contains mean aggregated sentiment scores for news relating to Amazon, historical sentiment, historical closing prices, and the direction label.

7. `Amzn_SentimentAggSumPriceHistDirection.csv`: contains sum aggregated sentiment scores for news relating to Amazon, historical sentiment, historical closing prices, and the direction label.

Specific feature definitions:
- `title_<pos/neg/net>_sent` - FinBERT sentiment scores of the article title
- `text_<pos/neg/net>_sent` - FinBERT sentiment scores of the article body
- `entity_<pos/neg/net>_sent` - FinBERT mean aggregated sentiment scores of sentences containing 'AAPL', 'Apple', 'AMZN', or 'Amazon'. 
- `prevClose_<n>`: the closing price from $n$ days ago. $n \in [1,25]$
- `entity_<pos/neg/net>_sent_minus_<n>` - the sentiment from $n$ days ago. $n \in [1,25]$



