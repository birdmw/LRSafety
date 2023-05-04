# LRSafety
checklist for liberty ridge

I wanted to see if I could produce a checklist that a climber could use on the mountain, made from the aggregate wisdom etched into the last 20 years of Accident Reports to help them to evaluate their turn-around status, which is so difficult to do on the mountain where objectivity is pitted against one's motivation.

SETUP & DATA:
  In the last 20 years, there have been 21 accident reports written specific to Liberty Ridge. I chose to use modern reports because gear, techniques, and conditions are evolving over time, and thus more recent data would have the more relevant insight. (See Attached: 21_accident_reports.txt)

METHODOLOGY:
There are two main phases

1. Transforming the data into a common checklist format. There are 21 checklists here, each corresponding to an Accident Report. Each accident report was fed through ChatGPT with the explicit (prompt engineered) task of generating a checklist. GPT is asked to make a list whereby if the climbers on that particular trip had used it, the tragedy they encountered stood the best chance of being averted. (Atached: all_checklists.txt)

2. Combining this data into a singular checklist which preserves and highlights "themes". This part is tricky. The trick is to convert the checklists into vector embeddings and combine them not by proximity, but by distance through (bear with me) agglomerative hierarchical clustering. Imagine a bracket tournament (like in team sports), where instead of a team losing or winning, the best half of the team gets to go on, join up with the best half of the other team, and continue. We can do that with concepts within the checklists. In fact, we aren't even taking the best players, we are taking the best parts of each player, and making a better player. Here is an example of one such transformation combining reports:

Report 1:
  Gear
    (1pt) low on one item of (fuel, food, battery)
    (2pts) Low on two items
    (3pts) low on 3 items or empty on one

Report 2:
  Gear
    (2 pt) didn't bring a communication device
    (3 pt) dropped my only nalgene

           Combined Report:
               (1 pt) low on one item
               (2 pt) low on two items or no comms
               (3pt) critical gear missing or low supply in several categories

This is how I combined wisdoms: on a category by category basis. This is done using the Magic of LLMs like ChatGPT and is beyond the scope of this email.

The last notable trick is to organize the bracket so that the most disparate checklists combine first. We do this using maximum distance agglomeration. This serves to weed out "one-off" concepts like "If only I had a hand warmer I would be safe" because they are forced to combine with themes that reoccur most often.

CODE:
          Attached: 01_accident reports.ipynb
          Attached: 02_combining.ipynb

RESULT:
"safety checklist.docx" represents the final product of this project and is ONLY built for Liberty Ridge. None of it was written by human hands, however the heuristic & algorithm were designed to generate a checklist which would stand the best chance of preventing tragedy on Liberty Ridge.

All categories were naturally discovered, and no human intervention was needed at any step other than prompt engineering.

Finally I ran many scenarios to rescale the final scoring system to a "makes sense" set of threshold as decided by chatgpt. Chatgpt agrees that these new thresholds are sensical - and I verified it with my own intuition as well.

CONCLUSION:
The final checklist might seem obvious, or simplistic, and an experienced Ranger or Guide might balk at some elements like "Team separated or isolated in hazardous conditions (5 points)" not being an IMMEDIATE turn around condition, but there is deep reasoning for this being there, and I would implore a skeptic to spend some time with it - or tweak it!

POSSIBLE PROBLEMS:
There are real gems in these trip reports, such as when the team, 4000 feet from the summit, progressed 1200 feet, bivyd, and continued the next day. Had they evaluated their progress, they could have suspected they needed at LEAST two additional days of climbing through rough conditions. This checklist does not precisely capture this nuance, and one concern might be that a reader might feel invited to gloss over these technical points. Another example is "If the freezing line is below 14k, don't go up Liberty Ridge. The reason I decided to move ahead with this project is because I decided this checklist is not meant to replace reading accident reports. I see it merely as a tool, for a tired climber, to remember the reports, and if used in this way, I think it should bear value.

This safety checklist was entirely computer generated, and as such can be applied, repeatedly, without limit, to any set of trip reports including whole mountains, all of the cascades, or such as in this report, applied to a single route (Liberty Ridge) - and more generally wherever you have a collection of trip reports. At its most general, this is a generic method for combining wisdom from accident reports of any kind into any kind of safety checklist.