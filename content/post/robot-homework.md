+++
title = "Can a Robot do my Homework"
date = 2021-01-06T23:22:09Z
author = "Shane Nolan"
keywords = ["", ""]
cover = "/images/avatar.png"
summary = "A guide for lazy financial analysts and optimistic investors. The blog post that talks about that time I played with python code to see if it could give me a TLDR on complex datasets"

+++

## A guide for lazy financial analysts and optimistic investors

If there’s any industry thats both [resistant to change](https://www.obserwatorfinansowy.pl/in-english/banks-are-resisting-modern-technology/) and the perfect target for automation, its the finance industry. NLG (Natural Language Generation) can analyse, interpret, summarise and explain large data in a fraction of the time it would take Johnny Wallstreet to do manually with his calculator and dictionary. Using an NLG engine also removes human bias and error, providing reliable, repeatable, consistent and honest results.

Contrary to the popular belief that finance is all about numbers, financial analysts are not worth the paper their degree was printed on if they don't understand or can't effectively communicate the meaning and context behind these numbers to any interested stakeholders. In [this](https://www2.deloitte.com/content/dam/Deloitte/us/Documents/finance-transformation/us-crunch-time-seven-reporting-in-a-digital-world.pdf) study by deloitte, and according to [this](https://www.allbusinessschools.com/finance/common-questions/financial-analyst-job-description/) random article from the internet, it is clear that the majority of a financial teams time is spent creating and updating reports, with very little time spent communicating findings with the business.

The aim of NLG is to reverse this behaviour. Similar to the manual tasks a financial analyst like Johnny Wallstreet undertakes, NLG analyses data, extracts and interprets the most interesting and important facts, and summarises it to suit it's target audience. Speed is not the only benefit of this process, as mentioned before, NLG removes bias and human error and produces consistent, objective reports.

Some brave financial institutes are already starting to realise the potential of investing in NLG, unlike their friends who are [relying on technology like COBOL to run wall street](https://www.wsj.com/articles/BL-CIOB-5413), some companies are embracing cutting edge technologies to drive their business and give them an edge over their competitors. In [this](https://deloitte.wsj.com/cio/2017/10/05/digitizing-finance-communications-with-natural-language-generation/) wall street journal article, one financial institute states that  

> Prior to using NLG, the client needed to engage more than 40 analysts around the world. With NLG, the organization could create the first draft in 10 minutes rather than several weeks

## Show me the code

[NLG for fun and finance](https://github.com/shanenolanwit/tunnel-snakes-101/blob/master/OffLicenceNLG.ipynb) 

In the github project linked above, I take a csv that contains off license sales data for a week and use nlg to describe the sales for the week. I then move onto a more complex example and take a block of text representing a blog or article about whats going on in the world of finance and investments, and attempt to use nlg to provide a quick summary of what to invest in and/or what to avoid. I even include a little graph for those who prefer pictures than words. Follow the link for the most up to date version of the case study but basically we aim to take an input such as this:

> greetings to first time readers this blog aims to inform you of useful stuff. In todays financial news experts are predicting chicken goujons are a safe and secure bet. i am particularly speculative of investments in antique typewriters and i believe calculators are still risky in the long term. However with regard to precious metals, the returns are at all time high, our resident expert predicts gold prices will soar

And produce a report like this:
```
Invest in chicken goujons and gold
Things are looking pretty shit for typewriters and calculators
```
We don't quite get there, and our end results look something like this:
```
i'm getting [safe, secure] vibes off ['goujons', 'chicken']
i'm getting ['speculative'] vibes off ['investments', 'typewriters']
```
and this : 
```json
chicken goujons safe secure bet
experts predicting chicken goujons safe
expert predicts gold prices soar
speculative investments antique typewriters
calculators still risky long term
```

Jump over to the github [repo](https://github.com/shanenolanwit/tunnel-snakes-101/blob/master/OffLicenceNLG.ipynb) and take a look at the code and the graphs, it's presented as a jupyter notebook so you can see the result of each piece of code as 
it's executed. I've added comments and commentary so hopefully you can get a good understanding of whats going on. This work was done prior to my AWS Machine Learning journey so I'll probably revisit at some stage, hopefully improve the results and maybe even get another blog post out of it. Until then, see you guys on the Nasdaq, or whatever.

![teamwork](/images/guywithmoney.png)

## DISCLAIMER
Please don't use my code to make real investment decisions. *Unless* you are willing to take full responsibility if you lose money, and willing to split the profits with me if you make money.
