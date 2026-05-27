# Nagi · 凪

A private anxiety-management companion. Single HTML file, `localStorage`-only, deployed via GitHub Pages — nothing ever leaves the device.

---

## Home screen

A serif tagline ("Impermanence. *Nothing spans all time or space.*") sits above four tiles. Each tile is a button to its section; Sleep and HAM-A tiles also surface live status pills.

| Tile | Tag | Screen |
|---|---|---|
| Sleep | 眠り | Daily sleep checklist |
| HAM-A | 焦り | Daily anxiety scoring |
| Calm | 静穏 | Calming exercises |
| Toolkit | 療法 | CBT/ACT tools |

An **Options** button below the tiles opens backup / wipe controls.

---

## HAM-A check-in

Hamilton Anxiety Rating Scale–style daily check-in. One record per calendar day; re-rating overwrites the existing record. Resets at midnight.

**14 symptoms, 3 groups:**

| Group | Symptoms |
|---|---|
| Physical | Tension, Somatic-Muscular, Cardiovascular, Autonomic, Genitourinary†, Somatic-Sensory†, Respiratory†, Gastrointestinal† |
| Behavioral | Intellectual, Insomnia, Behavior† |
| Feelings | Anxious mood, Depressed mood, Fears† |

†5 optional symptoms shown at reduced opacity; brighten once rated.

**Scoring:** 0 / 1 / 2 / 3 = None / Mild / Moderate / Severe. Max total: 42.

**Today sub-tab**
- 14-dot colored snapshot (green → amber → orange → red by score)
- Symptom cards grouped Physical / Behavioral / Feelings with colored left-accent bars
- Free-text note field (auto-saves shortly after last keystroke)
- Rating taps save immediately

**History sub-tab**
- One entry per date, newest first
- Same 14-dot grid per entry for at-a-glance comparison
- Edit mode: re-rate any symptom and update the note inline
- Delete entry with confirmation

**Settings sub-tab**
- JSON backup / restore, full data export, data wipe

**Home tile pill:** today's average score + label, count of symptoms rated, current streak.

**Storage:** `nagi.hama.v1`

---

## Sleep checklist

Daily sleep-hygiene tracker. One record per calendar day; opens at the time range matching the current clock.

**Four time ranges (15 items total):**

| Range | Window | Items |
|---|---|---|
| Morning | 6–8 am | Total sleep >7.5 h · consistent wake time · wake up well rested |
| Day | 8 am – 6 pm | Daylight exposure · no caffeine after 3 pm · no naps beyond a 20 min power nap |
| Evening | 6–10 pm | No large meals 2 h before bed · no intense exercise 1 h before bed · no screens (except ebooks) 30 min before bed |
| Night | 10 pm – 6 am | No activities in bed · dark, cool bedroom · ritual† · calming technique† · consistent sleep time · early sleep time |

†Two "nice-to-have" Night items; every other item defaults unchecked.

**Checklist sub-tab**
- Stepper UI — ‹ › arrows + 4-dot indicator walk the loop; current-time dot has a distinct ring
- Each item is a toggle — unchecking means "didn't manage this"
- Night shows a non-interactive Tips block (anxious-thoughts and 30-minute-rule advice)
- Every tap saves immediately

**History sub-tab**
- One entry per day, newest first, with a 15-dot kept / not-kept summary
- Edit mode re-toggles any item grouped by range; delete with confirmation

**Home tile pills:** current range's accomplished count + a logged-days streak.

**Storage:** `nagi.sleep.v1`

---

## Calm

Four exercises accessible from a landing card grid. A History sub-tab on the Calm screen lists saved narrations.

### Deep Breathing · 呼吸

Two patterns: **4-7-8** (inhale 4 s / hold 7 s / exhale 8 s) and **Box** (inhale 4 s / hold 4 s / exhale 4 s / hold 4 s). Animated SVG ring arcs through each phase; color shifts between inhale and exhale. Goal picker: finish by cycle count or elapsed minutes.

### Grounding · 実感

Three sub-modes selectable from a picker:

- **Senses** — 5-4-3-2-1: guided through 5 things you see → 4 hear → 3 touch → 2 smell → 1 taste. Tap button counts off items; dot-progress strip tracks senses.
- **Narration** — Open textarea; describe the current moment in third person, as if narrating a novel. Saved locally by date.
- **Imagery** — Beach script reader: 5-paragraph guided visualization. Dot-progress strip shows current and completed paragraphs; Back / Next / Done navigation.

Narrations are stored in `nagi.calm.v1` and viewable in the Calm History tab.

### Emotions at Tea · 感情

Name an emotion; a tea-cup visualization renders steam animations above the cup. The app offers a short reflection passage framed around sitting with that feeling rather than escaping it. Close when done — no data saved.

### PMR · 弛緩

Progressive muscle relaxation. 13 muscle groups (Hands → Forearms → Biceps → Shoulders → Forehead → Mouth → Neck → Chest → Stomach → Buttocks → Calves → Thighs → Feet). Animated ring tracks tense (3 s, amber arc) then release (10 s, green arc) phases; phase label and countdown shown inside the circle.

Settings panel: toggle visibility per group; reorder shown groups with up/down arrows.

---

## Toolkit

Seven CBT/ACT tools on a flat landing grid. Each card shows a Japanese tag, a first-person cue, and a concrete example — no triage wizard, you pick the tool that fits.

| Tool | Tag | When |
|---|---|---|
| Intrusion Check | 閃念 | A flash of negative thought intruded; want to step out of it |
| Rumination Break | 反芻 | Stuck in a thought spiral; want to interrupt the loop |
| Situation Processing | 事態 | Something happened that triggered you; want to process it |
| Anticipation Planning | 予想 | Worrying about something coming up; want a plan |
| Values Alignment | 価値 | A wedge between values and surroundings; want to realign |
| Injustice Navigation | 公正 | Struck by an injustice event; want to navigate it |
| Exposure Rewire | 構築 | Avoiding something scary; want to face it slowly |

