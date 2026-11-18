<div align="center">

![Rasayanik Mistri | Chemical Engineering in Hinglish](rasayanik-mistri-banner.png.jpeg)

# Rasayanik Mistri
### Chemical Engineering in Hinglish

**Real Science • Real Engineering • Real Stories**

</div>

<p align="center"> <img src="YOUTUBE LOGO.png" alt="RM GATE Lab logo" width="140"> </p> <h1 align="center">RM GATE Lab 🎲</h1> <p align="center"><b>Chemical Engineering in Hinglish</b></p>

A free, mobile-friendly chemical engineering practice game. Roll a dice, get a question, beat the timer, and learn from a Hinglish explanation in the way of Ayon, Drishti or Host RM.
 
**Live demo:** https://atul04pramanik.github.io/rasayanik-mistri-gate/RMindex.html
 
> **Status: working prototype.** It has **261 questions** across **14 topics**, runs entirely in your browser, and has no accounts or leaderboards yet. It includes a Mistake Notebook and Bookmarks. See the [roadmap](#roadmap).
 
---
 
## How it works
 
### 1. Roll the dice
Tap **Roll the dice**. The die spins and the app picks one question for you.
 
- **Faces 1 to 5:** a normal round. The app picks a question at random, but it favours topics where your accuracy is low and questions you haven't seen yet.
- **Face 6: Weakness Distillation.** Roll a 6 to enter a Weakness Distillation round. The app identifies the weakest topic *among the currently eligible questions* and selects a question from that topic. Catalyst points earned in this round are **doubled**. Your selected topic and difficulty filters still apply.
- You can lock the dice to one topic with the topic filter, and to one difficulty level with the **All / Easy / Medium / Tricky** buttons. Your choice is remembered next time.
- Filters apply first: the dice only picks from questions that match your topic and difficulty choices. For example, with **Thermodynamics + Tricky** selected, a 6 looks for the weakest topic among those questions only, so the round stays inside Thermodynamics.
- If a topic has no questions at the chosen level, the app says so and picks any level of that topic instead.
- The app avoids selecting the same question twice consecutively whenever more than one eligible question is available. If your filters leave only one question, it can repeat.
### 2. Beat the timer
Every question has a 45-second "Time remaining" bar. It runs on a real clock deadline, so it stays accurate even if the browser lags or the tab is in the background. The bar turns red in the last 30% of the time. If it runs out, the question counts as wrong.
 
### 3. Answer and learn
Options are shuffled fairly every time (Fisher-Yates), so you can't memorise the position. After you answer you get:
 
- an instant right/wrong highlight,
- a verdict from one of three characters,
- a short **Hinglish explanation**, and on some questions a **Trap** line that names the mistake most students make,
- a **Next question** button to keep going.
| Character | Role | Appears on |
|---|---|---|
| 🧪 **Ayon** | Nerdy scientist | Concept and theory questions |
| 🏭 **Drishti** | Practical engineer | Numericals and plant-practice questions |
| 🎙️ **Host RM** | Mentor | Exam strategy and calculation questions |
 
### 4. Points and stats
 
| Result | Catalyst points |
|---|---|
| Correct | 10, plus 1 for every 5 seconds left on the timer |
| Correct in a Weakness round | The above, doubled (maximum about 38) |
| Wrong or timed out | 0, and your streak resets |
 
The header shows **Solved**, **Accuracy**, **Streak** and **Catalyst** points, plus your current weakest topic and your accuracy at each difficulty level (Easy, Medium, Tricky). Points are a score only for now; they don't unlock anything yet.
 
### 5. How "weakest topic" is calculated
For each topic the app tracks attempts and correct answers, then calculates a smoothed accuracy so one lucky or unlucky answer doesn't swing it:
 
```
accuracy = (correct + 2.5) / (attempted + 5)
weakness = 1 - accuracy
question weight = (0.3 + 1.7 × weakness) × (1.2 if never seen, else 1)
```
 
A question is then chosen at random using those weights, so weak topics come up more often but strong topics still appear. Topic accuracy is measured from your history across all difficulty levels, but a Weakness round only considers topics that still have eligible questions after your filters.
 
### 6. Mistake Notebook
Every wrong or timed-out answer is saved automatically to your **Mistake Notebook**. Tap any saved mistake to open it with the full question, all four options, the correct answer marked and the explanation, and use **Practice this now** to try it again whenever you like (practice does not change the review schedule unless you get it wrong). Tap **Review due mistakes** to revisit them on a spaced schedule:
 
| Step | What happens |
|---|---|
| Wrong answer | Saved, first review due in **1 day** |
| Correct in review | Next review in **3 days**, then **7 days** |
| Correct a third time | **Mastered**, and it leaves the notebook |
| Wrong in review | Back to day 1 |
 
### 7. Bookmarks
Save useful questions to your Bookmarks list for later practice. Tap **☆ Save question** while practising (it turns into **★ Saved**). You can open a saved question, practise it again or remove it from the list. Bookmarks stay saved even if you later answer the question correctly. Bookmarks are stored locally and are included in progress backups.
 
The two lists have different jobs:
 
| | Mistake Notebook | Bookmarks |
|---|---|---|
| Stores | Questions you answered **incorrectly** | Questions **you chose** to keep |
| Added | Automatically | Manually, with ☆ Save question |
| Removed | When mastered after 1, 3 and 7 day reviews | Only when you remove it |
| Schedule | Spaced reviews | None, practise whenever you like |
 
### 8. Back up your progress
Use **Export progress** to download a `.json` backup and **Import progress** to restore it on another device or after clearing your browser. Backups include your stats, Mistake Notebook and bookmarks. Imported files are validated and cleaned before use.
 
### Privacy
Your practice progress, mistakes and bookmarks are stored locally in your browser using `localStorage`. There is no account system, application backend or analytics service. Progress does not automatically synchronise between devices, and clearing your browser data, or opening the app on a different web address, starts you from zero. Export your progress periodically to keep a backup. The app loads its Google Fonts stylesheet externally when an internet connection is available; everything else is in the page itself. The **Reset my stats** button wipes your stats, mistakes and bookmarks after a second tap within 5 seconds.
 
---
 
## Difficulty levels
 
Every question is tagged with a colour-coded badge:
 
| Level | Meaning | Questions |
|---|---|---|
| **Easy** | Definitions and direct recall | 128 |
| **Medium** | One concept or a short calculation | 79 |
| **Tricky** | Multi-step numericals, or questions with a common trap | 54 |
 
Difficulty labels are editorial judgements by the creator, not official GATE classifications. Please [open an issue](../../issues) if a question feels mis-labelled.
 
## Topics (14)
 
Thermodynamics · Fluid Mechanics · Heat Transfer · Mass Transfer · CRE · Process Control · Mechanical Operations · Chemical Technology · Polymer Technology · Membrane Separation · Process Calculations · Numerical Methods · Plant Design · Environment
 
## Design
 
- Compact mobile-first layout, and a two-column dashboard on screens 900 px wide or more (controls, Mistake Notebook and Bookmarks on the left, the question on the right).
- Light and dark themes that follow your device setting.
- Footer with Follow and Contact sides and built-in social icons (X, Instagram, YouTube, GitHub, email), with no extra files to load.
- The RM logo appears in the header, as a faint background watermark, and as the browser tab icon.
- Keyboard-friendly buttons with visible focus outlines, and reduced-motion settings are respected (including smooth scrolling).
## Tech
 
- One file: `RMindex.html`, with plain HTML, CSS and JavaScript. No framework, no build step, no backend. The logo is embedded inside the file.
- Progress uses browser `localStorage` and does not automatically sync across devices (use Export and Import to move it).
- Only outside resource: the Google Fonts stylesheet (falls back to system fonts).
## Run it or deploy it
 
**Locally:** download `RMindex.html` and open it in any browser.
 
**On GitHub Pages:** upload the file to a public repo, then go to *Settings → Pages*, choose the main branch and the root folder, and save. For the clean GitHub Pages address (`https://username.github.io/repo/`), the file must be named `index.html` and sit in the repository root. If you keep the name `RMindex.html`, the page opens at `.../RMindex.html`, which is the live demo link above.
 
**Updating later:** in the repo choose *Add file → Upload files*, upload the new file with the same name, and commit. The live site updates in a minute or two.
 
## Contact and support links
 
Near the top of the script in the HTML file there is a block:
 
```js
const CONTACT={email:"",x:"",instagram:"",youtube:"",github:"",issues:""};
```
 
The footer is split in two: **Follow** (X, Instagram and YouTube icons) on the left and **Contact** (GitHub icon and the support email) on the right. The released file is already filled in with the Rasayanik Mistri profiles, the GitHub profile and the support email. To change them, edit the values (links must start with `https://`) and the footer shows your social links and a "Help and complaints" email. If you add your repository's issues link, or an email, a **Report a problem with this question** link appears after every answer. Empty values stay hidden.
 
## Add or fix questions
 
Questions live in one array inside the HTML file. Each row is:
 
```js
["Th", 1, "ayon", "Question text?", ["Option A", "Option B", "Option C", "Option D"], 3, "Hinglish explanation.", "Optional trap line."]
```
 
| Position | Meaning |
|---|---|
| 1 | Topic code: `Th` `Fl` `Ht` `Mt` `Cr` `Pc` `Mo` `Ct` `Pl` `Mb` `Pr` `Mx` `Pd` `En` |
| 2 | Difficulty level: `1` Easy, `2` Medium, `3` Tricky |
| 3 | Speaker: `ayon`, `drishti` or `host_rm` |
| 4 | Question text |
| 5 | The four options |
| 6 | Index of the correct option (0 is the first) |
| 7 | Explanation |
| 8 | Optional trap line |
 
Add new rows at the **end** of the array so existing players' saved progress stays correct.
 
## Contributing
 
- **Report an error:** [open an issue](../../issues) with the question text, what looks wrong and what you think is correct, or use the **Report a problem with this question** link shown after each answer in the app.
- **Suggest new questions:** open an issue or a pull request with the rows in the format above, the source of each question, and a short explanation. Please only submit questions you have the right to share, and double-check the answer key.
- **Keep ids stable:** add new rows at the end of the array and avoid rewording existing questions, because saved mistakes and bookmarks are matched by question text.
## Roadmap
 
These are **not built yet**:
 
- [ ] Real GATE previous-year questions, including MSQ and NAT types
- [ ] Accounts and cloud-saved progress
- [ ] Private groups with join codes, and group leaderboards
- [ ] Duel mode (challenge a friend on 5 questions)
- [ ] GitHub-style activity heatmap
- [ ] Daily reminder notifications
- [ ] Levels that unlock with Catalyst points
- [ ] Performance dashboard (topic-wise accuracy and progress over time)
- [ ] Timed GATE mock test mode
## Credits and disclaimer
 
- Questions are adapted from five sources: the **BARC 2022 Chemical Engineering model paper** (GATExplore.com), the technical section of the **IFFCO 2024 Mains Chemical Engineering paper**, a **Chemical Technology Part 1 practice set**, two **RCFL** practice sets (50 MCQs and the 2024 PYQ paper), and the **HURL Chemical GET 2025 PYQ set** compiled by Team Rasayanik Mistri. HURL questions that the compilation itself marked as flawed, ambiguous or approximate were left out. The Hinglish explanations and character voices were written with **Claude AI** (by Anthropic); some English solutions come from the Team Rasayanik Mistri HURL compilation.
- Published answer keys were re-checked, and the corrected answer was used where a key looked wrong. Examples: the Gilliland correlation estimates *theoretical* stages, laminar Fanning friction factor is 16/Re, laminar boundary layer thickness keeps increasing with distance, and the syrup evaporation problem gives 214 t of water. Questions that were flawed, ambiguous or internally inconsistent were left out.
- This is a **practice aid, not an official source**. Explanations were written quickly and may contain errors. Please verify against your textbooks before relying on them in an exam.
- This project is not affiliated with or endorsed by BARC, IFFCO, RCFL, HURL, GATE, GATExplore or Anthropic. Check the reuse terms of the source material before promoting it widely.
*Add a LICENSE file of your choice before inviting contributions.*
 
---
 
Created by **Atul Pramanik**, Creator of **Rasayanik Mistri™**, and built with **Claude AI** by Anthropic.
 
© 2026 Atul Pramanik. The app design, code and original explanations are all rights reserved unless you add an open-source license. Third-party question wording remains with its original sources. Rasayanik Mistri™, RM GATE Lab and the RM logo are brand names and marks used by Atul Pramanik.
