# Guitar Fretboard Trainer

## Project Status

Candidate release: **v2.0**

Last tagged known-good production release: **v1.2**

GitHub repository: `PessimisticPress/guitar-fretboard-trainer`

GitHub Pages site: `https://pessimisticpress.github.io/guitar-fretboard-trainer/`

The production application is the repository's `index.html` on the `main` branch. GitHub releases/tags preserve known-good checkpoints.

## Project Purpose

Guitar Fretboard Trainer is a mobile-first web app for learning and memorizing note locations on a standard six-string guitar fretboard.

The primary use case is frequent, focused practice on an iPhone. The app supports both deliberate practice and, beginning in v2.0, speed/fluency practice through Timed Challenge.

## Development Workflow

1. Discuss proposed features or changes in the Guitar Fretboard Trainer ChatGPT Project.
2. Start from the latest production `index.html` uploaded to the Project.
3. Preserve existing working behavior unless a requested change explicitly requires changing it.
4. Generate a complete replacement `index.html`.
5. Replace the repository's `index.html` on `main`.
6. GitHub Pages automatically republishes the site.
7. Test the live GitHub Pages version on the iPhone.
8. When the version is confirmed good, create a GitHub release/tag as a known-good checkpoint.
9. Keep the ChatGPT Project copy of `index.html` synchronized with the latest known-good production version.

GitHub is the authoritative source for the currently published application.

## Core Quiz Types

### Name the Note

The trainer displays a specific string and fret position and asks the player to identify the note.

### Find the Note

The trainer gives a target note and string and asks the player to identify the correct fret.

The correct fretboard position must **not** be displayed or highlighted before the user answers or chooses Reveal in Standard Practice. In Timed Challenge, the correct position may appear only after an answer has been submitted.

## Practice Styles

### Standard Practice

Standard Practice preserves the established v1.2 behavior.

It includes:

- Accuracy, current streak, and answered metrics
- Reveal and Next controls
- Adaptive repetition of missed positions
- Weak-position tracking
- Persistent standard-practice statistics

Standard statistics must not be altered by Timed Challenge runs.

### Timed Challenge

v2.0 adds Timed Challenge as a separate practice style.

Available durations:

- 30 seconds
- 60 seconds
- 2 minutes

Timed Challenge supports both Name the Note and Find the Note.

#### Timed Scoring

The headline score is **number of correct answers completed before time expires**.

There is no additional mathematical penalty for a wrong answer. A wrong answer already creates a natural penalty because:

1. It does not add to the correct-answer score.
2. The correct answer is displayed briefly while the challenge clock continues to run.

An unanswered question when the timer reaches zero does not count as correct or incorrect.

#### Timed Answer Flow

- The challenge begins with a short `3 → 2 → 1 → GO` countdown.
- The timed clock starts when the first question appears.
- A correct answer displays brief confirmation for approximately 0.3 seconds and automatically advances.
- A wrong answer displays the correct answer for approximately 1.1 seconds and automatically advances.
- The timer continues during wrong-answer feedback.
- If the timer expires during feedback, the challenge ends immediately.
- Reveal and Next are not used during an active timed challenge.

#### Timed Settings Lock

Once a timed challenge begins:

- Practice settings collapse.
- Practice settings are locked until the challenge ends.
- This prevents the challenge configuration from changing mid-run.

#### Adaptive Practice in Timed Mode

Adaptive weighting is **not used** in Timed Challenge.

Every eligible position has equal selection weight so runs using the same settings remain comparable.

The Adaptive Practice toggle continues to apply to Standard Practice only.

#### Timed Personal Bests

Timed personal bests are saved locally.

A personal best is compared only against an **exact matching challenge configuration**, including:

- Quiz type
- Duration
- Selected strings
- Lowest fret
- Highest fret
- Natural Notes Only versus all notes

For example, a 60-second Name the Note run using all strings, frets 0–5, and Natural Notes Only is not compared with a 60-second run using frets 0–12 or chromatic notes.

The pre-challenge screen shows the personal best for the exact current challenge configuration so the player knows the score to beat.

A **View Records** control allows the player to browse saved Timed Challenge personal bests across configurations. The current configuration is identified in the records list.

The results screen shows:

- Correct answers
- Questions attempted
- Accuracy
- Whether the score is a new personal best
- Previous best when one exists
- The exact challenge configuration

#### Timed Challenge Review

After a timed run, **Review Challenge** provides a review based only on the challenge that just ended.

The review groups encountered targets into:

- **Needs Work** — any target missed at least once during the challenge
- **Strong** — targets answered correctly every time they appeared

Each review row shows the target and the number correct out of the number attempted.

Timed Challenge review data is session-specific and does **not** feed into Standard Practice weak-position/adaptive data.

