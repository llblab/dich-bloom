# Dich // Bloom

A single-file audiovisual instrument built in plain HTML, Canvas 2D, and Web Audio.

Open `dich.html` in a modern browser and interact with the world using the cursor and the left mouse button. There is no visible HUD and no on-screen control panel. The piece is meant to be discovered through play.

## Core Idea

`dich` is an interactive constellation of sound nodes.

Each run generates a different world:

- a different instrument profile
- a different scale and key center
- different mutation ranges and combo windows
- different physics warps
- different available cursor modes
- different genetic makeup for every node

The run evolves while you play. The main hidden objective is:

**activate as many triangles as possible**

Triangles are the main driver of world evolution.

## Controls

Shortcuts are based on **physical key codes**, not typed characters, so they work across keyboard layouts.

- **R** — reroll the world
- **M** — mute / unmute
- **F** — fullscreen
- **Space** — pause / resume

Mouse:

- **Move cursor** — interact with nodes, edges, and triangles
- **LMB down** — switch into grip interaction mode
- **LMB up** — release stored grip force

## Interaction Model

The world has three interactive layers:

### 1. Node interaction

When the cursor touches a node, it plays the node's **genetic percussion**.

Every node has its own DNA, so node hits are not simple repeated samples. A node can behave like a click, tom, hat, snap, FM hit, filtered noise, metallic ring, grain burst, pluck, or breath depending on its genes.

### 2. Edge interaction

When the cursor crosses an edge, the sound is created from the **combined genes of the two connected nodes**.

This usually behaves like a pluck, string, ping, or hybrid struck tone.

### 3. Triangle interaction

When the cursor enters a triangle, the sound is created from the **combined genes of all three triangle nodes**.

Triangles are the most important structure in the piece. They produce low-register, bass-like, or chordal sounds and they drive run evolution.

## Two Cursor Contact States

The system distinguishes between two kinds of contact:

### Touch

When **LMB is not pressed**:

- node contact triggers genetic percussion
- edge contact triggers two-node crossover sound
- triangle contact triggers three-node crossover sound
- **triangle activation evolves the world**
- the world may grow by spawning new nodes near the activated triangle
- triangle activations raise the run's evolution level and help unlock more modes and events

### Grip

When **LMB is pressed**:

- interactions become heavier, denser, and more forceful
- node, edge, and triangle sounds use stronger “grip” variants
- triangle contact no longer evolves the world directly
- instead, triangles **charge stored force**
- the grip charge is shown by a **ciliary force indicator** around the cursor
- orbiting satellites are shown with visible tethers and orbital halos

## Satellite Mechanic

If you stay on a node long enough while gripping it, the node can become a **satellite**.

A satellite:

- detaches from ordinary drift behavior
- starts orbiting the cursor-player
- stays outside the ordinary world graph while attached
- remains visually active and genetically alive

Satellites remain attached while grip force is being accumulated.

When the stored grip force is released, satellites:

- detach from the cursor
- fly outward with burst velocity
- flash and scatter back into the world

## Grip Release

When LMB is released after charging triangles:

- stored force is released at the cursor position
- one or more **activation ripples** expand through the world
- ripples activate nodes they pass through
- activated nodes emit sound and visual response
- attached satellites detach and scatter outward at the same moment

This creates a delayed, player-centered chain reaction.

## Genetic Audio System

Every node is born with a small gene set. Genes influence sound identity and crossover behavior.

Current gene traits include:

- `wave1`, `wave2`
- `octave`
- `detune`
- `attack`, `decay`
- `filterType`
- `filterFreq`, `filterQ`
- `modDepth`, `modRatio`
- `harmonics`
- `noiseAmt`
- `pitchEnv`
- `percStyle`
- `scaleDegree`
- `brightness` — filter intensity and high-frequency content
- `spread` — stereo detune and harmonic width
- `articulation` — attack sharpness and transient character

### Gene crossover

- **Node** = single-node genetic percussion
- **Edge** = crossover of 2 node genes
- **Triangle** = crossover of 3 node genes

Gene crossover changes waveform choice, pitch register, filter shape, modulation, harmonic density, and noise character.

## World Structure Rules

### Nodes

The world usually maintains roughly **18 to 56 active nodes**, depending on the current run and evolution state.

### Edges

Edges are not fully dense. The graph is intentionally constrained.

Rules:

- each node can keep at most **3 edges**
- edges have **hysteresis**: once formed, they can persist slightly longer before breaking
- this makes the graph more readable and more stable musically

### Triangles

A triangle is considered valid only when:

- all **three edges are actually visible** in the current graph
- its area passes the minimum threshold
- **every angle is at least 20°**

