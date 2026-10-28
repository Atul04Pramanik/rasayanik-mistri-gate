# rasayanik-mistri-gate
Gamified GATE Chemical Engineering preparation platform
# Rasayanik Mistri: GATE Lab

> *Engineering ko sirf padhte nahi... samajhte hain.*

A free, mobile-friendly chemical engineering practice game. Roll a dice, get a question, beat the timer, and learn from a Hinglish explanation in the voice of Ayon, Drishti or Host RM.

Live demo: `[https://YOUR-USERNAME.github.io/YOUR-REPO](https://atul04pramanik.github.io/rasayanik-mistri-gate/RMindex.html)`

> Status: working prototype. It has 102 questions, runs entirely in your browser, and has no accounts or leaderboards yet. See the [roadmap](#roadmap).

## How it works

### 1. Roll the dice
Tap **Roll the dice**. The die spins and the app picks one question for you.

- **Faces 1 to 5:** a normal round. The app picks a question at random, but it favours topics where your accuracy is low and questions you haven't seen yet.
- **Face 6: Weakness Distillation.** The app finds your weakest topic and picks a question from it. Every point earned in this round is **doubled**.
- You can lock the dice to one topic with the topic filter.
- You never get the same question twice in a row.

### 2. Beat the timer ("Reaction Kinetics")
Every question has a 45-second countdown bar. The bar turns red in the last 30% of the time. If it runs out, the question counts as wrong.

### 3. Answer and learn
Options are shuffled every time, so you can't memorise the position. After you answer you get:

- an instant right/wrong highlight,
- a verdict from one of three characters,
- a short **Hinglish explanation**, and on some questions a **Trap** line that names the mistake most students make.

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

The header shows **Solved**, **Accuracy**, **Streak** and **Catalyst** points, plus your current weakest topic. Points are a score only for now; they don't unlock anything yet.

### 5. How "weakest topic" is calculated
For each topic the app tracks attempts and correct answers, then calculates a smoothed accuracy so one lucky or unlucky answer doesn't swing it:

```
accuracy = (correct + 2.5) / (attempted + 5)
weakness = 1 - accuracy
question weight = (0.3 + 1.7 × weakness) × (1.2 if never seen, else 1)
```

A question is then chosen at random using those weights, so weak topics come up more often but strong topics still appear.

### Privacy
Everything is stored in **your own browser** (localStorage). There is no server, no login and no tracking. Clearing your browser data, or opening the app on another device or address, starts you from zero. The **Reset my stats** button wipes your stats after a second tap.

---

## Topics (11)

Thermodynamics · Fluid Mechanics · Heat Transfer · Mass Transfer · CRE · Process Control · Mechanical Operations · Chemical Technology · Numerical Methods · Plant Design · Environment

## Tech

- One file: `index.html`, with plain HTML, CSS and JavaScript. No framework, no build step, no backend.
- Only outside resource: the Google Fonts stylesheet (falls back to system fonts).
- Light and dark theme follow your device setting.

## Run it or deploy it

**Locally:** download `index.html` and open it in any browser.

**On GitHub Pages:** upload `index.html` to a public repo, then go to *Settings → Pages*, choose the main branch and the root folder, and save. Your link appears after a minute or two.

## Add or fix questions

Questions live in one array inside `index.html`. Each row is:

```js
["Th", 1, "ayon", "Question text?", ["Option A", "Option B", "Option C", "Option D"], 3, "Hinglish explanation.", "Optional trap line."]
```

| Position | Meaning |
|---|---|
| 1 | Topic code: `Th` `Fl` `Ht` `Mt` `Cr` `Pc` `Mo` `Ct` `Mx` `Pd` |
| 2 | Difficulty level (1 to 5) |
| 3 | Speaker: `ayon`, `drishti` or `host_rm` |
| 4 | Question text |
| 5 | The four options |
| 6 | Index of the correct option (0 is the first) |
| 7 | Explanation |
| 8 | Optional trap line |

Found a wrong answer or a typo? Please [open an issue](../../issues) with the question text and what you think is correct.

## Roadmap

These are **not built yet**:

- [ ] Real GATE previous-year questions, including MSQ and NAT types
- [ ] Accounts and cloud-saved progress
- [ ] Private groups with join codes, and group leaderboards
- [ ] Duel mode (challenge a friend on 5 questions)
- [ ] GitHub-style activity heatmap
- [ ] Daily reminder notifications
- [ ] Levels that unlock with Catalyst points
- [ ] An in-app "report a wrong answer" button

## Credits and disclaimer

- Current questions are adapted from the **BARC 2022 Chemical Engineering model paper** (GATExplore.com) and the technical section of the **IFFCO 2024 Mains Chemical Engineering paper**. Where a published key looked wrong, the answer was re-derived (for example the Gilliland correlation estimates *theoretical* stages). Explanations and the Hinglish character voices are original. Questions flagged as disputed or flawed in that source were left out, and two corrected answers (Fanning friction factor for laminar flow, and laminar boundary layer growth) were used.
- This is a **practice aid, not an official source**. Explanations were written quickly and may contain errors. Please verify against your textbooks before relying on them in an exam.
- Check the reuse terms of the source material before promoting it widely.

Created by **Atul Pramanik**, Creator of **Rasayanik Mistri™**.

© 2026 Atul Pramanik. The app design, code and original explanations are all rights reserved unless you add an open-source license. Third-party question wording remains with its original sources.
