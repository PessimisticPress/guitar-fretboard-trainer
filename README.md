# Guitar Fretboard Trainer

## Project Purpose

Guitar Fretboard Trainer is a small, mobile-first web app for learning
and memorizing note locations on a standard six-string guitar fretboard.

The primary use case is quick practice on an iPhone. The trainer is
hosted with GitHub Pages and can be added to the iPhone Home Screen so
it behaves like a lightweight app.

## Current Live App

GitHub repository: `PessimisticPress/guitar-fretboard-trainer`

GitHub Pages site:
`https://pessimisticpress.github.io/guitar-fretboard-trainer/`

The published application is the repository's `index.html` file.

## Development Workflow

1.  Discuss a proposed feature or change in the Guitar Fretboard Trainer
    ChatGPT Project.
2.  Modify the current `index.html`, rather than rebuilding the
    application from memory.
3.  Test the updated file when practical.
4.  Replace the repository's existing `index.html` with the new version.
5.  Commit the change to the `main` branch.
6.  GitHub Pages automatically republishes the site.
7.  Verify the live version on the iPhone.

GitHub is the authoritative source for the currently published
application.

## Current Features

### Name the Note

The trainer displays a specific string and fret position and asks the
player to identify the note.

### Find the Note

The trainer gives a target note and string and asks the player to
identify the correct fret.

The correct fretboard position must NOT be marked before the user
answers. The fretboard should remain neutral until an answer is
submitted or the user chooses Reveal.

### Practice Controls

The user can select any combination of the six strings, choose a fret
range, restrict practice to natural notes, and enable adaptive
repetition of missed positions.

### Metrics

The trainer tracks accuracy, current streak, questions answered, and
weak spots.

The existing Reset Stats control resets saved performance data. Do not
add a second redundant metrics-reset control.

## Fretboard Display Rules

The fretboard follows guitar tablature orientation:

-   High E is the TOP string.
-   Low E is the BOTTOM string.

This orientation is important and should not be reversed in future
versions.

In Find the Note mode, never visually reveal the correct location before
the user answers.

## Mobile Design

The primary display target is an iPhone. Prioritize large tap targets,
legible text, no unnecessary horizontal scrolling, a clear fretboard,
efficient vertical space, and Safari/Home Screen compatibility.

Desktop compatibility is useful but secondary.

## Data and Persistence

Practice statistics and weak-position information are stored locally in
the browser using local storage.

The app should remain self-contained and should not require a
server-side database or user account unless that architecture is
intentionally changed later.

## Technical Architecture

-   One `index.html` file
-   HTML for structure
-   CSS for styling
-   Vanilla JavaScript for application logic
-   No external framework required
-   Hosted by GitHub Pages

Prefer preserving this simple architecture unless a future feature
genuinely requires additional files or dependencies.

## Update Rules

1.  Start from the latest current `index.html`.
2.  Preserve existing working features unless a requested change
    requires altering them.
3.  Avoid unrelated visual or behavioral changes.
4.  Maintain TAB-style fretboard orientation.
5.  Maintain multi-string selection.
6.  Do not expose answers before the user responds.
7.  Keep the app mobile-first.
8.  When ready to publish, generate a complete replacement `index.html`
    rather than only partial code snippets.

## Potential Future Features

-   Mastery tracking by string and fret
-   Visual fretboard heat map
-   Timed drills
-   Progressive fret-range learning
-   Sharps-versus-flats display preferences
-   Additional quiz modes
-   Session statistics and historical progress
-   Scale-note training
-   Chord-tone location exercises

These are ideas, not current requirements. They should not be added
automatically without deciding how they fit the learning experience.

## Project Philosophy

The goal is not merely to calculate notes on the fretboard. The trainer
should help the player reach immediate recall.

Practice should favor focused repetition, gradual expansion of the
fretboard, immediate feedback, and extra exposure to weak positions.
