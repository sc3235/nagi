# Nagi · 凪

A private anxiety-management companion. Single HTML file, `localStorage`-only, deployed via GitHub Pages — nothing ever leaves the device.

---

## Home screen

Four tiles navigate to the main sections. Each tile shows live status (today's score, streak, current range).

| Tile | Tag | Screen |
|---|---|---|
| Sleep | 眠り | Daily sleep-hygiene checklist |
| HAM-A | 焦り | Daily anxiety scoring |
| Calm | 静穏 | Calming exercises |
| Toolkit | 療法 | CBT/ACT tools |

An **Options** button at the bottom of the home screen opens backup / wipe controls.

---

## HAM-A check-in

Hamilton Anxiety Rating Scale–style daily check-in. One record per calendar day; re-rating overwrites the existing record. Resets at midnight.

**14 symptoms, 3 groups:**

| Group | Symptoms |
|---|---|
| Physical | Tension, Somatic-Muscular, Cardiovascular, Autonomic, Genitourinary†, Somatic-Sensory†, Respiratory†, Gastrointestinal† |
| Behavioral | Intellectual, Insomnia, Behavior† |
| Feelings | Anxious mood, Depressed mood, Fears† |

†5 optional symptoms shown at 42% opacity; brighten to 80% once rated.

**Scoring:** 0 / 1 / 2 / 3 = None / Mild / Moderate / Severe. Max total: 42.

**Today sub-tab**
- 14-dot colored snapshot (green → amber → orange → red by score)
- Symptom cards grouped Physical / Behavioral / Feelings with colored left-accent bars
- Free-text note field (auto-saves 600 ms after last keystroke)
- Rating taps save immediately

**History sub-tab**
- One entry per date, newest first
- Same 14-dot grid per entry for at-a-glance comparison
- Edit mode: re-rate any symptom and update the note inline
- Delete entry with confirmation

**Settings sub-tab**
- JSON backup / restore, full data export, data wipe

**Storage:** `nagi.hama.v1`

---

## Sleep checklist

Daily sleep-hygiene tracker. One record per calendar day; opens at the time range matching the current clock.

**Four time ranges:**

| Range | Window | Items |
|---|---|---|
| Morning | 6–8 am | 8 hours of sleep, consistent wake time |
| Day | 8 am – 6 pm | Daylight, caffeine limit, nap limit |
| Evening | 6–10 pm | No large meals, no intense exercise, no screens |
| Night | 10 pm – 6 am | No activities in bed, good environment, ritual†, calming technique†, consistent early sleep |

†Two "nice-to-have" Night items default unchecked; every other item defaults checked.

**Checklist sub-tab**
- Stepper UI — ‹ › arrows + 4-dot indicator walk the loop; current-time dot has a distinct ring
- Each item is a toggle — unchecking means "didn't manage this"
- Night shows a non-interactive Tips block (anxious-thoughts and 30-minute-rule advice)
- Every tap saves immediately

**History sub-tab**
- One entry per day, newest first, with a 13-dot kept / not-kept summary
- Edit mode re-toggles any item grouped by range; delete with confirmation

**Home tile** shows current range's kept count + a logged-days streak.

**Storage:** `nagi.sleep.v1`

---

## Calm

Four exercises accessible from a landing card grid.

### Deep Breathing · 呼吸

Two patterns: **4-7-8** (inhale 4s / hold 7s / exhale 8s) and **Box** (inhale 4s / hold 4s / exhale 4s / hold 4s). Animated SVG ring arcs through each phase; color shifts between inhale (blue) and exhale (green). Goal picker: finish by cycle count (1–30) or elapsed time (minutes).

### Grounding · 実感

Three sub-modes selectable from a picker:

- **Senses** — 5-4-3-2-1: guided through 5 things seen → 4 heard → 3 felt → 2 smelled → 1 tasted. Tap button counts off items; dot-progress strip tracks senses.
- **Narration** — Open textarea; describe the current moment in third person, as if narrating a novel. Saved locally by date.
- **Imagery** — Beach script reader: 4-paragraph guided visualization. Dot-progress strip shows current and completed paragraphs; Prev / Next / Done navigation.

Narrations are stored in `nagi.calm.v1` and viewable in the Calm History tab.

### Emotions at Tea · 感情

Name an emotion; a tea-cup visualization renders steam animations above the cup. The app offers a short reflection passage framed around sitting with that feeling rather than escaping it. Close when done — no data saved.

### PMR · 弛緩

Progressive muscle relaxation. 13 muscle groups (Hands → Forearms → Biceps → Shoulders → Forehead → Mouth → Neck → Chest → Stomach → Buttocks → Calves → Thighs → Feet). Animated ring tracks tense (3 s, amber arc) then release (10 s, green arc) phases; phase label and countdown shown inside the circle.

Settings panel: toggle visibility per group; reorder shown groups with up/down arrows.

---

## Toolkit

Four CBT/ACT tools, each with a Japanese tag, a one-line cue, and a concrete example. No triage wizard — pick the tool that fits.

| Tool | Tag | When |
|---|---|---|
| Thought Check | 長考 | Spiraling on a negative thought; need to interrupt the loop or examine whether it's true |
| Situation Debrief | 事態 | Something just happened (or is coming up); want to process it and figure out what to do |
| Values Compass | 価値 | A wedge between how I'm living and what I value; want to articulate it |
| Exposure Rewire | 構築 | Avoiding something because it's scary; want to face it in my own time |

### Thought Check (長考)

Branch picker on entry: **Belief check** or **Rumination break**.

*Belief check (6 steps)*
1. Facts — what happened, objectively
2. Thoughts — the specific belief causing distress; optional "is this about yourself?" prompt unlocks a "what would you say to a friend?" step
3. Emotion + intensity (1–10 slider)
4. Evidence for the thought
5. Evidence against — plus a side-drawer of cognitive distortion patterns (Reframing Cheatsheet) for reference
6. Reinterpret — a more accurate reading; emotion re-rated (1–10)

Optional save. Stored in `nagi.toolkit.thought.v1` with `branch: "belief"`.

*Rumination break (4 steps)*
1. Name it — describe what's looping
2. Body check — where do you feel it physically?
3. Defusion prompt — static text anchoring the thought as mental noise
4. Redirect — shortcut to the Calm section, or four physical action options

Optional save. Stored in `nagi.toolkit.thought.v1` with `branch: "rumination"`.

### Situation Debrief (事態)

Branch picker on entry: **Past · process** or **Future · plan**.

*Past branch (7 steps)* — situation, immediate reaction, core thought, CBT check (is it accurate?), ACT check (what do you want to do regardless?), response severity triage, one concrete action.

*Future branch (6 steps)* — situation, what you're dreading, reality check (how likely / how bad?), ACT check, coping plan, one prep step.

Reframing Cheatsheet available in both branches. Optional save. Stored in `nagi.toolkit.situation.v1`.

### Values Compass (価値)

1. Pick a domain — Work / Relationships / Health / Creative life / Other
2. What kind of person do you want to be in this area?
3. Is there a wedge between that and how you're living now? (free text)
4. What's one thing you could do this week?

Optional save. Stored in `nagi.toolkit.values.v1`.

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

### Toolkit History

The History sub-tab in the Toolkit screen shows all saved records (thought checks, rumination breaks, situation debriefs, values compass entries) grouped by type, with edit and delete.

---

## Storage

All data is on-device in `localStorage`. The backup nudge prompts periodically; dismissing snoozes it. JSON export / import and a full data wipe are available under Options.

| Key | Contents |
|---|---|
| `nagi.meta.v1` | App metadata (nudge timing) |
| `nagi.hama.v1` | HAM-A daily history |
| `nagi.sleep.v1` | Sleep checklist history |
| `nagi.calm.v1` | Grounding narrations |
| `nagi.toolkit.thought.v1` | Thought check + rumination records |
| `nagi.toolkit.situation.v1` | Situation debrief records |
| `nagi.toolkit.values.v1` | Values compass records |
| `nagi.toolkit.exposure.v1` | Exposure rewire records |

---

## Tech

- **Single file:** `index.html` (~5 400 lines, no framework, no build step)
- **Typography:** Fraunces variable serif · JetBrains Mono · Shippori Mincho
- **Palette:** blue-grey base (`#E6ECF1`) with sky / slate / sage / amber / rose accents
- **PWA:** `apple-mobile-web-app-capable`, viewport-fit cover, safe-area insets — installable on iOS via Add to Home Screen