This means hidden or ghost triangles are not allowed. If one side is not visible, the triangle is not interactive.

## Evolution and Roguelike Structure

Each run has its own evolving state.

### Run systems

A run tracks:

- unique particles touched
- unique edges crossed
- unique triangles activated
- unique combo discoveries
- total trigger count
- burst meter
- tier progression
- mutation events
- available cursor modes for the current run

### Triangle-driven evolution

Triangles are the main engine of progression.

Activating triangles through normal touch:

- increases evolution pressure
- can grow the world by adding nodes
- advances run progression
- helps unlock new cursor modes during the run
- feeds tier growth more strongly than ordinary particle or edge interaction

### Run tiers

The run has progression tiers. Higher tiers intensify the piece and expand what is available during that run.

### Mutations

Runs can produce temporary world mutations such as:

- gravity inversion
- speed surges
- slow-motion states
- denser or sparser populations
- wetter or drier worlds
- stronger orbit / drift / flash states
- scale shifts
- gene storms

### Rare events

Runs can also trigger rarer world events that may reshuffle genes, colors, scale, or instrument identity.

## Cursor Modes

The cursor evolves alongside the world. Mode is determined by progression level and run tier:

- **Repel** — starting mode
- **Attract** — unlocks at evolution level 0.22 (Genesis → Drift)
- **Orbit** — unlocks at evolution level 0.46 (Drift → Bloom)
- **Stir** — unlocks at evolution level 0.7 (Bloom → Ascension)
- **Vortex** — unlocks at evolution level 0.92 (Ascension → Singularity)
- **Scatter** — unlocks at tier 3 (Resonant)
- **Gravity** — unlocks at tier 4 (Architect)
- **Pulse** — unlocks at tier 5 (Ascended)

The cursor mode changes automatically as the run deepens. Not all modes are necessarily available in every run — some are rolled at world generation.

## Combo Layer

The piece includes hidden interaction combos with randomized windows and thresholds.

Known combo families include:

- line-cross pluck
- triangle bass pulse
- siege
- chain
- prism
- rake
- halo
- echo
- gate
- crown
- weave
- monolith
- relic
- bloomlock

These are still hidden mechanics, but their state is hinted visually through the interactive field rather than through UI text.

## Visual Language

The background is intentionally restrained.

### Background

Only two persistent background layers are kept:

- **stars**
- **aurora / rainbow bands**

The background no longer contains extra fake graph elements that could be confused with interactive nodes or edges.

### Interactive visuals

Interactive layers include:

- glowing particles
- constrained edges
- triangle fills and outlines
- frozen triangle afterimages
- ripples
- sparks and spark trails
- cursor aura
- ciliary grip-force indicator
- satellite nodes orbiting the cursor

## Bloom

Bloom is **audio-reactive**.

When there is no sound, bloom can decay all the way to **zero**.
When the player produces sound, bloom rises from interaction energy rather than existing as a permanent ambient glow.

## Audio Priorities

The system is built so that direct player interaction has priority over decorative sound.

Audio management includes:

- priority-based budgeting
- dynamic throttling for low-priority layers
- shared effect buses
- compression on the master chain
- brick-wall limiter for clipping protection
- per-kind loudness normalization with activity ducking
- velocity-sensitive articulation based on cursor speed
- reduced ambient interference during active play

User-driven sounds are favored over decorative or ambient activity.

## Instrument Profiles and Scales

The world rolls a weighted instrument profile per run.

Current profiles include common and rare identities such as:

- Aether Bloom
- Dust Percussion
- Glass Flora
- Neon Reed
- Velvet FM
- Bronze Circuit
- Xeno Koto
- Void Organ
- Mercury Bells
- Obsidian Choir
- Silk Thread
- Iron Garden

The scale library includes 11 modes/scales, including both familiar and more exotic options.

## Technical Characteristics

- single file: `dich.html`
- no external dependencies
- Canvas 2D rendering
- Web Audio synthesis only
- additive blend-heavy visual style
- physically keyed shortcuts via `KeyboardEvent.code`
- performance-oriented graph building and event trimming

## What the Player Is Really Doing

The piece is not a passive music toy. It behaves more like a run-based instrument-world.

The player is:

- exploring a random sound ecology
- discovering how nodes combine genetically
- learning how to build and trigger triangles
- deciding when to evolve the world and when to store force instead
- collecting satellites while gripping
- releasing shockwaves at meaningful moments
- pushing the run deeper into mutation and complexity

In short:

**touch triangles to evolve the world**

**hold triangles to charge force**

**capture satellites during grip**

**release to detonate the stored structure back into the field**
