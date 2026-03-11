# Cooperative Horror Game (Inspired by MIMESIS)

## Project Overview

This project is a **multiplayer cooperative horror game** developed using **Unity Engine**. The gameplay focuses on **teamwork, exploration, loot extraction, and psychological horror**, where players must work together to collect valuable items and escape dangerous environments while avoiding hostile creatures.

The design is inspired by **MIMESIS**, a psychological horror co-op game where trust between players becomes uncertain.

One of the core mechanics of this project is a **monster that can disguise itself as a player and replay previously recorded voice lines**, creating tension, paranoia, and misinformation within the team.

---

## Platform

**PC (Windows)**

---

## Game Engine

**Unity LTS**
**Rendering Pipeline:** Universal Render Pipeline (**URP**)

URP is used to:

* Optimize performance
* Improve lighting for horror environments
* Support post-processing effects such as:

  * Film Grain
  * Chromatic Aberration
  * Fog
  * Color Grading

---

## Core Gameplay Loop

```text
Start Game
→ Join Lobby
→ Spawn in Mission Area
→ Explore the Map
→ Find Valuable Items
→ Cooperate to Carry Heavy Objects
→ Avoid or Escape Monsters
→ Deliver Loot to Extraction Zone
→ Receive Money / Rewards
→ Start Next Mission
```

---

## Gameplay Features

### Exploration

Players explore dangerous environments such as:

* Abandoned factories
* Laboratories
* Industrial warehouses

These environments are designed to support **procedural or semi-procedural generation** for replayability.

---

### Loot System

Items have **weight** and **value**, affecting how players carry and prioritize them.

| Item      | Weight | Value |
| --------- | ------ | ----- |
| Laptop    | Medium | 100   |
| Generator | Heavy  | 300   |
| Data Disk | Light  | 50    |

Some items require **two players to carry together**.

---

### Cooperative Gameplay

Players must communicate and cooperate to:

* Carry heavy objects
* Navigate dangerous environments
* Escape enemies
* Complete missions efficiently

Teamwork is essential for survival and success.

---

## Mimic Monster System

One of the most important horror mechanics in the game is the **Mimic Monster**.

This creature can:

* Copy the appearance of a player
* Mimic player movement
* Replay previously recorded voice lines from players

This mechanic introduces **psychological horror**, where players cannot always trust their teammates.

---

## Mimic Behaviour Phases

### Observation

The monster secretly observes players and records their voice chat patterns.

### Mimic

The monster selects a nearby or isolated player and copies:

* Character model
* Basic animation behavior
* Player display name

It then attempts to blend into the group.

### Voice Mimic

The monster can replay recorded voice lines.

Example:

> "Come here, I found something."

Later, the monster may repeat the same sentence to lure another player away from the team.

### Attack

Once a player approaches or becomes isolated, the monster reveals itself and attacks.

---

## Technology Stack

### Game Engine

* Unity LTS
* Universal Render Pipeline (URP)

### Networking

**Photon Fusion 2**

Used for:

* Multiplayer networking
* Lobby system
* Player synchronization
* Object synchronization
* Host-authoritative gameplay logic

### Physics System

**Unity Rigidbody Physics**

Used for:

* Object interactions
* Loot carrying
* Environmental physics

Grab interactions are implemented using:

* Rigidbody
* Configurable Joint

### Artificial Intelligence

**Unity NavMesh System**

AI features include:

* Pathfinding
* Player detection
* Chase/attack behavior
* Mimic/disguise logic

### Voice Chat System

**Photon Voice 2**

Supports:

* Proximity voice chat
* Spatial audio
* Voice transmission between players

---

## Voice Mimic System

The monster can replay previously recorded player voices.

### Voice Recording

Player voice chat is recorded into a short-term buffer.

Example structure:

```text
VoiceBuffer
├── Player1
│   ├── clip1
│   ├── clip2
│   └── clip3
├── Player2
│   ├── clip1
│   └── clip2
```

