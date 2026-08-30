# Orbit Explorer

An interactive visualization tool for exploring parameterized sequence rules through graph-based pattern hunting.

## Versions

### Version 2.2 (Latest) ✨

**[Launch Orbit Explorer](https://ohiomathteacher.github.io/orbit-explorer/)**

The version you are running is stamped faintly in the bottom-right corner of the
canvas — `v2.2 · <build>`. If a change seems missing, check that stamp first: it is
the quickest way to tell whether you are on the build you think you are.

**New in v2.2 (August 29, 2026) — session recording:**

- **Every action is recorded, in order and timestamped** from the first thing the
  student does. Parameter changes, each seed with the outcome it produced, max steps,
  layout mode, prime colouring, step numbers, Reset Layout, node drags, and both sides
  of the AI conversation with its timing.
- **Download Session** — in the Cases panel, beside Download Cases. Writes the whole
  sitting as one JSON file. Offered even with no conversation, because exploring
  without asking anything is still a session.
  - `events` — the full record, in order.
  - `turns` — the conversation projected into [verbatim-app](https://github.com/OhioMathTeacher/verbatim-app)'s
    shape, so it reads with the same tooling. Speaker is a fact about where the text
    came from, not an inference from how it looks.
  - `saved_cases`, the layout seed, the app version and build.
- **What this makes possible that neither tool could do alone:** verbatim records the
  conversation but never sees the applet; Cases records the applet but not a word of
  the talk. One session file ties *what the student did* to *what they said about it*,
  on the same clock.
- **Seeded layout.** Node positions come from a seeded PRNG rather than `Math.random()`,
  and the seed travels in the session file — so a recorded session can be redrawn node
  for node, not merely re-derived.
- **`OrbitRecorder` on `window`** for checking a recording from the browser console.

**Fixed in v2.2:**

- Grid highlights follow the trajectory currently drawn instead of accumulating every
  seed explored. Exploring 1111 and then clicking another number used to leave 1111's
  whole chain lit beside the new one.
- The graph re-centres while the force layout settles, so showing or hiding the Data
  Reference Grids no longer parks it against an edge.
- The AI panel handle is a 36px grip with a hover state, not a 16px strip carrying a
  13px chevron that nobody found.

**New in v2 (March 22, 2026):**

- **Visible Steps Control** - Clean stepper widget to control sequence display length (1-9999, default: 50)
  - Large, easy-to-click arrows (▲/▼) positioned in top-left canvas area
  - Visual feedback: arrows highlight yellow when clicked
  - Audio feedback: satisfying click sound on each press
  - Type directly in the circle to jump to any value
  - Starts at 50 steps for pedagogical discovery—students increase it to explore cycle behavior
  - Extend cycles to see infinite repetition (e.g., 1↔2↔1↔2... for 100+ steps)
  - Hover tooltip explains purpose without cluttering canvas
- **Show Cycles Layout** - Toggle to arrange cycle nodes in separate circular groups
  - Clearer visualization of cycle structure vs path-to-cycle nodes
  - Multiple cycles stack vertically when present
  - Easier analysis of cycle overlap/independence
- **Curved Cycle Arrows** - Multiple curved yellow arrows show bidirectional cycle edges
  - 3 arrow pairs with fading effect emphasize infinite looping
  - Makes it visually obvious sequences loop forever, not stop at a value
- **Timestamped Downloads** - Hour-minute-second timestamps on CSV/TXT filenames
  - Better tracking for research data collection
  - Example: `orbit-explorer-cases-2026-03-22-20-43-00.csv`

All features from v1 remain available.

### Version 1 (Stable)

_No `v1` branch or tag exists in this repository — both links here previously pointed at one and were dead. v1 survives only as history on `main`; browse [the commit log](https://github.com/OhioMathTeacher/orbit-explorer/commits/main) to reach it._

**Features in v1:**

- Interactive graph visualization with force-directed layout
- Adjustable parameters for m, b, and d
- Click numbers in canvas to add them to exploration
- Draggable nodes that pin in place
- Purple breathing animation for deliberately-tested start nodes
- Yellow glow for detected cycle nodes
- Cases panel with Recent Results (auto-fills) and Saved Cases (manual save)
- Download Cases button (exports CSV with metadata)
- Download Chat button (saves AI conversation as TXT)
- Reset button (clears visual graph, preserves data for research)
- Reset Layout button (releases pinned nodes)
- Grid on/off toggle
- Light theme toggle
- Language support: English, Spanish, Simplified Chinese
- ZhengGPT AI thinking partner (OpenRouter or DeepSeek)
- Reference grids with movable viewing windows
- Outcome detection: converges to 1, enters cycle, or diverges

### Version 0.5 (Beta Archive)

**[Launch Version 0.5](https://ohiomathteacher.github.io/orbit-explorer/index-experimental.html)**

Early beta version used for initial testing. See v1 or v2 for current features.

## The Rule

The explorer visualizes sequences generated by:

- **f(n) = n/d** when n is even
- **f(n) = mn + b** when n is odd

Where m, b, and d are adjustable parameters.

## How to Use

1. Adjust the parameters using the sliders.
2. Enter a starting value and click Add.
3. Watch the graph build the sequence visually.
4. Open Cases to compare Recent Results and Saved Cases.
5. Use ZhengGPT if you want a thinking partner while exploring patterns.

## For Educators

This tool is designed for mathematical inquiry. Students can:

- Discover patterns in sequence behavior
- Form and test conjectures
- Compare different parameter sets
- Develop critical thinking about computational exploration

## Technical Details

- Built with React via CDN
- Pure client-side JavaScript with no server required
- Canvas-based force-directed graph rendering
- AI chat uses OpenRouter

## Privacy & Security

- Your API key, if entered, is stored only in your browser localStorage
- No data is sent anywhere except to OpenRouter when you use the chat feature
- The applet runs entirely in your browser

## Credits

Developed by the Technology Educator Alliance for research on critical AI literacy and mathematical inquiry.

## License

MIT License - Free to use for educational purposes
