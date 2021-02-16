# FOREX strategy parameter selection with Random Forest

My FOREX trade system and strategy has lots of parameters. Because of the number of parameters, the combinations of the possible test scenarios easily can reach very large numbers. To test all promising scenarios would require a very long time. For example, if I want to change only six parameters, all of them with 10 different numbers gives 1 million combinations, this means 1 million test runs.

If I want to run tests and trade my strategy in this century I need some techniques to reduce the number of test scenarios :) Here I show how I try to find the best parameter combinations for the tests and how I choose the combinations for trade.

The main idea is to build a sparse grid of parameter combinations in two steps, where the grid is denser in the space where the strategy has a better chance to be in profit. After that, I fit some estimators to this grid where the labels are different metrics of the trade. I use random forest classifiers and regressors because they gave a good fit. Then I build a denser grid of parameters, where the metrics (for example finished deposit) are estimated by the random forest models. With different metrics, I build a score for each grid. This score is proportional to the chance that the parameter combination (or the grid point) will be selected for trade. Obviously better performing combinations will have a higher score, and losing combinations will have zero scores. From the score with a simple transformation, we get the probability mass function of the grid for selecting the given grid point. I randomly select multiple parameter combinations based on this probabilities and test them on a different year than the earlier tests were run.

### Parameter selection:<br>
https://www.kaggle.com/sinusgamma/forex-strategy-eda-and-parameter-selection<br>
https://github.com/sinusgamma/FOREX-strategy-parameter-selection/blob/master/forex-strategy-eda-and-parameter-selection.ipynb<br>

### My trade system and the strategy:<br>
https://medium.com/@istvan.veber/forex-news-trader-785ad0a1394c<br>
https://medium.com/@istvan.veber/trade-the-news-but-make-your-forex-research-part-2-analysis-and-strategy-e0f2c84a3bdd<br>
https://github.com/sinusgamma/Forex-News-Trader-Dukascopy-API<br>

