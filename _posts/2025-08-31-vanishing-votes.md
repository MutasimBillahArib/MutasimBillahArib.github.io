---
title: The Case of the Vanishing Votes
subtitle: A Sherlock Holmes Data Science Mystery
tags: [Sherlock Holmes, Time Series]
description: An election analyst claims 98% accuracy predicting voter turnout. Holmes finds rural votes were systematically ignored (data leakage from future elections).
---

{% include elements/figure.html image="/assets/images/blog/2025-08-31-vanishing-votes.png" caption="Image was generated using Qwen3-235B-A22B-2507" %}

*221B Baker Street, London*  
*October 17th, 1892*

## The Client with Vanishing Votes

The fog wrapped around London, thick and clinging, like a thief to the shadows, when Mr. Percy Phelps stumbled into our room. His spectacles were crooked, one lens fogged, and election ledgers clutched to his chest like a life raft.

"*Mr. Holmes! My model has committed electoral murder!*" he gasped, collapsing into my armchair. "*Fifty-three rural villages cast ballots yesterday. My system predicted a mere 3% turnout; yet 65% of voters appeared! Half the votes have vanished from my predictions!*"

Holmes steepled his fingers, eyes gleaming. "*Your model, you say? Explain this system.*"

Mr. Phelps straightened his waistcoat, pride momentarily eclipsing panic. "*I built a predictor for voter turnout using five past elections; 1887 to 1891. Features include railway access, newspaper circulation, population density... even alehouse proximity! It achieved 98% accuracy across all five contests. Yet yesterday, __catastrophe__! Rural votes simply... disappeared.*"

He slapped a chart onto Holmes’ desk: five neat bars labeled "*Actual vs. Predicted Turnout*"; all nearly identical. "*See? Flawless!*"

I leaned in, impressed. "*Remarkable precision, Mr. Phelps.*"

Holmes did not move. "*When,*" he murmured, "*did you collect the railway data?*"

"*Why, after each election! The Great Western Railway publishes annual reports every January.*"

"*Ah.*" Holmes' voice turned to ice. "*So for the 1888 election... you used railway data from January 1889?*"

Mr. Phelps blinked. "*Naturally. How else would I know if new lines opened?*"

Holmes sprang to his feet, scattering tobacco ash like confetti. "*Then your 98% accuracy is a __phantom__, sir! A ghost built on __future knowledge__!*"

## The Chronological Crime

Holmes seized a dusty ledger from the shelf, *Railway Expansion Reports, 1885-1892*; and hurled it onto the table.

"*Observe, Mr. Phelps!*" he said, tracing a finger down columns of ink. "*In 1888, the village of Little Purlington had __no railway__. Yet your model __knew__ a station would open there in January 1889 and used that future fact to predict high turnout for the 1888 election! It didn't predict turnout it __memorized hindsight__!*"

Mr. Phelps paled. "*But... the data was available when I trained the model!*"

"*Precisely!*" Holmes snatched Mr. Phelps' chart and pointed at the 1888 bar. "*You measured success using __the future to judge the past__. Your 98% accuracy wasn't forecasting-it was __cheating with tomorrow's newspaper__! And rural villages paid the price.*"

He spun to the window, silhouetted against the gaslit fog. "*Rural infrastructure changed __after__ elections. New railways built in 1889 were used to predict 1888 turnout. But yesterday's election? No future railway data existed. So your model defaulted to assuming no railways in remote villages; hence predicting near-zero turnout!*"

"*But why only rural votes?*" I asked.

"*Because cities change slowly,*" Holmes replied. "*London's railways were static. But rural villages? Like Little Purlington, __transformed__ by new lines. The model learned to spot villages destined for railways; knowledge impossible on Election Day!*"

## The Temporal Trap

Mr. Phelps slumped. "*So my model is fraudulent?*"

"*Not fraudulent, __leaky__,*" Holmes corrected. "*You committed the cardinal sin of time-series modeling: __temporal data leakage__. You allowed future information to seep into your training data.*"

He seized chalk and sketched a timeline on the wall:  

`1887 Election → [Jan 1888 Railway Data] → 1888 Election → [Jan 1889 Railway Data] → 1889 Election`

"*Your model saw __Jan 1888 data__ when predicting the __1887 election__ as if a soothsayer used tomorrow's horoscope to predict yesterday's weather!"* He spun to face Mr Phelps. "*Tell me, could you have known in __July 1888__ that Little Purlington would get a railway six months later?*"

"*Of course not!*"

"*Then why,*" Holmes intoned, "*did you let your model know it?!*"

## The Prescription  

Holmes tossed Mr. Phelps a fresh ledger *Election Records, Chronologically Sorted*.

"*Here is your cure, sir. First, __split by time__, not chance.*" He drew a sharp line through the ledger:

> TRAINING DATA: 1887–1889 elections  
> TEST DATA: 1890–1891 elections

"*Train only on the past. Test only on the future. No shuffling! No peeking!*"

"*Second, audit your features like a customs inspector.*" Holmes pointed Mr. Phelps' railway column. "*For __every__ feature, ask __Could I collect this on Election Day?__ If the answer is only after the election; __discard it__! Use __pre-election__ railway maps, not January reports!*"

"*But my accuracy will plummet!*" Mr. Phelps wailed.

"*Good!*" Holmes snapped. "*Let it crash to, say, 62%. That 62% is __truth__. Your 98% was a lie. Accuracy that ignores time is not science; it is alchemy.*"

## The Verdict

As Mr. Phelps departed, clutching the corrected ledger, I turned to Holmes. "*A sobering lesson, Holmes. But why did the rural votes vanish specifically?*"

Holmes lit his pipe, the smoke twisted slowly, like the fog over London. "*Because leakage favors the predictable, Watson. Cities change slowly, leakage masked itself. But rural villages? __Dynamic, evolving, vulnerable__. Just as in modern data science, __minority groups suffer first when time leaks__. The poor, the remote, the overlooked-they vanish from flawed models while the privileged coast on hindsight.*"

He tapped the timeline on the wall. "*Remember this, Watson, When time flows in one direction, your data must flow with it. Never let the future whisper secrets to the past.*"

Holmes paused, eyes sharp like a blade. "*And never trust an accuracy metric that hasn't been __tested in time__.*"

## The Data Science Epilogue

*For the modern reader:*

Mr. Phelps' crime was temporal data leakage; using future information to predict past events. His *98% accuracy* was an illusion because:

- __His test data wasn't unseen__: it was contaminated with future knowledge (railway data published *after* elections).

- __He shuffled time-series data__: treating election years like random marbles in a bag, ignoring chronological order. 

__How to avoid this__:

- __Split chronologically__: Train on *all data before time T*, test on *data after T*.

- __Use time-aware validation__: `TimeSeriesSplit` in scikit-learn.

- __Audit every feature__: "*Could this exist on prediction day?*"

- __Never use__: Post-event data (e.g., *2023 sales* to predict *Q2 2023 performance*). 

When Mr. Phelps rebuilt his model without leakage, accuracy dropped, but rural votes __stopped vanishing__. Because in data science, __truth often looks like a lower number__.

> "*The greatest deception in prediction is not lying with data, it is believing data that has lied to itself.*"  
> - Sherlock Holmes, The Final Problem of Prediction 

