# How I used Claude to build the animated walkthroughs

The animated diagrams in my FYP presentation (the life of a recording, tracing a broken Admin Panel page, why the transcript page should not just scroll, and Ask AI end to end) were made with Claude (Claude Code, in the desktop app). It was not a single prompt. It was a short starting brief, then many rounds of specific feedback. This page shows both, so you can repeat it.

**Open the walkthroughs:** download any file in [`animations/`](./animations) and open it in a browser. Press **→** or **Space** for the next step and **←** to go back.

| File | Slide | What it shows |
|---|---|---|
| `lifecycle2.html` | 5 | The life of a recording through MAGOR's real parts, and where it broke |
| `trace.html` | 13 | Tracing one broken Admin Panel page across Nginx, Backend, MongoDB and Studio |
| `scroll.html` | backup | Why the transcript page should not just scroll (a hidden backup slide) |
| `askai.html` | 54 | Ask AI end to end: Frontend → Studio → AI gateway → back |
| `lifecycle.html` | — | The first version of slide 5 (boxes), kept for comparison |

## 1. What I gave Claude first

Context matters more than the wording of the prompt. Before asking for any animation, Claude had:

- **My report and codebase.** The diagrams had to match the real code, so Claude read the code to check each step (for example, which collection a route reads from).
- **The presentation guidelines** (section 3.2.2 of Prof Chng's page): problem first, lots of figures, zoom in and out without losing context.
- **Two example HTML animations** from earlier students that Prof Chng shared.

## 2. The starting prompt

Prof Chng's suggestion, which I passed on with the files above:

> Create a html page to animate your process for presentation, with instructions of your work.

Then my own brief, listing which parts of the talk needed an animation and why:

> I basically need the slides to be animated diagrams where relevant. Some suggestions:
> 1. The Admin Panel's 4 pages can be 4 blocks. Each time I elaborate on one, it zooms in to that block and goes to a slide on the issue and fix.
> 2. An animated diagram to show download is a single file for one selected format, and a ZIP for several.
> 3. The review workflow slide is really about refining the Recordings page layout: there used to be so much metadata that it caused scrolling.
> 4. For deletion, an animated diagram of what was deleted before and what is deleted after, to show cascading deletion.
> 5. The Ask AI flowchart works, but improve and animate it if you can.
>
> Make use of figures, animations and diagrams to explain rather than boring text slides as much as possible. Insert placeholders if you need me to screenshot or record from MAGOR.

**Tip:** say *what each animation must explain*, not how to draw it. "Show what was deleted before and after" gives a better result than "draw 8 boxes and turn them red".

## 3. The feedback rounds (where most of the quality came from)

These are real examples of the corrections I gave after viewing a draft:

- **Use real shapes, not boxes.** After Prof Chng sent another example, slide 5 was redrawn: *"slide 5 is boxes instead of actual shapes to show the overall layout of MAGOR."* It now shows the browser, Studio server, MongoDB, storage and the SpeechLab services.
- **Animate the actual problem.** *"Show a transcript overflowing down and scrolling down, then when the playback auto-scrolls it snaps the page back. Do an animation to snap it back to show the issue."*
- **Keep the order natural.** *"Slide 10 didn't introduce the Admin Panel, it went straight into the diagram."* The pages are shown first, then the diagram.
- **Make it accurate.** *"It's not missing id, it's missing functions. The id was only for the example."* Every label was checked against the code.
- **No absolute claims.** *"Don't put definitives like every, put most."* Examiners can challenge "every".

## 4. Claude can make slides, but you make the presentation

Claude can generate a whole slide deck, but what it produces is usually chunks of well-organized information: correct, neat, and grouped by topic. That is not the same as a presentation. In the end I did not use the first deck Claude generated. I used Claude for the parts it is good at (diagrams, animations, checking facts, tightening wording) and planned the flow myself.

The student still has to:

- **Decide the story.** What problem does the audience need to feel first, and what order makes each fix make sense? I followed the problem first, then the fix, then the result, so every solution had a reason before it appeared.
- **Plan the flow between slides.** For example, I reordered my Ask AI section so the audience sees a summary explained, then the demo, then custom summaries, then the Q&A demo, and only then the behind-the-scenes flow. Claude organized the content; I chose the order that a listener could follow.
- **Make the transitions sound natural when spoken.** A line can read well and still sound abrupt out loud. I rewrote several opening lines so each slide connected to the one before it.
- **State the impact, not just the fix.** On my results slide, I asked for each improvement to answer "so what?", for example better storage efficiency or security and long-term maintainability, rather than a list of what was changed.
- **Keep it in your own voice.** The script should sound like you, because you are the one presenting it and answering questions on it.

A good way to work: write the outline and the order of slides yourself first, then ask Claude to build the figures and animations for each point.

## 5. How the HTML became slides

Each walkthrough is one self-contained HTML file (SVG drawing plus a small timeline engine, no internet needed). To use it in PowerPoint:

1. Each step of the HTML is recorded as its own short video clip (Playwright drives the page in a browser and ffmpeg encodes it).
2. The clips are stacked on the slide. The first plays automatically, and each click plays the next, so the animation follows my narration.
3. The step list on the right of each walkthrough doubles as the speaker's outline, so the audience always knows where they are.

Because each step's timing is fixed, a diagram can be corrected and re-recorded without changing the clip lengths, so recorded narration still lines up.

## 6. Tips for new students

1. **Plan the story yourself:** the outline and slide order are your job; Claude fills in the figures.
2. **Give context first:** report, code and the guidelines. Then ask.
3. **One animation per idea:** a problem, a trace or a before/after, not the whole system.
4. **Look at every draft and be specific:** "this label overlaps", "this step happens before that one", "use the real component name".
5. **Check facts against the code:** a beautiful diagram that is wrong is worse than none.
6. **Keep the HTML.** It is the source; the slides and videos are generated from it, so fixes stay cheap.
