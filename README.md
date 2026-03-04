![Kotlin](https://img.shields.io/badge/Kotlin-1.9-blue?style=flat-square)
![Compose](https://img.shields.io/badge/Jetpack%20Compose-UI-green?style=flat-square)
![Min SDK](https://img.shields.io/badge/Min%20SDK-26-orange?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)
![Platform](https://img.shields.io/badge/Platform-Android-lightgrey?style=flat-square)

# Dot

A minimal month-focused calendar for marking days.  
Nothing more.

---

## ✦ Philosophy

Most calendar apps ask you to plan, schedule, and optimize.

Dot asks nothing.

It gives you a month.  
You mark the days that matter.  
That's it.

No streaks. No scores. No reminders. No analytics.  
Just a quiet record of what happened.

The design is inspired by the restraint of Braun instruments and the precision of Apple interfaces.  
Every element earns its presence.

---

## 📱 What It Does

- Opens directly to the current month
- Tap any day to mark it
- Tap again to unmark it
- Swipe left or right to move between months
- Follows system Light / Dark mode automatically
- Includes a home screen widget with the same interaction model

That is the entire feature set.

---

## 🎨 Design System

Dot uses a fixed, hand-tuned color palette. No dynamic color. No theme selector.

| Token | Light | Dark |
|---|---|---|
| Background | `#F2F2F3` | `#1C1C1E` |
| Primary Text | `#2C2C2E` | `#E5E5E7` |
| Secondary Text | `#8E8E93` | `#8E8E93` |
| Filled Dot | `#6F8F88` | `#5A7872` |
| Empty Stroke | `#D1D1D6` | `#3A3A3C` |

No gradients. No shadows. No ripple effects.  
Dot state toggles with a 90ms alpha animation — fast enough to feel mechanical, slow enough to feel intentional.

Today is indicated by a thin 1dp ring around the date number.

---

## 🧠 How It Works

**Marking a day**

Tap any cell. The empty stroke fades out. The filled dot fades in. State is persisted immediately to DataStore.

**Unmarking a day**

Tap again. The filled dot fades out. The empty stroke returns.

**Navigation**

Tap the arrow chevrons or swipe horizontally to change months.  
The calendar animates with a subtle directional slide.

**Widget**

Add Dot to your home screen. Tap any day in the widget to toggle it.  
Widget and app share the same DataStore — changes appear immediately in both.

---

## 🏗 Architecture

```
MainActivity
└── DotApp()
    └── MonthView()
        └── DayCell()

DotViewModel
└── DataStoreManager (singleton)

DotWidget (Glance)
└── DotWidgetReceiver
└── ToggleDateAction
```

- Single-activity architecture
- ViewModel holds `YearMonth` navigation state and `Set<LocalDate>` marked dates
- DataStore persists marked dates as `Set<String>` of ISO-8601 date strings
- Widget reads from the same DataStore via `collectAsState` inside `provideContent`
- No Room. No network. No permissions.

---

## 🛠 Built With

- Kotlin 1.9
- Jetpack Compose (BOM 2024.05)
- Material 3
- DataStore Preferences
- Glance App Widget 1.1.0
- MVVM
- StateFlow
- Min SDK 26 / Target SDK 34

---

## 🚀 Installation

**From source**

```bash
git clone https://github.com/waleedahmedja/Dot.git
```

Open in Android Studio Hedgehog or later.  
Let Gradle sync. Run on any device with API 26+.

**From Releases**

[https://github.com/waleedahmedja/Dot/releases](https://github.com/waleedahmedja/Dot/releases)

---

## 📁 Project Structure

```
app/
└── src/main/
    ├── java/com/waleedahmedja/dot/
    │   ├── MainActivity.kt
    │   ├── DotApplication.kt
    │   ├── data/
    │   │   └── DataStoreManager.kt
    │   ├── ui/
    │   │   ├── DotApp.kt
    │   │   ├── DotViewModel.kt
    │   │   ├── components/
    │   │   │   ├── MonthView.kt
    │   │   │   └── DayCell.kt
    │   │   └── theme/
    │   │       └── DotTheme.kt
    │   └── widget/
    │       ├── DotWidget.kt
    │       └── DotWidgetReceiver.kt
    └── res/
        ├── values/themes.xml
        ├── values-night/themes.xml
        └── xml/dot_widget_info.xml
```

---

## 📄 License

MIT License. See [LICENSE](LICENSE.md) for details.

---

## 🧭 Roadmap

- Lock screen widget support
- Monochrome adaptive icon
- Optional month note (single line, no formatting)
- Export marked dates as plain text

---

> Dot is calm.  
> Dot is precise.  
> Dot remembers what you marked.

— waleedahmedja
