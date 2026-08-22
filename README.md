# Guitar Fretboard Trainer

## Project Status

Current known-good production release: **v1.2**

GitHub repository: `PessimisticPress/guitar-fretboard-trainer`

GitHub Pages site:
`https://pessimisticpress.github.io/guitar-fretboard-trainer/`

The production application is the repository's `index.html` on the
`main` branch. GitHub releases/tags preserve known-good checkpoints.

## Project Purpose

Guitar Fretboard Trainer is a small, mobile-first web app for learning
and memorizing note locations on a standard six-string guitar fretboard.

The primary use case is frequent, focused practice on an iPhone. The
interface should keep configuration available without allowing it to
dominate the quiz experience.

## Development Workflow

1.  Discuss proposed features or changes in the Guitar Fretboard Trainer
    ChatGPT Project.
2.  Start from the latest production `index.html` uploaded to the
    Project.
3.  Preserve existing working behavior unless a requested change
    explicitly requires changing it.
4.  Generate a complete replacement `index.html`.
5.  Replace the repository's `index.html` on `main`.
6.  GitHub Pages automatically republishes the site.
7.  Test the live GitHub Pages version on the iPhone.
8.  When the version is confirmed good, create a GitHub release/tag as a
    known-good checkpoint.
9.  Keep the ChatGPT Project copy of `index.html` synchronized with the
    latest known-good production version.

GitHub is the authoritative source for the currently published
application.

## Current Features

### Name the Note

The trainer displays a specific string and fret position and asks the
player to identify the note.

### Find the Note

The trainer gives a target note and string and asks the player to
identify the correct fret.

The correct fretboard position must **not** be displayed or highlighted
before the user answers or chooses Reveal. After an answer or Reveal,
the correct position may be shown.

### Multi-String Practice

The user can select any combination of the six strings for a practice
session.

All six strings are selected by default.

### Fret Range

The user can choose the lowest and highest fret included in practice.

The current default range is frets 0--5.

### Natural Notes Only

Natural Notes Only is enabled by default.

When Natural Notes Only is enabled, accidental answer buttons are
visually hidden rather than removed from the answer grid. Their
positions remain as empty spaces. This preserves the visual spacing of
the chromatic scale and reinforces that E--F and B--C are adjacent while
the other natural-note pairs have an intervening accidental.

Turning Natural Notes Only off restores the accidental buttons in those
same positions.

### Adaptive Practice

The trainer can repeat missed positions more frequently so weaker
fretboard locations receive additional practice.

Adaptive practice is enabled by default.

### Metrics and Weak Spots

The trainer tracks:

-   Accuracy
-   Current streak
-   Questions answered
-   Weak positions

Statistics and weak-position information are saved locally on the
device.

The existing Reset All Stats control resets saved performance data. Do
not add a duplicate reset control.

## v1.2 Interface Design

### Collapsible Practice Settings

Practice Settings are collapsed by default so the primary screen
emphasizes using the quiz rather than configuring it.

The collapsed Settings row displays a concise live summary containing:

-   Quiz type
-   Selected string scope
-   Fret range
-   Natural Notes Only versus all notes

Adaptive/Standard status is intentionally **not** included in the
collapsed summary because it is not sufficiently meaningful without
additional context.

Expanding Settings reveals the existing controls. Settings should not
automatically collapse after the user changes an option; the user
controls when the panel opens and closes.

### Quiz Type Placement

Quiz Type is a practice-setting choice and therefore lives inside the
expanded Settings panel rather than occupying permanent space on the
main quiz screen.

Quiz Type is the first control in expanded Settings.

### Main Screen Hierarchy

The intended top-to-bottom hierarchy is:

1.  App title and subtitle
2.  Collapsed/expanded Settings
3.  Accuracy, Streak, and Answered metrics
4.  Active quiz
5.  Weak Spots and Reset All Stats controls

This ordering is intentional. Settings should remain visually secondary,
while the metrics should feel connected to the active quiz.

## Fretboard Display Rules

The fretboard follows guitar tablature orientation:

-   High E is the **top** string.
-   Low E is the **bottom** string.

This orientation must not be reversed in future versions.

In Find the Note mode, never visually reveal the correct location before
the user answers or chooses Reveal.

## Mobile Design

The iPhone is the primary target.

Changes should prioritize:

-   Large, easy-to-tap controls
-   Legible text without zooming
-   No unnecessary horizontal scrolling
-   Clear fretboard visualization
-   Efficient use of vertical screen space
-   Safari and iPhone Home Screen compatibility
-   Keeping the quiz more prominent than infrequently changed
    configuration controls

Desktop compatibility is useful but secondary.

## Data and Persistence

Practice statistics and weak-position information are stored locally in
the browser using local storage.

The app should remain self-contained and should not require a
server-side database or user account unless that architecture is
intentionally changed later.

Existing saved statistics should be preserved across application updates
unless a future change explicitly requires a data migration.

## Technical Architecture

The application intentionally uses a simple architecture:

-   One `index.html` production application file
-   HTML for structure
-   CSS for styling
-   Vanilla JavaScript for application logic
-   No external framework required
-   Hosted by GitHub Pages

Prefer preserving this architecture unless a future feature genuinely
requires additional files or dependencies.

## Update Rules

When modifying the trainer:

1.  Start from the latest known-good production `index.html`.
2.  Preserve existing working features unless the requested change
    requires altering them.
3.  Make only requested changes plus technically necessary supporting
    changes.
4.  Avoid unrelated visual or behavioral redesigns.
5.  Maintain TAB-style fretboard orientation.
6.  Maintain multi-string selection.
7.  Never expose Find the Note answers before the user responds or
    chooses Reveal.
8.  Preserve saved statistics and adaptive weak-position practice.
9.  Preserve the v1.2 interface hierarchy unless a future design
    decision explicitly changes it.
10. Keep the app mobile-first.
11. When ready to publish, generate a complete replacement `index.html`
    rather than only code fragments.
12. Regression-check established behavior before treating a new build as
    production-ready.

## Known-Good Releases

-   **v1.0** --- original known-good baseline preserved before expansion
    work.
-   **v1.1** --- all strings selected by default; Natural Notes Only
    enabled by default; accidental answer buttons hidden while
    preserving their grid positions.
-   **v1.2** --- current known-good production release; collapsible
    Settings, compact settings summary, Quiz Type moved into Settings,
    and metrics repositioned immediately above the quiz.

## Potential Future Features

Ideas discussed but **not currently implemented requirements** include:

-   Timed Challenge mode
-   Response-time tracking
-   Smarter weak-position analysis using both accuracy and response
    speed
-   Session summaries
-   Practice presets
-   Mastery tracking by string and fret
-   Visual fretboard heat map
-   Progressive fret-range learning
-   Sharps-versus-flats display preferences

Feature ideas remain proposals until explicitly approved. Avoid adding
complexity simply because an idea appears in this list.

## Project Philosophy

The goal is not merely to calculate notes on the fretboard. The trainer
should help the player reach immediate recall.

Practice should favor focused repetition, gradual expansion of the
fretboard, immediate feedback, and extra exposure to weak positions.

The interface should increasingly get out of the way during practice:
configuration should be easy to reach when needed, while the quiz itself
remains the primary focus.
