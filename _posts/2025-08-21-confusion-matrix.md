---
title: The Case of the Deceptive Accuracy
tags: [Classification, Confusion Matrix, Accuracy]
description: A suspenseful Sherlock Holmes tale where Dr. Trevelyan seeks Holmes’s help after an AI cancer screening tool fails, revealing the deadly consequences hidden behind ‘99% accuracy’ and the crucial truths of the Confusion Matrix.
---

It was a damp November morning when Dr. Percy Trevelyan staggered into our sitting-room at Baker Street. His face was ashen, shoulders slumped, and his hand shook so violently that the coffee he carried sloshed over my desk, leaving a dark, jagged stain.

Holmes, reclining with eyes closed, opened them abruptly, sharp and penetrating.

“You are a physician of distinction,” he said, “recently engaged at a cancer clinic. Yet you are haunted not by disease itself, but by the tyranny of numbers.”

Dr. Trevelyan swallowed, bewildered. “How—”

Holmes waved a hand lazily. “The stain on your cuff. The exhaustion in your posture. That haunted look of a man undone by statistics. Speak, sir—what troubles you?”


## Lucy  

The tale came haltingly, almost in whispers. Dr. Trevelyan’s clinic had adopted a new AI diagnostic tool, boasting **99% accuracy** in detecting tumors. For a time, it seemed miraculous—until Lucy.

“She was forty-two, with no family history,” he murmured. “The machine declared her clear. I trusted it. Months later, she returned—the tumor had been there all along. Aggressive. Advanced. The machine missed it. A false negative.”

His voice faltered. “How could ninety-nine percent conceal such a tragedy?”

Holmes rose, pacing, eyes glittering with intensity.
“Accuracy is a beguiling liar,” he said. “It comforts the untrained, yet hides the errors that truly matter. Show me the report.”


## Anatomy of Error 

Holmes spread the papers and drew a square, divided into four quadrants.

“Behold, the Confusion Matrix. It is no mystery—simply the anatomy of error.” 

- **True Positive (TP):** The machine cries *Tumor!* and it is correct. “Fortunate patients—Lucy caught in time.”  
- **True Negative (TN):** It declares *No tumor*, correctly. “The quiet relief of reassurance.”  
- **False Positive (FP):** It screams danger where none exists. “Annoying, but survivable—extra tests and anxiety.”  
- **False Negative (FN):** It whispers *All clear* while danger lurks. Holmes’s voice dropped. “This is Lucy—the catastrophic failure.”  

For 1,000 patients, the numbers were brutal:  

- 990 TNs.  
- 5 TPs.  
- 5 FPs.  
- 10 FNs.  

“Accuracy?” Holmes scrawled.  

$$
\frac{TP + TN}{\text{Total}} = \frac{5 + 990}{1000} = 99.5\%
$$

“Gleaming, yet treacherous,” Holmes said softly. “It hides ten Lucys. Accuracy tells the story of the crowd, not the few who truly matter.”   


## The Right Metric 

Holmes leaned close. “The question is not *How accurate?* but *What is the cost of being wrong?* Consider your world, Trevelyan.” 

### 🩺 Cancer Screening
- **False Negative:** Catastrophic—delayed treatment, death.  
- **False Positive:** Anxiety, tests—annoying, but survivable.  
- **Priority:** Catch every possible tumor.  
- **Metric:** Recall.  

$$
\text{Recall} = \frac{TP}{TP + FN} = \frac{5}{15} = 33\%
$$

Holmes jabbed the paper. “There lies your disaster.”

Dr. Trevelyan’s head sank. “It wasn’t 99%. It was 33%. Ten Lucys… lost.”


## The Crime in the Numbers  

Holmes delved deeper and drew forth a memorandum.
“They knew the machine missed tumors in younger women,” he said, voice cold, “yet hid it behind glossy promises. Not a flaw of science—but of men.”

Reforms followed. The AI was rebuilt to prioritize recall. False alarms increased, but fewer Lucys were missed. Every positive was now reviewed by a physician before action.   


## Holmes’s Reflection

By the fire, I asked, “Holmes, then, what is accuracy?”

He smiled thinly.
“Accuracy, Watson, is the laziest storyteller. It smooths jagged edges and whispers comforting lies. The Confusion Matrix tells the whole story—it shows where the landmines lie. And sometimes, saving a life demands enduring a thousand false alarms.” 


## Other Lessons from Holmes

- **Spam Filter**: False negatives—spam in the inbox—are tolerable. False positives—an urgent letter lost—are catastrophic. Thus, the wise man demands **Precision**:

$$
\text{Precision} = \frac{TP}{TP + FP}
$$


- **Loan Approval**: A balance of perils. Deny a worthy man credit—bad. Approve a rogue—worse. Both errors cut, though differently. Here the **F1-score**, harmonising recall and precision, is the truest guide.

$$
F1 = 2 \cdot \frac{\text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}}
$$

 
- **Common Disease**: Where disease is frequent and errors less dire, **Accuracy** regains some meaning. But only, Watson, if the classes are balanced. Always consult the matrix before you trust the percentage.


## TL;DR

- Accuracy lies when classes are imbalanced (like rare diseases). Ignore it alone!

- Maximize RECALL when missing a positive is CATASTROPHIC (Cancer screening, search & rescue). Catch everything, even if it means false alarms.

- Maximize PRECISION when false positives are CATASTROPHIC (Spam filters, loan approvals for high-risk). Be super sure when you say "YES".

- Use F1-SCORE when BOTH false positives and false negatives are costly and need balancing (Loan approvals, general classification).

- ALWAYS look at the full Confusion Matrix. The story is in the quadrants. Know your costs!