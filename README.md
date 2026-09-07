# STADIOEquities - Capstone Project (CAP 182)

# Project Overview

This project suggests a data science solution for the digital investing platform STADIOEquities in South Africa. The project focuses on active investors, clients who register but do not get financed, and funded clients who then become inactive—three of the company's most significant and expensive business issues.

By identifying clients who are likely to get stuck during activation or go inactive, the suggested solution—a predictive analytics model—allows STADIOEquities to intervene earlier and more effectively.

# Motivation

With almost 2.3 million registered accounts, STADIOEquities has successfully lowered investment obstacles and developed a sizable client base of young, first-time investors. However, it is evident that the company's primary problem is now turning customers into funded, active, and long-term investors rather from just collecting accounts. Only 760,000 accounts are funded and active at the moment, and 41% of registered accounts have never been funded. This is important from a business standpoint because the platform makes very little money from empty accounts, therefore engagement and activation are essential to the business's business strategy.

There is a decline in the activation funnel. The percentage of accounts that become inactive within six months has increased from 22% to 31%, while the conversion rate from sign-up to first deposit has decreased from 64% to 59%. Additionally, the rate of KYC onboarding abandonment has gone up from 13% to 18%. These patterns suggest that STADIOEquities is investing efforts in attracting clients who do not regularly develop into profitable partnerships. Despite evidence indicating drop-off is related to acquisition channel, onboarding progress, first-session conduct, and the time necessary to make a first deposit, the organization still sends onboarding emails and nudges in accordance with a set schedule.

By identifying trends linked to activation and future dormancy utilising the behavioural, account, funding, trading, marketing, and demographic data already collected by STADIOEquities, a this project can offer value. The company may utilise a predictive score to identify which customers are most likely to stop or withdraw and intervene at a more suitable time, rather than treating every customer equally. This immediately contributes to the company's 2030 strategic focus of activating its existing accounts and maintaining long-term client engagement.

Additionally, the project encourages more effective use of client-service and marketing resources. Support tickets have increased from 46 to 63 per 1,000 active clients, according to STADIOEquities, and the company has a lot of behavioural and service data that isn't being regularly combined into a single client perspective. Therefore, predictive insight could assist the company in switching from a reactive strategy—reacting to a client's inactivity or complaints—to a proactive strategy based on observable behaviour.

Because STADIOEquities won't need to develop a whole new information source, the project is especially relevant to the company. The company already keeps track of app and online behaviour, account and financing activity, trading activity, product and subscription statistics, demographics, support and feedback, marketing activity, and compliance monitoring. These sources, which provide data ranging three to six years, offer a solid basis for a Data Science solution.

Therefore, there are three anticipated commercial benefits: better targeting of interventions and resources, decreased inactivity among funded clients, and increased conversion of current registrations into funded accounts. These results can then support revenue streams like platform and administrative fees, broking fees, interest collected on client funds, premium subscriptions, and value-added products that rely on funded and active clients.

Finally, this initiative is in line with the strategic direction of the company. The STADIOEquities 2030 strategy specifically requires the company to identify clients who are likely to activate or stall their accounts, recognise inactivity before an account becomes silent, and take appropriate action. Therefore, a predictive activation and inactivity model makes effective use of the company's existing data assets while addressing a clearly defined business priority.

# Problem Statement

Although STADIOEquities has a sizeable registered clientele, a sizeable percentage of these clients never get from registration to funded, active, and long-term investment. The percentage of accounts that become dormant within six months has increased to 31%, the sign-up-to-first-deposit conversion rate has decreased to 59%, and 41% of registered accounts have never deposited money. It is now challenging to differentiate between customers who are likely to activate organically and clients who are at risk of giving up or going dormant because onboarding communications and nudges are primarily sent in accordance with a set schedule.

Because STADIOEquities must pay an average of R180 to obtain an account, which is only recouped upon account activation, this presents a financial challenge. The company is not utilising all of its available behavioural, funding, trade, marketing, and service data, and inactive accounts generate very little revenue.

The data science challenge is to create a prediction model that uses information known before to the outcome to estimate the probability that a single registered or funded customer will fail to activate or become dormant during a specified future period. STADIOEquities should be able to detect high-risk clients early and prioritise the right interventions thanks to the resulting predictions.

In the end, the project should respond to: Which observable client actions and traits are most predictive of future dormancy or activation failure, and can these signals be utilised to precisely identify clients who need proactive intervention?

# Repository Structure

![image](https://github.com/21208737/STADIOEquities/blob/main/Repository%20structure.jpeg?raw=true)

# Repository Artefact Guide

![image](https://github.com/21208737/STADIOEquities/blob/488ae8c37e882a1670e7d2f00aa381fb0689dd16/Artefact.png)

# RAAIDD LOG

|  RAAIDD CATEGORY  |  Project specific entry   |
|  ---------------  |  ----------------------   |
|  Risks            |1. The outcome labels for activation and dormancy may be inconsistent across historical periods.
|                   |2. App/web, funding, trading, marketing, and support systems may not consistently link client identities. 
|                   |3. If events that happen after the prediction point are inadvertently included, behavioural data may contain leakage. 
|                   |4. Inexperienced or specific client groups may be disproportionately flagged by the model, resulting in an inappropriate intervention experience. 
|                   |5. If STADIOEquities modifies onboarding, products, or price, past behaviour might not accurately reflect future conduct.
|                   |                                                                                                    |
|  Actions          |1. Before modelling, explicitly define activation and dormancy with business stakeholders. |
|                   |2. Examine each requested data source for completeness, consistency, and join-ability. |
|                   |3. Make a time-based modelling dataset that uses only data that was accessible prior to the prediction point. |
|                   |4. Conduct exploratory analysis and look into the behavioural cues related to dormancy and activation. |
|                   |5. Develop and evaluate appropriate baseline and prediction models. |
|                   |6. Assess business utility, subgroup behaviour, calibration, and predictive performance.         |
|                   |                                                                                                    |
|  Assumptions      |1. Historical client-level data with a reliable pseudonymous identification can be obtained via STADIOEquities. |
|                   |2. Account and financing data are a reliable source of historical activation and dormancy results. |
|                   |3. There are enough instances of activation and dormancy in the four to six years of data that are now accessible to train and assess a model. |
|                   |4. There is enough information in the behavioural signals recorded prior to activation/dormancy to enable prediction. |
|                   |5. Without requiring the model to make independent judgements regarding a client's financial appropriateness, STADIOEquities can use model scores to prioritise interventions.          |
|                   |                                                                                          |
|  Issues           |The information pack specifies the relevant data sources but does not provide a single standard definition for the modelling target, which is the primary known problem at the beginning of the project. Before model development starts, this needs to be settled with the client.          |
|                   |                                                            |
|  Decisions        |Instead of trying to address all five STADIOEquities 2030 priorities at once, the initiative will first concentrate on activation and six-month dormancy prediction. This offers a targeted issue with quantifiable results and a direct connection to the company's dormancy problem and activation gap.          |
|                   |                                        |
|  Dependencies     |1. Before labels are made, target definitions must be agreed upon. |
|                   |2. Before joining various data sources, stable client identities are needed. |
|                   |3. Prior to feature engineering, data-quality checks must be finished. |
|                   |4. Accurate events are necessary for a time-based train/validation/test split. |
         
