---
name: neuron-explorer
description: "Explain neurons (nerve cells) as a single-file interactive Arabic/English HTML lesson: labeled clickable neuron anatomy (dendrites, soma, nucleus, axon, myelin, nodes of Ranvier, axon terminals, synapse), an animated action-potential simulator with a stimulus slider and threshold, a synapse/neurotransmitter animation, neuron types, and a 5-question quiz. Use when the user asks to explain, teach, visualize or quiz on neurons, nerve impulses, synapses or the nervous system."
---

# Neuron Explorer — مستكشف الخلية العصبية

Turn any request about neurons into **one self-contained interactive HTML page** the learner can open, click and play with — not a wall of text.

## When to use
- "اشرح الخلية العصبية"، "كيف تنتقل السيالة العصبية؟"، "ما هو التشابك العصبي؟"
- "Explain neurons / action potential / synapse", "make an interactive neuron lesson", "quiz my class on neurons".

## Inputs to infer (ask only if truly unclear)
| Input | Default |
|---|---|
| Language | The user's language; Arabic → `dir="rtl"`, English → `ltr` |
| Level | Middle/high school (grades 7–12). Adjust vocabulary for "primary" or "university". |
| Focus | Full lesson. If the user names one part (e.g. synapse only), still include anatomy + that part. |

## Output: one HTML file, five sections
Build a single `neuron-explorer.html` (inline CSS + JS, inline SVG, no external images, no CDN required; system Arabic font stack `Tajawal, "Noto Kufi Arabic", Segoe UI, sans-serif` with graceful fallback).

1. **Hero** — title, one-sentence definition: *the neuron is the basic unit of the nervous system that receives, processes and transmits electrical and chemical signals.*
2. **Interactive anatomy (SVG)** — a drawn neuron with clickable/hoverable parts. Clicking a part highlights it and shows a card (name AR/EN + function in one or two sentences):
   - Dendrites — receive signals from other neurons
   - Cell body (soma) — integrates incoming signals; holds the nucleus
   - Nucleus — contains DNA, controls the cell
   - Axon hillock — where the decision to fire is made (threshold)
   - Axon — carries the impulse away from the soma
   - Myelin sheath — insulates and speeds conduction
   - Nodes of Ranvier — gaps where the signal "jumps" (saltatory conduction)
   - Axon terminals — release neurotransmitters into the synapse
3. **Action-potential simulator** — a slider for stimulus strength (0–100) and a "Stimulate" button. If stimulus < threshold (≈ −55 mV reached), show a small bump that fades ("sub-threshold — no impulse"). If ≥ threshold, animate a glowing pulse travelling along the axon, jumping node to node, while a live voltage graph (canvas) draws the curve: resting −70 mV → depolarization to +30/+40 mV → repolarization → hyperpolarization ≈ −80 mV → back to −70 mV. Show the all-or-none rule in a caption. Optional toggle "Remove myelin" makes the pulse visibly slower.
4. **Synapse animation** — zoom view of a terminal and the next dendrite: vesicles move, release neurotransmitter dots across the gap, dots bind to receptors, receiving side lights up. Button to replay.
5. **Neuron types + quiz** — three cards (sensory, motor, interneuron) with a one-line role each; then a 5-question multiple-choice quiz with instant feedback and a final score.

## Design rules
- Dark navy background (`#0b1530`), cyan/teal signal glow (`#22d3ee`), gold accents (`#f5b942`); rounded cards; generous spacing; responsive down to 360 px.
- Every label bilingual when the page is Arabic: Arabic first, English small below.
- Animations with `requestAnimationFrame`; respect `prefers-reduced-motion` (show static states).
- No flags, logos, brand marks or photos of people.
- Accessibility: buttons are real `<button>`s, parts are focusable (`tabindex="0"`, Enter = click), color is never the only cue.

## Scientific accuracy checklist (verify before delivering)
- Resting potential ≈ −70 mV; threshold ≈ −55 mV; peak ≈ +30 to +40 mV.
- Depolarization = Na⁺ in; repolarization = K⁺ out; Na⁺/K⁺ pump restores gradients (3 Na⁺ out / 2 K⁺ in).
- Myelin made by Schwann cells (PNS) / oligodendrocytes (CNS).
- Impulse is all-or-none; strength is coded by **frequency**, not size.
- Synapse: Ca²⁺ entry triggers vesicle release; examples of neurotransmitters: acetylcholine, dopamine, serotonin.

## Delivery
1. Write the HTML file and offer it as a download.
2. In chat, give a 3-line summary of what the page contains and how to use it (click parts, move the slider, replay the synapse, take the quiz).
3. If the user asks for a printable version, add a "Print" button that switches to a static, labeled layout.

## Example prompts
- `Use $neuron-explorer to build an interactive Arabic lesson on neurons for grade 9.`
- `اشرح لي الخلية العصبية بشكل تفاعلي`
- `Make a neuron + synapse simulator with a quiz, in English.`