### Voice Playback

The Mimic selects a random or context-relevant audio clip from the target player's buffer and plays it back using **3D spatial audio** from the monster's position.

This makes the sound appear to come from somewhere in the environment, increasing tension and uncertainty.

---

## Game Architecture

```text
Player Client
│
├── Input System
├── Player Controller
├── Gameplay Systems
│   ├── Physics System
│   ├── AI System
│   └── Loot System
│
└── Networking Layer (Photon Fusion)
    └── Game Host
```

---

## System Architecture

```text
Player Client
│
├── Networking Layer
├── Physics System
├── AI System
├── Voice Chat System
└── Game Manager
```

---

## Procedural Map Generation

The game uses **modular procedural generation** to create replayable maps.

### Room Modules

* Corridor
* Storage Room
* Control Room
* Laboratory
* Power Room
* Extraction Room

### Map Generation Process

```text
Start Game
→ Create Map Grid / Seed
→ Spawn Starting Room
→ Attach Random Rooms
→ Validate Room Connections
→ Spawn Loot Points
→ Spawn Enemy Locations
→ Spawn Exit / Extraction Point
```

For prototype scope, a **semi-procedural modular approach** is recommended to keep the system stable and production-friendly.

---

## Team Work Distribution

The project is developed by **two team members**, with responsibilities split evenly.

### Member 1 – Gameplay & Physics Programmer

Responsibilities:

* Player Controller
* Camera System
* Object Interaction System
* Loot System
* Cooperative Carry System
* Gameplay UI
* Mission Logic

Technologies used:

* Unity Physics
* Animation Rigging
* Unity UI / TextMeshPro

### Member 2 – Multiplayer & AI Programmer

Responsibilities:

* Photon Fusion Networking
* Lobby System
* Player Synchronization
* Object Network Sync
* Enemy AI
* Mimic Monster System
* Voice Mimic System
* Procedural Map Generation

Technologies used:

* Photon Fusion 2
* Photon Voice 2
* NavMesh AI

---

## Development Timeline (10 Weeks)

### Week 1–2

* Project setup
* Player controller
* Physics interaction
* Basic loot handling

### Week 3–4

* Multiplayer lobby system
* Player synchronization
* Networked loot interaction

### Week 5–6

* Loot system refinement
* Cooperative carry mechanics
* Basic enemy AI

### Week 7–8

* Mimic monster system
* Disguise behavior
* Voice chat integration

### Week 9–10

* Voice mimic system
* Procedural map generation
* Bug fixing
* Performance optimization
* Final build preparation

---

## Prototype Scope

The initial playable prototype should include:

* 1 playable environment theme (recommended: **Abandoned Laboratory**)
* 2-player co-op support
* Lobby creation and joining
* Light, medium, and heavy loot items
* Extraction zone and reward calculation
* 1 Mimic monster with disguise and reveal behavior
* Proximity voice chat
* Basic modular map generation

---

## Design Goals

The prototype is considered successful if it can demonstrate:

1. A stable multiplayer co-op session
2. A complete loot extraction loop
3. At least one heavy object requiring teamwork
4. A Mimic enemy that can impersonate a player
5. A voice-based deception mechanic that creates psychological tension

---

## Future Expansion

Possible future features beyond the prototype:

* More enemy types
* More map themes
* Expanded mission variety
* Equipment and progression system
* Enhanced voice manipulation and deception behaviors
* More advanced procedural generation

---

## Repository Notes

This README is intended to serve as the **high-level proposal and project overview** for the GitHub repository.

Recommended additional documents for the repository:

* `GDD.md` — full Game Design Document
* `TDD.md` — Technical Design Document
* `TASK_BOARD.md` — production schedule and task breakdown
* `TEST_PLAN.md` — playtest and QA checklist

---

## Status

**Current Stage:** Pre-Production / Prototype Planning

The current focus is on building a **playable vertical slice** that proves the project’s core mechanics and horror identity.