## Practice Controls

### Multi-String Practice

The user can select any combination of the six strings.

All six strings are selected by default.

### Fret Range

The user chooses the lowest and highest fret included in practice.

The current default range is frets 0–5.

### Natural Notes Only

Natural Notes Only is enabled by default.

When enabled, accidental answer buttons are visually hidden rather than removed from the answer grid. Their positions remain as empty spaces, preserving the visual spacing of the chromatic scale.

Turning Natural Notes Only off restores accidental buttons in those same positions.

### Adaptive Practice

Adaptive practice repeats missed positions more frequently in Standard Practice.

Adaptive practice is enabled by default in Standard Practice and is intentionally disabled for Timed Challenge.

## Settings and Main-Screen Hierarchy

Practice Settings are collapsed by default.

The collapsed Settings row summarizes:

- Practice style
- Timed duration when applicable
- Quiz type
- Selected string scope
- Fret range
- Natural Notes Only versus all notes

Adaptive status is intentionally not included in the collapsed summary.

Expanded Settings contain:

1. Practice Style
2. Timed Duration when Timed is selected
3. Quiz Type
4. String selection
5. Fret range
6. Natural Notes Only
7. Adaptive Practice

The intended Standard Practice hierarchy is:

1. App title and subtitle
2. Settings
3. Accuracy, Streak, and Answered metrics
4. Active quiz
5. Weak Spots and Reset All Stats

In Timed Challenge, the normal metrics are replaced by:

- Time remaining
- Correct answers

The quiz remains the visual focus.

## Fretboard Display Rules

The fretboard follows guitar tablature orientation:

- High E is the **top** string.
- Low E is the **bottom** string.

This orientation must not be reversed.

In Find the Note mode, never visually reveal the correct position before the user answers.

## Data and Persistence

The app uses browser local storage.

Saved data includes:

- Standard-practice statistics
- Weak-position counts
- Timed personal bests

The most recent Timed Challenge review is kept only for the current in-app challenge result and is not stored as long-term weakness data.

Existing v1.x standard statistics should remain compatible with v2.0. If older saved data does not contain timed personal-best storage, v2.0 initializes that portion without resetting existing statistics.

Reset All Stats clears standard statistics, weak spots, and timed personal bests.

## Mobile Design

The iPhone is the primary target.

Prioritize:

- Large tap targets
- Legible text without zooming
- No unnecessary horizontal scrolling
- Efficient vertical space
- Clear fretboard visualization
- Safari and iPhone Home Screen compatibility
- Keeping configuration secondary to actual practice

Desktop compatibility is useful but secondary.

## Technical Architecture

The application remains intentionally simple:

- One `index.html` production file
- HTML
- CSS
- Vanilla JavaScript
- No external framework
- GitHub Pages hosting

Preserve this architecture unless a future requirement genuinely justifies changing it.

## Update Rules

1. Start from the latest known-good production `index.html`.
2. Preserve existing working features unless explicitly changing them.
3. Avoid unrelated visual or behavioral redesigns.
4. Maintain TAB-style fretboard orientation.
5. Maintain multi-string selection.
6. Never expose Find the Note answers before the user responds.
7. Preserve existing saved standard statistics.
8. Keep Timed Challenge data separate from Standard Practice statistics.
9. Timed Challenge must not use adaptive weighting.
10. Timed personal bests must compare only exact matching configurations.
11. Keep the app mobile-first.
12. Generate a complete replacement `index.html` for deployment.
13. Regression-check Standard Practice before treating a v2 build as production-ready.

## Known-Good Releases

- **v1.0** — original known-good baseline.
- **v1.1** — all strings selected by default; Natural Notes Only enabled by default; accidental buttons hidden while preserving grid positions.
- **v1.2** — collapsible Settings, compact settings summary, Quiz Type moved into Settings, and metrics placed immediately above the quiz.
- **v2.0** — final candidate introducing Timed Challenge, exact-configuration personal bests, visible records, pre-challenge best-to-beat display, and per-run Challenge Review; do not mark known-good until tested and tagged.

## Future Ideas Not Yet Implemented

- Response-time tracking in Standard Practice
- Smarter weak-position analysis using both accuracy and response speed
- Session summaries
- Practice presets
- Mastery tracking by string and fret
- Visual fretboard heat map
- Progressive fret-range learning
- Sharps-versus-flats display preferences

These remain proposals until explicitly approved.

## Project Philosophy

The goal is immediate fretboard recall, not merely eventual calculation.

Standard Practice should support deliberate learning and correction. Timed Challenge should develop fluency and speed without replacing Standard Practice.

The interface should keep configuration available while making the quiz itself the primary experience.
