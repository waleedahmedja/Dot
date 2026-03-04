# Contributing to Dot

Thank you for your interest in contributing.

Before opening a pull request, please understand what Dot is — and more importantly, what it is not.

---

## ✦ What Dot Is

Dot is a binary day-marking calendar.  
One month. Mark a day. Unmark it. Navigate months.  
That is the entire scope.

It is not a habit tracker.  
It is not a journal.  
It is not a productivity system.

Every design decision in Dot exists to reduce surface area, not expand it.

---

## 🧠 Core Principles

Before contributing, internalize these:

**Minimal over featured.**  
If a new feature makes Dot do more things, it should be questioned. If it makes Dot do the same things better, it belongs.

**Intentional over clever.**  
Code that is easy to read is more valuable than code that is clever. Architecture should be obvious.

**Quiet over expressive.**  
The UI should not call attention to itself. Animations should be functional. Colors should be neutral. Nothing should feel decorative.

**No gamification. Ever.**  
No streaks. No marks counts. No "best month" indicators. No rewards. These are architectural constraints, not preferences.

---

## 🏗 Architecture Rules

- Follow the existing MVVM structure
- UI state lives in `DotViewModel` via `StateFlow`
- Persistence is handled exclusively through `DataStoreManager`
- Do not introduce Room, network calls, or third-party analytics
- Do not add new `@Composable` screens without justification
- Keep `DataStoreManager` as the single source of truth — both app and widget read from it
- Widget must remain in sync with the app; test toggling from both surfaces

---

## 🎨 UI / UX Guidelines

- Preserve the existing color system — do not add new colors
- Do not add shadows, gradients, or decorative shapes
- Animations must be 80–180ms max — nothing slow, nothing bouncy
- Typography scale is fixed — do not introduce new font sizes without replacing existing ones
- Respect system Light/Dark mode — do not add manual theme switching
- Every new UI element must earn its presence by removing visual noise, not adding it

---

## 🚀 How to Contribute

1. Fork the repository
2. Create a branch with a descriptive name:
   ```
   fix/widget-state-sync
   feature/month-note
   refactor/day-cell-layout
   ```
3. Make focused, atomic commits
4. Open a Pull Request with:
   - A clear one-line description of what changed and why
   - Screenshots or screen recordings for any UI changes
   - Confirmation that widget and app remain in sync

---

## 🧪 Before Submitting

Verify the following manually:

- Marked dates persist across app restarts
- Widget reflects app state after toggling from the app
- App reflects widget state after toggling from the widget
- Today's ring renders correctly
- Month navigation (swipe and chevron) works cleanly
- Light mode and Dark mode both render correctly
- No visible layout issues on a small screen (360dp width)

---

## What Will Not Be Merged

- Streak counters or any cumulative date statistics
- Notification or reminder systems
- Cloud sync or account features
- Custom theme selectors
- Any UI element that adds visual weight without adding clarity
- Dependency additions that can be avoided

---

Dot is a quiet app.  
Contributions should keep it that way.
