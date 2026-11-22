
**Data:**

NASA Kepler KOI table (2017 snapshot, from Kaggle): https://www.kaggle.com/datasets/nasa/kepler-exoplanet-search-results
NASA’s current KOI table: https://exoplanetarchive.ipac.caltech.edu/cgi-bin/TblView/nph-tblView?app=ExoTbls&config=cumulative
Files:

Kepler_Analysis.ipynb. To run it, upload cumulative.csv and nasa_now.csv.

License: CC0: Public Domain, per the Kaggle dataset page.
This dataset was published as-is by NASA. You can access the original table here: https://exoplanetarchive.ipac.caltech.edu/cgi-bin/TblView/nph-tblView?app=ExoTbls&config=koi. More data from the Kepler mission is available from the same source here: https://exoplanetarchive.ipac.caltech.edu/docs/data.html

**Findings:**

According to NASA, an eclipsing binary is two stars orbiting each other, where one passes in front of the other as seen from Earth. This pattern could potentially explain the higher median for the false positive readings for object temperature and size, as well as shorter orbital periods.

The scatter plot demonstrated that confirmed planets sit at the bottom-left section, with impact < 1 and size between 1 and 10 earth radii. On the other hand, false positives had large sizes which is not typical of planets and had grazing impacts (around 1 or above).

The original baseline from the dataset (66%) improved by nearly 23 percentage points when the "max depth" was chosen as 8 for the decision tree.

The model predicted 906 confirmed planets, and 316 had a planet share of 0.8 or higher.

When the depth of the decision tree was increased, its training and test scores showed a wider gap. At a depth of 8-10, the training score rose sharply while the test score remained stagnant at 0.89.

From the original candidates, NASA has confirmed 442 as real planets, of my 2,185 cleaned candidates, through additional exploration and data.

Using this model, 377 out of 406, of the flagged candidates NASA has since resolved, were real planets (93%). When it predicted ‘false positive’, it was right 64% of the time (116 of 181).

For candidates NASA has since resolved, always guessing ‘planet’ would be right 75% of the time (442 real planets ÷ 587 resolved). The tree scores 84% ((377 + 116) ÷ 587), which is 9 percentage points higher.

**Limitations:**

The data is taken from 2017 Kepler data snapshot so the data might be outdated.

Certain rows with missing values were removed, leaving 2185 candidates, before the analysis so they are not accounted for in the prediction.

Planets and false positives can have large overlaps if they are similar in sizes, which can make it challenging for the model to predict.

NASA further used additional data and research that this model does not have.

**Next Steps:**

Include more test cases with different data columns, such as planet positioning, error rate, etc. to test if the test accuracy varies.

Use random forest to see if it gives a different prediction.

**Acknowledgements:**

I learned Python, pandas and scikit-learn for this project with guidance from Claude (Anthropic's AI assistant), which acted as a tutor and explained concepts, reviewed my code, answered questions, and helped me interpret the results. I wrote the code and made certain modelling decisions, such as features to train the model on, tree depth, validation against NASA’s current data, and wrote the findings.
