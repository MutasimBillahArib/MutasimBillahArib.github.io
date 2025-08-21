---
title: The Adventure of the False Negative 
tags: [Classification, Confusion Matrix]
description: Confusion? Matrix? Metrics? We've got you covered.
---

It was on a damp November morning that Dr. Percy Trevelyan was ushered into our sitting-room at Baker Street. His face was pale, his shoulders bowed, and his hand trembled so violently that the coffee he carried left a spreading stain across my desk.  

Holmes, who had been lounging with eyes closed in his armchair, opened them with sudden brightness.  
“You are a physician of some distinction,” said he, “lately occupied at a cancer screening clinic, and tormented not by disease but by numbers.”  

Dr. Trevelyan started. “How—”  

Holmes waved a languid hand. “The iodine stain upon your cuff, the fatigue of long hours, and that peculiar look of a man undone by mathematics. Pray, tell us your trouble.”  


## Lucy’s Case  

The story came haltingly, in tones of exhaustion. Dr. Trevelyan’s clinic, overwhelmed by patients, had welcomed a new artificial intelligence diagnostic tool. It boasted **99% accuracy** in detecting tumors. For a time, it seemed miraculous—until Lucy.  

“She was forty-two, with no family history,” Dr. Trevelyan whispered. “The machine declared her clear. I trusted it. Months later she returned—the tumor had been there all along. Aggressive. Advanced. The machine missed it. A false negative.”  

His voice broke. “How could ninety-nine percent conceal such a tragedy?”  

Holmes rose, pacing, his eyes afire.  
“My dear Watson, accuracy is the most treacherous of statistics. It comforts the untrained, yet hides the very error that matters most. Show me the report.”  


## The Matrix of Consequences  

Holmes spread the papers upon our table and, with a pencil, drew a square divided into four quadrants.  

“Behold, the Confusion Matrix. Not confusing at all, Watson—merely the anatomy of error.”  

He explained with crisp precision:  

- **True Positive (TP):** The machine cries *Tumor!* and it is correct. “The good outcome—Lucy caught in time.”  
- **True Negative (TN):** It says *No tumor*, and indeed there is none. “The good sleep of reassurance.”  
- **False Positive (FP):** It alarms where none exists. “Annoying, but survivable—needless tests and worry.”  
- **False Negative (FN):** It whispers *All clear* when danger lurks. Holmes’s voice dropped. “This is Lucy—the catastrophic mistake.”  

He filled the boxes with Dr. Trevelyan’s numbers for 1,000 patients:  

- 990 TNs.  
- 5 TPs.  
- 5 FPs.  
- 10 FNs.  

“Accuracy?” Holmes scrawled.  


$\frac{TP + TN}{\text{Total}} = \frac{5 + 990}{1000} = 99.5\%$



“Glittering! Yet it hides the ten Lucys. Accuracy is a lazy storyteller—it tells the tale of the majority, not the critical few.”    


## Choosing the Right Metric  

Holmes straightened. “The true question is not *How accurate?* but *What is the cost of being wrong in this particular way?* Observe.”  

### 🩺 Scenario 1: Cancer Screening (Trevelyan’s Case)  
- **False Negative:** Catastrophic—delayed treatment, death.  
- **False Positive:** Anxiety, extra tests—serious, but survivable.  
- **Priority:** Catch every possible tumor.  
- **Metric:** Recall.  


`\text{Recall} = \frac{TP}{TP + FN} = \frac{5}{15} = 33\%`


Holmes pointed. “There is your disaster.”  

Dr. Trevelyan buried his head in his hands. “It wasn’t 99%. It was 33%. Only one in three tumors caught. We failed ten Lucys.”


### 📧 Scenario 2: Spam Email Filter  
Holmes gave a wry smile.  
“A trivial modern nuisance. False negatives—spam in the inbox—are tolerable. False positives—an urgent letter lost—are catastrophic. Thus, the wise man demands **Precision**.”

$$Precision \eq \fraq{TP}{TP + FP}$$  


### ⚖️ Scenario 3: Loan Approval  

“A balance of perils. Deny a worthy man credit—bad. Approve a rogue—worse. Both errors cut, though differently. Here the **F1-score**, harmonising recall and precision, is the truest guide.”

$$F1 = 2 * \fraq{precision * recall}{precision + recall}$$


### 🤒 Scenario 4: Common Disease Screening  

“Where disease is frequent and errors less dire, **accuracy** regains some meaning. But only, Watson, if the classes are balanced. Always consult the matrix before you trust the percentage.”  


## The Crime in the Numbers  

Holmes delved deeper into the clinic’s files. At last, he drew forth a memorandum.  
“Here, Watson—buried in appendices. They knew the machine missed more tumors in younger women, but they concealed it in their promotional boasts. Not a flaw of science, but of men. The crime is not in the code, but in the concealment.”  

In the weeks that followed, reforms were enacted. The AI was rebuilt to prioritise recall, casting a wider net. More false alarms arose, but fewer Lucys were missed. A second safeguard was added: every positive was carefully reviewed by a physician before action was taken.  


## Holmes’s Reflection  

As we sat again by the fire, I could not help but ask, “Holmes, what then is accuracy?”  

He gave a thin smile.  
“Accuracy, my dear Watson, is the laziest of storytellers. It smooths the jagged edges and tells you only what you wish to hear. But the Confusion Matrix—ah, that tells the whole story. It shows you where the landmines are buried. And sometimes, Watson, saving a life means enduring a thousand false alarms.”  
