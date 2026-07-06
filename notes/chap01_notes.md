# Think Bayes Chapter 1 Notes

## Overview

Chapter 1: conditional probability -> Bayes's Theorem (theory)

Chapter 2: conditional probability -> Bayes's Theorem (application)

Chapter 3 and beyond: transition from Bayes's Theorem to Bayesian statistics

## Example: Linda the Banker

Given:

- A) Linda is 31 years old, single, outspoken, and very bright.
- B) She majored in philosophy, she was deeply concerned with issues of
  discrimination and social justice, and participated in anti-nuclear
  demonstrations.

Estimate which is more likely:

- Linda is a bank teller.
- Linda is a bank teller and is active in the feminist movement.

Suppose we find 1000 people who fit Linda's description and 10 of them work as
bank tellers (1-percent) How many of them are also feminists? At most, all 10 of
them are (1-percent)

So, the options range from equally probable to less probable.

## Probability

A simple definition: A probability is a fraction of a finite set.

If we survey 1000 people, and 20 of them are bank tellers, the fraction that
work as bank tellers is 0.02 or 2%.

If we choose a person from this population at random, the probability that they
are a bank teller is 2%.

Data from the General Social Survey (GSS). The DataFrame has one row for each
person surveyed and one column for each variable I selected.

The columns are

- caseid: Respondent identifier.
- year: Year when the respondent was surveyed.
- age: Respondent's age when surveyed.
- sex: Male or female.
- polviews: Political views on a range from liberal to conservative.
- partyid: Political party affiliation, Democrat, Independent, or Republican.
- indus10: Code for the industry the respondent works in.

Let's look at these variables in more detail, starting with `indus10`.

### Fraction of Bankers

In this dataset, there are 728 bankers. To compute the fraction of bankers, we
can use the mean function, which computes the fraction of True values in the
series.

About 1.5% of the respondents work in banking, so if we choose a random person
from the dataset, the probability they are a banker is about 1.5%.
