## Introduction

### Background

In 1998, Mexico had a close presidential election. The ruling party, the Institutional Revolutionary Party (PRI), had a great chance to win, but it was fractured due to internal corruption. Some members left to form the Democratic National Front (FDN), which focused on an electorate dissatisfied with declining living standards. The National Action Party (PAN) targeted middle-class voters who were unhappy with the country's economic policies.

Opposition parties identified and pointed out irregularities around the country during the voting process. However, questions about the state's legitimacy only emerged after the polls had closed on election night.

When 2% of the vote tallies had been counted, the preliminary results showed the PRI’s imminent defeat in Mexico City metropolitan area and a very narrow vote margin between PRI and FDN. A few minutes later, the screens at the Ministry of Interior went blank, an event that electoral authorities justified as a technical problem caused by an overload on telephone lines. The vote count was therefore suspended for three days, despite the fact that opposition representatives found a computer in the basement that continued to receive electoral results. Three days later, the vote count resumed, and soon the official announced PRI’s winning with 50.4% of the vote. 

What happened on that night and the following days? Was it just an accident or did PRI manipulate the election outcome? In the next weeks, we want to use data science tools to play detective and uncover the truth about the election.

### The assistance from another data scientist

The ideal way to figure out what happened is to count the votes ourselves and compare them with the announced result. However, we could not find the data.

Luckily, another data scientist, [Francisco Cantú](https://franciscocantu.github.io/), unearths a promising dataset that could provide some clues. At the National Archive in Mexico City, Francisco discovered almost 53,000 vote tally sheets. Francisco then discovered that the altered tallies varied significantly from the non-altered tallies, so the proportion of altered tallies can be used to determine the extent of fraud across the nation.

You might see how the altered tallies look like in the following figure.

![1675827583268](image/fraud.png)

Francisco utilized CNN to automatically distinguish between altered and unaltered totals, and he has graciously provided us with the dataset.

For more information, you can read [The Fingerprints of Fraud: Evidence from Mexico&#39;s 1988 Presidential Election](https://www.cambridge.org/core/journals/american-political-science-review/article/fingerprints-of-fraud-evidence-from-mexicos-1988-presidential-election/8F3C1BCA4C53FE85EA48E51321E339E9).

### The dataset

The dataset contains 52,288 vote tally sheets from the 1998 presidential election. Now let's load and check the dataset:

```
library(tidyverse)
mexico_fraud <- read_csv("https://raw.githubusercontent.com/sscihz/DaSPPA/main/InClass_Mexico_Fraud/Data/mexico_fraud.csv")
colnames(mexfraud) 

#[1] "V1"  "rural3"  "union1988"  "centeno"  "totalexperience" "replacement" 
#[7] "iddto"  "idedo"  "jornadaPRI"  "noOP"  "fraud"
```

`V1` is the unique name for each tally sheet.

`rural3` is the proportion of citizens in the district living in communities with fewer than 50,000 inhabitants according to the 1990 census.

`union1988` identifies if the PRI nominated a union leader as a legislative candidate in the tally’s district. The PRI’s territorial base for mobilization and intimidation on Election Day relied on labor unions, which displayed their manpower and resources at the polling stations in exchange for political positions within the party.

`centeno` identifies if the governor is in this within Salinas’s political group. 1 refers to a tally in the state where the governor was in this within Salinas’s political group, and 0 if otherwise.

`totalexperience` indicates whether the state executive had previously held an elected public office. refers to a tally in the state where the governor was previously elected as mayor, deputy, or senator, and 0 if otherwise. Electorally skillful governors are more able to alter the tally.

`replacement` identifies if there was any reappointment of election officials during the 6 months prior to the election in the district.

`iddto`  is an indicator of the polling station’s district.

`idedo` is an indicator of the polling station’s states.

`jornadaPRI` is the proportion of survey respondents in every state who identified with the PRI 3 weeks prior to the Election Day.

`noOP` is a binary variable indicating those tallies with no signature of even one representative from the opposition.

`fraud` is a binary variable indicating if the sheet has been altered.

## Exercise One

This part is the in class exercies for Feb 10. After you read the background of this study, please try to solve following questions using R in Posit Cloud:

To laod the data, you should run the following code:

```
library(tidyverse)
mexico_fraud <- read_csv("https://raw.githubusercontent.com/sscihz/DaSPPA/main/InClass_Mexico_Fraud/Data/mexico_fraud.csv")
```

- How many states and districts are there in Mexico according to this dataset?
  
- What is the proportion of altered tallies in each state? Also find the state with the highest and lowest proportion of altered tallies.

- Do you have any thoery about the variation of the proportion of altered tallies across states? Can you find any evidence to support your theory by the techniques we have learned in class? (Hint:`cor()` might be a useful function)
