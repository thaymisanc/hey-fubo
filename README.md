# Hey Fubo — Ask Fubo prototype

A clickable, browser-based prototype of an "Ask Fubo" voice + text search experience for the Fubo TV app. Built for UX research.

**Live demo:** https://thaymisanc.github.io/hey-fubo/

Best viewed full-screen on desktop (designed for 16:9 TV-style layouts). Works in Chrome, Edge, and Brave. Safari and Firefox work for everything except the real-microphone voice flow.

---

## Research questions this prototype is designed to surface

1. **Do users find the entry point?** — Specifically the "Ask Fubo" chip with the animated gradient border, placed at the top-left of the Sports page next to the category chips ("All", "Soccer", "Football", etc.).
2. **Do they realize they can only ask about their favorite teams/leagues?** — Internally, that's the vidAI content scope. Externally, the prompt copy says "Ask about your favorite teams' highlights."
3. **How do they expect to use this feature?** — Talking into the mic, typing on the on-screen keyboard, tapping a pre-built suggestion chip, or something else?
4. **Would they use the suggested questions?** — Four chips appear below the keyboard ("All Ohtani at-bats last night", "Patriots touchdowns from yesterday's game", "Knicks scores from last week", "Brazil goals from World Cup"). Are these expected? Useful? Limiting?
5. **What sort of results do they expect to get?** — The prototype shows two result patterns: rich photo/video clip grids for known sports (when a suggestion chip is tapped) and generic stacked clip placeholders for free-form typed or spoken queries. Do these match user expectations?
6. **Would they use this feature? Do they find it valuable?** — Overall reaction, perceived value, willingness to try it again.

---

## What's interactive in the prototype

- The **"Ask Fubo" chip** is the only entry point. Click or tap it to start.
- The **on-screen alphabet keyboard** is fully functional. Typing letters builds the search query character-by-character. Pressing Enter on a physical keyboard submits.
- **Real microphone** works if the participant is in Chrome / Edge / Brave on the hosted https URL. Holding the "Hold to dictate" button starts a live Web Speech API session and transcribes their voice into the query bar. Releasing the button submits. (If permission is denied, the unsupported browser, or local `file://`, it silently falls back to a scripted demo phrase.)
- **All four suggestion chips** are tappable and route to dedicated topic-specific result screens (Ohtani, Patriots, Knicks, Brazil).
- **Typed queries via keyboard always route to the generic mixed-results screen** (the stacked placeholder cards). 
- The first card on each result screen has a small white focus outline (TV remote pattern).
- The results screen has thumbs-up / thumbs-down feedback affordances that respond on click.
- The Close button (top-right) on the results/thinking screens returns to the home page.

## What's static / not interactive

- The home page category chips ("All", "Soccer", "Football", etc.) are decorative only — they don't filter content.
- The left-side navigation icons (Search, Home, Guide, Recordings, Sports, On now, Movies) are visual only.
- Cards on the home page rails do not deep-link — clicking any of them sends the user to the search screen as a shortcut.
- The results screens are pre-baked and don't reflect real-time data.

---

## Flow / states overview

```
Sports home page
    │  user clicks "Ask Fubo" chip
    ▼
Search screen  (keyboard, mic, 4 suggestion chips)
    │
    ├── tap suggestion chip ────► Topic-specific results (real photos/videos)
    │                              • Ohtani, Patriots, Knicks, Brazil
    │
    ├── type + Enter ───────────► Generic results (stacked placeholders)
    │
    └── hold mic to dictate ────► Generic results (stacked placeholders)
                                   • Real voice on https Chrome/Edge/Brave
                                   • Otherwise scripted demo phrase
                                   ▼
                       Thinking state (~2.4s with shimmer dots)
                                   ▼
                              Results state
                                   │
                                   └── Close button returns to home
```

---
