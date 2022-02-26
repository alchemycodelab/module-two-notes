# Grading Guidelines
- and helpful hints for a great week!

Your project should have the following features:

- Deployed on Netlify
- Thoughtful CSS
- Built in React, using hooks to manage state
- Some group collaboration tool to organize features like Miro. (You'll link to this tool in your Canvas submission).
- Supabase Auth and protected routes.
- User should be able to create, read, update, and delete rows from a supabase database. You should write functions to manage this in `fetch-utils.js` or some similar file.
- Rows in supabase should have a `user_id` property that links those rows to a particular user. RLS rules should be set up to let the user CRUD rows that have their `user_id`.
- There should be some 'List/Detail' element to your app.
    - The user should be presented with a list fetched from supabase
    - When the user clicks on the list item, they are navigated to that item's detail page, using query parameters (fetch that item from supabase on load)
- A "Built By" page detailing who worked on the project
- Your app hits a netlify function to hit a 3rd party API that requires an Auth token. The function that manages this should be in `fetch-utils.js` or something similar. The netlify function should accept and use query parameters (or POST body if you're feeling ambitious).
    - Ideally, you will store data from the 3rd party API in your supabase tables (like the movie watchlist app). I understand if this doesn't really fit your app, but I would like to see this.
- One of the following:
    - At least two tables in supabase (not including a user's table)
        - One table should have a foreign key pointing to another table (like `participants` having a `workshop_id`)
    - Your app is a sufficiently complex "game" that stores game state in supabase.

The two questions I ask while grading: 1) does the app work? and 2) how would I feel if somebody asked me to maintain this app (i.e., WTFs per minute)?

You will receive a grade as a group, as well as an individual grade.

Generally speaking, those grades will be the same. These grades will usually be different only in cases where it becomes obvious that one or more group members contributes markedly less or otherwise damages the group's ability to work. In a group project, this is of course difficult thing to pin down, and there are three major ways I'll evaluate this participation:

### Commit history
- Everybody knows that commit history is never the whole story. Indeed, in pair/mob programming a navigator contributes a great deal without making a signle commit! Nonetheless, commit history is one metric we use to evaluate individual participation. 
- To this end, be vigilant to make sure you are personally making a fair number of commits to the group repo. 
    - This may mean having candid conversations during morning standup about how you feel you are not getting enough time as the driver.
- In the "Sprint Week Project Submission" assignment on canvas, we'll ask you to upload a screenshot of the Insights -> Contributors graph from github, which describes the commits by each team member. 
### Peer feedback. 
- In the "Sprint Week Project Submission" assignment on Canvas, in addition to describing their own contributions, you will be asked to evaluate you team dynamic in general, and to specifically  evaluate each member's contributions.
### Instructor check-ins. 
- We'll visit your group at least once daily to ask how the project is going. In addition to a progress check, this is a _temperature check_. We'll be looking to see if the group dynamics feel off. Specifically we'll ask ourselves: does one person seem to be dominating the project to the detriment of the group? In a group project, this can be just as damaging (perhaps more damaging) than a coder who contributes nothing to a codebase.

# Group dynamics

### Collaborating Contributors vs Battling Experts
- Group dynamics are probably the most challenging aspect of a group project. Every unsuccessful project I can think of started with unsuccessful team dynamics. 
- Given the choice, consider which group most you would rather work with:
    1) a group of beginning coders who are good listeners, emapthetic and entusiastic teammates with "strong opinions, loosely held" and who want to have fun building something and learning.
    2) a group of programming experts who are committed to getting their way, obsessed with outcomes, and oblivious to the way their attitude affects their team
- Group 2 is incredibly painful. You will be walking on eggshells all week and we can feel the tension immediately when we visit. This is a miserable week emotionally, and ironically, the project quality will suffer compared to Group 1 because of group paralysis. 

### Expectations and Boundaries
- When selecting a group, be curious about the amount of 'extra' work you're wanting to put into the project. Obviously, you're required to work on the project from 9-6 during sprint week, but some groups work outside these hours as well. Are you in a group like this? Do you _want_ to be in such a group? Set these expectations ahead of time.
- No 'cowboy coding'
    - "If you want to go fast, go alone; if you want to go far, go together."
    - "Slow is smooth, smooth is fast"

### Common conflicts
- Look at yourself and your group and be conscious about how some people have historically been excluded from the benefits of tech work--specificially, women, people of color, and LGBTQ+ people. 
- Ask as a group: what are you going to do to make sure you don't reproduce that exclusion in your own sprint week group?
- Specifically, the most common complaint we hear: womens' opinions and contributions are ignored, devalued, or disregarded by men in their group.
    - Note that men in this kind of group _don't always notice that there's even a problem_. After all, if you're feeling this way, it is difficult and risky to bring your feelings to your group. It is often easier to just swallow your feelings and endure an unhappy week.
    - This dynamic creates bad feelings (for all parties) that can last for the rest of the cohort. You'll want to be able to depend on your cohort-mates for easy job referrals throughout your career: don't burn this bridge.
- One strategy for preventing this kind of dynamic is to plan daily (maybe twice-daily) check-ins where you do not even talk about code. It might be worthwhile to set a timer and give everyone a minimum of 1 minute uninterrupted time to speak. This is a good idea even if everybody chooses fill that time with silence.
- What if during a check-in, somebody (specifically, a person from a marginalized group) remarks that they are feeling disregarded or devaluded as a team member? 
    1) Resist defensiveness. 
    2) Thank this team member for doing the hard work of bringing up the problem: after all, they want a better group dynamic, and a better group dynamic helps everybody.
    3) Ask: what can we as a team--and I personally--do to repair this situation?