A History sub-tab lists saved records grouped by type, with inline edit and delete.

### Intrusion Check (閃念) · 4 steps

1. **Context** — how were you feeling before the thought appeared?
2. **Intrusion** — what flashed through your mind? Is anything actually supporting the fear right now?
3. **Gentle reminder** — static reframe ("an old protective alarm, not your true belief").
4. **Return** — pick a redirect action (stretch, water, wash face, step outside, calming exercise).

Stored in `nagi.toolkit.thought.v1` with `branch: "intrusion_check"`.

### Rumination Break (反芻) · 4 steps

1. **Name it** — what's looping?
2. **Symptoms** — pick from chip list (replaying loops, mental rehearsal, searching for closure, stalking online…) plus a free-text "other" and a "is new information emerging?" yes/no.
3. **Acknowledge** — defusion message ("this is your mind doing what minds do").
4. **Break the loop** — pick a redirect action.

Stored in `nagi.toolkit.thought.v1` with `branch: "rumination"`.

### Situation Processing (事態) · up to 8 steps

For something that already happened.

1. Situation — what happened.
2. Immediate reaction — plus an optional "what is your reaction protecting you from?" sub-field.
3. The thought — the belief driving the distress. If the belief is about yourself, an optional "what would you say to a friend?" prompt appears.
4. CBT check — evidence for and against, with a side-drawer of cognitive distortion patterns (Reframing Cheatsheet) to collect reframe notes.
5. Belief-check triage — done here, or "even if my belief were true…" continues.
6. ACT check — what do you want to do, regardless?
7. Severity triage — one-time situation vs. ongoing/serious.
8. **Onetime branch:** one concrete action today. **Serious branch:** real-world levers (reduce exposure, document, support network, exit plan, seek support).

Stored in `nagi.toolkit.situation.v1` with `branch: "past"`.

### Anticipation Planning (予想) · 6 steps

For something coming up.

1. Situation — what's coming up.
2. Immediate reaction — plus optional "what is this protecting you from?"
3. The dread — specific feared outcome.
4. Reality check — is it actually likely?
5. ACT check / coping plan — if it happens, how will you handle it?
6. Prep step — one concrete thing to do before it happens.

Stored in `nagi.toolkit.situation.v1` with `branch: "future"`.

### Values Alignment (価値) · 4 steps

1. Domain — Work / Health / Friendship / Family, or custom.
2. Identity — what kind of person you want to be in this area, and what that looks like day-to-day.
3. Alignment — closeness slider (1–5: far off → aligned), framed as information, not a verdict.
4. Action — pick "a small step can move it" (writes one concrete step) or "it feels bigger than that" (writes a sit-with-it reflection).

Stored in `nagi.toolkit.values.v1` with `branch: "alignment"`.

### Injustice Navigation (公正) · 5 steps

1. Situation — what's the injustice event?
2. Identity — what kind of person do you want to be in an unfair world?
3. Meaning — what strengths did surviving this develop?
4. Agency — what's in vs. out of your control right now?
5. Action — given unfairness exists, what would wise self-care look like today?

Stored in `nagi.toolkit.values.v1` with `branch: "injustice"`.

### Exposure Rewire (構築)

ACT-based exposure tool. Goal is **willingness** — doing the hard thing because it connects to values — not anxiety reduction.

*Wizard steps:* theme → situation → fear prediction → values link → ready → outcome → survived.

- **Theme** — pick an existing chip or name a new one. Existing themes surface a "variety nudge" listing situations already faced, nudging toward something different.
- **Values link** — mandatory; shows a warning if the answer reads like anxiety-reduction rather than something you genuinely care about.
- **Ready** — recap card (situation / prediction / values). Two exits: *I've done it* (→ outcome) or *Save & come back later* (writes a pending record).
- **Survived** — Yes / Yes but it was hard. No "No" option by design.

Pending exposures surface at the top of their theme with a *Resume* link. Once complete, exposures are permanent — the survival record is the therapeutic mechanism.

**History ("Your survival record")** — collapsible theme cards showing prediction-vs-outcome side by side. Once a theme has ≥3 completed exposures, a surfacing line appears recapping the pattern.

**Storage:** `nagi.toolkit.exposure.v1`

---

## Storage

All data is on-device in `localStorage`. The backup nudge prompts periodically; dismissing snoozes it. JSON export / import and a full data wipe are available under Options.

| Key | Contents |
|---|---|
| `nagi.meta.v1` | App metadata (nudge timing, PMR settings) |
| `nagi.hama.v1` | HAM-A daily history |
| `nagi.sleep.v1` | Sleep checklist history |
| `nagi.calm.v1` | Grounding narrations |
| `nagi.toolkit.thought.v1` | Intrusion checks + rumination breaks |
| `nagi.toolkit.situation.v1` | Situation processing + anticipation planning records |
| `nagi.toolkit.values.v1` | Values alignment + injustice navigation records |
| `nagi.toolkit.exposure.v1` | Exposure rewire records |

---

## Tech

- **Single file:** `index.html` (~5 450 lines, no framework, no build step)
- **Typography:** Fraunces variable serif · JetBrains Mono · Shippori Mincho
- **Palette:** blue-grey base (`#E6ECF1`) with sky / slate / sage / amber / rose accents
- **PWA:** `apple-mobile-web-app-capable`, viewport-fit cover, safe-area insets — installable on iOS via Add to Home Screen
