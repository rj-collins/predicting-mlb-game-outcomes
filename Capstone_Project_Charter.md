---
output:
  html_document: default
  pdf_document: default
  word_document: default
---

# Capstone Project Charter

The purpose of this charter is to establish a shared understanding of your team's project before you begin. It should identify the problem you are addressing, why it matters, who might benefit from the results, and what data you will use.

__This is not a research proposal or a full analysis plan.__ You will develop your project background/rationale and full analysis plan during Sprint 2 of the Capstone.

Keep your responses concise. Aim for approximately 1–2 pages.

## Project Information

__Project title:__ Predicting MLB Game Outcomes After Six Innings.

__Team name:__ I will rename your team in Canvas or you may use the default.

__Team members:__ Nick Degnan and Ruby Collins

__Project source:__

- [ ] Capstone Curated Project Bank

- [X] Alternative project approved by instructor

### Problem and Context

__What problem are you trying to address?__

Describe the problem in a few sentences. What is happening that an organization, business, agency, or community would want to understand, predict, or improve?

*Example:* A subscription-based company is experiencing customer attrition. When customers cancel their subscriptions, the company loses recurring revenue and may incur additional costs to acquire replacement customers.

__Your response:__

__Sports betting companies offer live betting for MLB games with fluid betting odds. In order to maximize profit, these groups require mid-game predictions that are as accurate as possible.__ 

### Why Does This Problem Matter?

Briefly explain why the problem is important in its organizational, business, healthcare, public sector, or other applied context. You do not need to provide a literature review or fully support your rationale with sources yet; you will develop the background and rationale during Sprint 2.

__Consider__:
- What consequences might result from this problem?
- Why might an organization or stakeholder want to address it?
- What decisions could a better understanding of the problem inform?

*Example:* Understanding customer attrition could help a company evaluate its retention strategies and determine where to focus customer support or engagement resources.

__Your response:__

__Sports betting companies make a profit by offering odds that favor themselves over the customer while still being fair enough to yield engagement and wagers. Accurate predictions for live MLB games empower companies to optimize live-betting odds for maximum house wins and minimum customer wins.__

### Stakeholder and Intended Use

__Who would care about the results of this project?__

Identify the primary stakeholder or intended audience. This could be a business unit, organizational decision-maker, public agency, healthcare provider, or other group.

__Primary stakeholder:__ Sport Betting Companies

__What might this stakeholder want to learn or do with the results?__

*Example:* A customer retention team might use the results to better understand which customer characteristics or behaviors are associated with cancellation and to inform future retention strategies.

__Your response:__

__Sportbooks can greatly benefit from more accurate predictions of where the game is going after 6 innings. They would also benefit from an optimal prediction methodology, i.e. determining the boundary where prediction based on current score breaks down and underlying statistics begin to provide accuracy amidst uncertainty.__

### Data Overview

__What data will you use to investigate the problem?__

Identify the dataset and briefly describe what it contains. For a project from the Capstone curated project bank, use the information provided in the project description. Remember, you have the option to refine the project goal or question while still using the same data source!

| Item | Description |
|---|---|
| Dataset name | *Main*: Retrosheet<BR>*Supplementary*: Lahman Database |
| Data source | https://retrosheet.org/downloads/plays.html<BR>https://sabr.org/lahman-database/  |
| Unit of analysis (e.g., customer, transaction, patient) | MLB game data with outcomes (win/lose) |
| Approximate number of observations, if known | Approximately 230,000 MLB games |
| General types of information available | Basic scoring data by inning, plus more detailed information down to individual plays. |
| Data access confirmed? | Yes |

__How might these data help address the problem?__

Briefly explain what information in the dataset could be relevant to the problem.

*Example:* The dataset contains customer demographics, subscription information, service usage, and cancellation status. These data may help the team examine patterns associated with customer attrition.

__Your response:__

__These datasets include the basic necessities of the investigation in box scores by inning, plus highly detailed play-by-play data. The team will examine these to determine patterns and discern key performance indicators.__ 

### The Data Science Opportunity

__What could data science / machine learning / AI practices help you accomplish here?__

At a high level, describe what you hope to learn or accomplish using the available data. You do not need to specify particular algorithms, preprocessing steps, or evaluation metrics here; those belong in the Analysis Plan due in Sprint 2.

*Example:* The team could use historical customer information to identify patterns associated with churn and investigate whether customer cancellation can be predicted using available customer characteristics and behaviors.

__Your response:__

__The team will use historical MLB game data to conduct a straightforward predictive analysis based on score by inning, as well as more complex analyses utilizing comprehensive play-by-play data. The different models can then be compared for relative predictive strength and to discern the strength of key performance indicators.__ 

### Initial Questions and Unknowns

What do you still need to understand about the problem, the data, or the intended use of the results before beginning the analysis?

List up to three questions that your team expects to investigate during the background/rationale development and initial data exploration, both of which you will do during Sprint 2.

1. __Do underlying in-game statistics provide more predictive value than score alone when predicting the outcomes of MLB games after six innings?__ 

2. __What is the optimal number of innings for predictive model performance?__ 

3. __Which features may be predictive of game outcome?__

These are starting questions, not necessarily your final analytical question(s). You will refine your understanding of the problem and develop your Analysis Plan during Sprint 2.

### Project Risks

Project risks are uncertainties that can undermine a project's success. Sometimes we have ways to better control for or assess risks, and sometimes we do not. Your job is to try to identify at least 2 more risks to this project. I am starting you off with a risk everyone will always have at this stage in a project.

1. __The dataset chosen may not be suitable to address the problem/question exactly as posed.__

2. __Substantial quantity of data could provide challenges in data cleaning and processing.__

3. __Shifts in typical MLB athlete/team performance across 120+ years of data may lead to differences in detectable patterns between different time periods.__

### Your Intended Stakeholder

This is actually one of the hardest parts - identifying your primary stakeholder. In the real world, you will know exactly who they are and what is expected of you. Here, you are being asked __to choose__ one (and really try to focus on just one) stakeholder. This will be the audience to whom you address your deliverables (as well as other data scientists on your team, of course!).

__As mentioned above, *sports betting companies* (sportsbooks) will likely be very interested in a predictive model that can indicate the result of a baseball game after six innings. They stand to benefit the most from this investigation and provide the most natural setup to apply our intended models.__

## Final Check

Before submitting, confirm that everyone on your team can answer the following:

- [X] We can clearly describe the problem we will address in our Capstone project.
- [X] We understand why the problem may matter and __to whom__ it may matter.
- [X] We have identified a relevant stakeholder or intended audience.
- [X] We have identified the data we will use and what those data represent.
- [X] We understand, at a high level, what machine learning and data science practices might contribute to this problem.
- [X] We have identified any important questions or uncertainties that remain.
- [X] We have identified, at a high level, any risks to this project.
- [X] We have confirmed that the project and data source are appropriate for the eight-week Capstone.

__Team confirmation:__ We agree that this charter accurately describes our shared understanding of the project at the start of the Capstone.

__Submitted by:__ Nick Degnan

__Date:__ 11/5/26
