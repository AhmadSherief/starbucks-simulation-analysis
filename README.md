# Starbucks Simulation Analysis

Detailed analysis of simulated data that mimics customer behavior on the Starbucks rewards mobile app, along with a machine learning model that predicts whether a customer will respond to an offer. There is also a [blog post](https://medium.com/@ahmad_sherief/analyzing-customer-behavior-on-the-starbucks-rewards-mobile-app-d60534f8bc25) that describes the findings of the analysis.

## Table of contents

- [Quick Start](#quick-start)
- [Project Motivation](#project-motivation)
- [File Description](#file-description)
- [Data Sets](#data-sets)
- [Summary](#summary)
- [Author](#author)
- [Copyright and License](#copyright-and-license)

## Quick Start

There are 2 options available:

- Clone the repo: `git clone https://github.com/AhmadSherief/starbucks-simulation-analysis.git`
- [Download the latest release](https://github.com/AhmadSherief/starbucks-simulation-analysis/archive/master.zip)

## Project Motivation

Once every few days, Starbucks sends out an offer to users of the Starbucks rewards mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or a buy one get one free.

The objective is to combine transaction, demographic and offer data to determine which demographic groups respond best to which offer reward, and to predict which users would respond to a sent offer and make a purchase through it. We define the questions that we will try to answer below:

1. What percentage of users view offers? and what are their characteristics?
2. What percentage of users respond to offers? and what percentage complete the offer after viewing it?
3. How much do adevertisements contribute in user transactions?
4. Can we predict whether a user will respond to an offer or not from demographics and offer reward?

## File Description

The file `Starbucks_Capstone_notebook.ipynb` is written in a Jupyter Notebook, and follows the `CRISP-DM` process.

- First we state the questions that we need to answer.
- Next we explore the data.
- Then we perform some `Data wrangling` to gain insights in order to answer our questions.
- After that we model the data using a LinearSVC model combined with a pipeline to utilize gridsearch optimization to predict whether a user will respond to a sent offer or not.
- Finally we summarize our findings.

## Data Sets

The data is contained in three files:

### portfolio.json

- id (string) - offer id
- offer_type (string) - type of offer ie BOGO, discount, informational
- difficulty (int) - minimum required spend to complete an offer
- reward (int) - reward given for completing an offer
- duration (int) - time for offer to be open, in days
- channels (list of strings)

### profile.json

- age (int) - age of the customer.
- became_member_on (int) - date when customer created an app account
- gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
- id (str) - customer id
- income (float) - customer's income

### transcript.json

- event (str) - record description (ie transaction, offer received, offer viewed, etc.)
- person (str) - customer id
- time (int) - time in hours since start of test. The data begins at time t=0
- value - (dict of strings) - either an offer id or transaction amount depending on the record

## Summary

We discussed how user demographics and the offer reward affect their response to offers or advertisements sent. First, we identified users who don't prefere to share their personal information, and we classified them into a group of users who prefere to stay `anonymous`. We saw that they form 13% of the total users. This helped us identify accurately the gender distribution in the dataset. We saw that males take up 57% of total users and females take up 41%, leaving 1% for others.

Next we saw that the majority of users are in their late 50's or eary 60's, and that the number of users decreases as we move away from the peak. We also saw that age doesn't affect the user attraction to certain offer rewards. However, it was seen that the average amount spent per transaction increases as user age increases.

Many users have an annual income in the range between 30000\$ and 50000\$, but the majority are in the range between 50000\$ and 75000\$, and of course less users have high annual salary. The amount spent per transaction is more when the user income is more, which is expected.

After that we saw that 75% of all the received offers were actually viewed, and that 71% of users complete offers after they view them leaving 29% completing offers unintentionally.

It was seen that offers influence 19% of the total transactions or completed offers that occured, which is pretty big, and that users are 7% more likely to respond to offers when they are sent through social media.

We saw how gender plays role in the average amount spent by a user, and also in responding to which type of offer reward. Males responded more to the 2, 3, and 5 dollar rewards while females respond more to the 10 dollar rewards, and on average, females spend more than males.

People who chose to stay anonymous tend to spend more per transaction in the group that responded to offers, however, for the other group it's completely the opposite, known users spend a lot more than anonymous users.

Finally, we built a model that predicts whether a user will respond to an offer or not based of demographics and offer reward, and the model predicted this with an accuracy of 87%, an F1-score of 0.65 for identifing those who will repond to offers, and an F1-score of 0.92 for those who will not.

## Author

### Ahmad Sherief

- [linkedin.com/in/ahmadsherief/](https://www.linkedin.com/in/ahmadsherief/)
- [github.com/AhmadSherief](https://github.com/AhmadSherief)

## Copyright and License

Code is released under the [MIT License](https://github.com/AhmadSherief/Boston-Airbnb-Data-Analysis/blob/master/LICENSE).
