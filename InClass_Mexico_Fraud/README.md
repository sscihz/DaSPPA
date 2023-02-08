## Introduction

### Background

In 1998, Mexico had a close presidential election. The ruling party, the Institutional Revolutionary Party (PRI), had a great chance to win, but it was fractured due to internal corruption. Some members left to form the Democratic National Front (FDN), which focused on an electorate dissatisfied with declining living standards. The National Action Party (PAN) targeted middle-class voters who were unhappy with the country's economic policies.

Opposition parties identified and pointed out irregularities around the country during the voting process. However, questions about the state's legitimacy only emerged after the polls had closed on election night.

When 2% of the vote tallies had been counted, the preliminary results showed the PRI’s imminent defeat in Mexico City metropolitan area and a very narrow vote margin between PRI and FDN. A few minutes later, the screens at the Ministry of Interior went blank, an event that electoral authorities justified as a technical problem caused by an overload on telephone lines. The vote count was therefore suspended for three days, despite the fact that opposition representatives found a computer in the basement that continued to receive electoral results. Three days later, the vote count resumed, and soon the official announced PRI’s winning with 50.4% of the vote.

What happened on that night and the following days? In the next weeks, we want to use data science tools to play detective and uncover the truth about the election.

### The assistance from another data scientist

The ideal way to figure out what happened is to count the votes ourselves and compare them with the announced result. However, we could not find the data.

Luckily, another data scientist, [Francisco Cantú](https://franciscocantu.github.io/), unearths a promising dataset that could provide some clues. At the National Archive in Mexico City, Francisco discovered almost 53,000 vote tally sheets. Francisco then discovered that the altered tallies varied significantly from the non-altered tallies, so the proportion of altered tallies can be used to determine the extent of fraud across the nation.

You might see how the altered tallies look like in the following figure.

![1675827583268](image/README/1675827583268.png)

Francisco utilized CNN to automatically distinguish between altered and unaltered totals, and he has graciously provided us with the dataset.

For more information, you can read [The Fingerprints of Fraud: Evidence from Mexico&#39;s 1988 Presidential Election](https://www.cambridge.org/core/journals/american-political-science-review/article/fingerprints-of-fraud-evidence-from-mexicos-1988-presidential-election/8F3C1BCA4C53FE85EA48E51321E339E9).

### The dataset

The dataset contains 52,999 vote tally sheets from the 1998 presidential election. Each row represents a tally sheet, and each column represents a candidate. The column “jornadaPRI” indicates whether the tally sheet was altered or not. The column “jornadaPRI” is 1 if the tally sheet was altered, and 0 if the tally sheet was not altered. The column “jornadaPRI” is the target variable.


Now let's load and check the dataset:
```
mexico_fraud <- read.csv("")
colnames(mexfraud) 

#[1] "V1"  "rural3"  "union1988"  "centeno"  "totalexperience" "replacement" 
#[7] "iddto"  "idedo"  "jornadaPRI"  "noOP"  "fraud"
```


## Day One

As a detective unfamiliar with Mexican politics, how many states and districts are there in Mexico according to this dataset?
What is the proportion of altered tallies in each state?
Is there any relation between the “jornadaPRI” and the proportion of altered tallies?
