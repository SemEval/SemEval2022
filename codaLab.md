---
title: CodaLab
---

**Quick links:** [http://codalab.org](http://codalab.org), [SemEval-2022 tasks](https://semeval.github.io/SemEval2022/tasks), [SemEval-2022 home](https://semeval.github.io/SemEval2022)

This page has two sections:
1. Setting up CodaLab competition websites (for task organizers)
2. Participating in CodaLab competitions (for task participants)

## Setting up a CodaLab competition website for SemEval-2022 

### Benefits of CodaLab:
 - No need to manually download and manage system submissions.
 - Evaluation scripts run (and results collected) fully automatically.
 - Participants can easily test their output formats (e.g., on the trial data) without any help from organizers.
 - CodaLab supports setting specific task start and end dates for individual tasks.
 - CodaLab supports multi-phase evaluation.
 - CodaLab allows upload, download, and versioning of your datasets and scoring programs.
 - CodaLab leaderboards can include multiple different scores and can be anonymous if desired.
 - The CodaLab website can remain active even after the competition, allowing others to upload their submissions and be automatically evaluated.

Note that CodaLab competitions is not the same as CodaLab worksheets. There is no requirement of participants to upload any code to CodaLab. In the vast majority of competitions, participants simply upload their output files, as in all past SemEvals.

### Tutorials:
 - This tutorial by Tristan Miller is likely to be extremely useful: [Slides](https://www.hse.ru/data/2017/05/31/1171931089/CodaLabCompetitions.pdf), [Video](https://www.youtube.com/watch?v=Ptx93cSBdNY)
 - [Isabelle Guyon's Codalab tutorial](https://www.youtube.com/watch?v=mU1yEEMrMvY)
 - [CodaLab Quickstart Guide](https://github.com/codalab/codalab-worksheets/wiki/Quickstart)
 - [Running a Competition](https://github.com/codalab/codalab-competitions/wiki/User_Running-a-Competition)
 - [Competition Roadmap](https://github.com/codalab/codalab-competitions/wiki/User_Competition-Roadmap)

### Some resources that should help you in this process:
 - We have put together a [sample CodaLab competition](https://github.com/bethard/semeval-codalab) that you can use as a starting point for your task’s competition: 
 - Example Competition on CodaLab for Emotion Intensity: [CodaLab site](https://competitions.codalab.org/competitions/16380), [Code](https://github.com/felipebravom/EmoInt/tree/master/codalab)
 - Example Competition on CodaLab for Clinical TempEval: [CodaLab site](https://competitions.codalab.org/competitions/15621), [Code](https://github.com/bethard/clinical-tempeval)
 - Post your questions and issues on CodaLab [here](https://github.com/codalab/codalab-competitions/issues)
   - Search first to see if a similar question has already been asked and answered.
   - You can also post your questions to the semeval-tasks@googlegroups.com mailing group where other task organizers and SemEval organizers might be of help.

### Important Notes:
 - Experiment with the [testing version of Codalab](https://competitions-test.codalab.org/) before uploading an official competition.
 - Create only a single CodaLab competition, even if you have multiple subtasks. Multiple CodaLab competitions solve very few problems and make things more complicated.
   - If you have multiple subtasks, define a submission file format that is the same regardless of how many subtasks someone participants in.
   - If you have multiple subtasks, your evaluation script will have to handle cases where a participant makes submissions for only one or some subtasks.
 - Ensure that your CodaLab competition defines a detailed `overview.html`, `data.html`, and `evaluation.html`. These are the key pieces of documentation for your task, and they're what potential participants will be looking at.
 - While the CodaLab browser-based interface can update many parts of a competition, there are several known circumstances where the only way to modify part of a CodaLab competition is to delete and recreate it, uploading a new `competition.yaml`, etc. Some such circumstances are:
   - Adding or removing `.html` files from the CodaLab website
   - Modifying the leaderboard (e.g., adding new evaluation metrics)
   - Adding a new phase (if done via the browser-based interface, leaderboards will not display)
 - Make sure your evaluation script throws errors (and exits with an error status) for all formatting issues you are able to detect in system submissions. This will ensure that ill-formatted submissions do not count against a participant’s submission limit.
   - A very common error is for participants to include an extra subdirectory in their submission. Please make sure your evaluation script detects and handles this error.
 
### Phases of the competition:

Consider setting up at least the following three phases for your competition:
1. **Practice phase:**
   - Runs from now until roughly 10 Jan 2022 (official dates TBA)
   - Uses the official evaluation script, but on the trial data
   - Set maximum submissions to something high like 999
   - Make the leaderboard public
   - Allows participants to check their formatting
2. **Evaluation phase:**
   - Runs from roughly 10 Jan until 31 Jan 2022 or some subset, if your competition is shorter (official dates TBA)
   - Uses the official evaluation script and the official test data
   - Set maximum submissions to a number less than or equal to 10. If the number is greater than 1, a suggested option is to tell the participants that only their final valid submission on CodaLab will be taken as the official submission to the competition. The participants can still describe contrastive runs in their system paper. If you choose to accept more than one official submission per team, then you will have to look for the other submissions in the 'submissions' tab (the leaderboard only shows the latest valid submission).
   - Hide the leaderboard (`leaderboard_management_mode: hide_results`)
   - Determines the official leaderboard rankings for SemEval
   - At the end of the evaluation period, make a copy of the leaderboard and save it as backup in case the leaderboard gets updated (especially needed if you have not set up a post-evaluation phase)
3. **Post-Evaluation phase:**
   - Runs from roughly 31 Jan (or earlier, if your evaluation length is shorter than the maximum allowed time) (official dates TBA)
   - Uses the official evaluation script and the official test data
   - Enable “Auto migration” of submissions from Evaluation phase to this phase
   - Set maximum submissions to something high like 999
   - Make the leaderboard public
   - Allows participants to score “contrastive runs” that can be included as part of the analysis in system description papers. Also allows scoring of future systems interested in the task beyond SemEval-2022
   - At most one submission for each participant can be displayed on the leaderboard.

Participants must click the Submit to Leaderboard button underneath one of their submissions to display those results on the leaderboard. (Task organizers may override the participants using the `SHOW` setting on the `Submissions` page.)
- If you choose to allow more than 1 submission in your phases, organizers can see all submissions in the `Admin Features` -> `Submissions` tab.
- If you choose to allow more than 1 submission, it is especially important to consider hiding the leaderboard during the Test phase to prevent participants from making a large number of submissions, viewing their results, and then choosing the best to place on the leaderboard (i.e., tuning to the test data).

## Participating in a CodaLab competition:
1. Create a [CodaLab](https://competitions.codalab.org/) account. Sign in.
2. Edit your profile appropriately. Make sure to add a team name, and enter names of team members. (Go to `Settings`, and look under `Competition settings`.)
3. Proceed to task webpage on CodaLab. Read information on all the pages.
4. Download data: training, development, and test (when released)
5. Run your system on the data and generate a submission file, which must follow the official submission format outlined for your task. CodaLab does not place any restrictions on the name of the zip file.
6. Make submissions on the development set (Phase 1).
   - Wait a few moments for the submission to execute.
   - Click on the `Refresh Status` button to check status.
   - Check to make sure submission is successful.
     - System will show status as `Finished`.
     - Click on `Download evaluation output from scoring step` to examine the result. If you choose to, you can upload the result on the leaderboard.
     - If unsuccessful, check error log, fix format issues (if any), resubmit updated zip.
7. Once the evaluation period begins, you can make submissions for the test set. The procedure is similar to that on the dev set. These differences apply:
   - The leader board will be disabled until the end of the evaluation period.
   - You cannot see the results of your submission. They will be posted on a later date after the evaluation period ends.
   - You can still see if your submission was successful or resulted in some error.
   - In case of error, you can view the error log.



#### CONTACT
Contact information for organizers of individual tasks will be available soon. General questions about SemEval organization should be directed to <semeval-organizers@googlegroups.com>.
