# Cooperative Horror Game (Inspired by MIMESIS)

## Project Overview

This project is a **multiplayer cooperative horror game** developed using **Unity Engine**.  
The gameplay focuses on teamwork, exploration, and psychological horror elements where players must work together to collect valuable items while avoiding dangerous creatures.

The design is inspired by the gameplay style of **MIMESIS**, a psychological horror co-op game where trust between players becomes uncertain.

One of the core mechanics of this game is a **monster that can disguise itself as a player and mimic previously recorded voice lines**, creating tension and paranoia among players.

---

# Platform

PC (Windows)

---

# Game Engine

Unity LTS  
Rendering Pipeline: Universal Render Pipeline (URP)

URP is used to:

- Optimize performance
- Improve lighting for horror environments
- Apply post-processing effects such as:
  - Film Grain
  - Chromatic Aberration
  - Fog
  - Color Grading

---

# Core Gameplay Loop

The gameplay loop defines the main player experience.
Start Game
→
Join Lobby
→
Spawn in Mission Area
→
Explore the Map
→
Find Valuable Items
→
Cooperate to Carry Heavy Objects
→
Avoid or Escape Monsters
→
Deliver Loot to Extraction Zone
→
Receive Money / Rewards
→
Start Next Mission

---

# Gameplay Features

## Exploration

Players explore dangerous environments such as:

- Abandoned factories
- Laboratories
- Industrial warehouses

These environments are procedurally generated to ensure replayability.

---

## Loot System

Items have **weight and value**, affecting how players carry them.

| Item | Weight | Value |
|-----|------|------|
Laptop | Medium | 100 |
Generator | Heavy | 300 |
Data Disk | Light | 50 |

Some items require **two players to carry together**.

---

## Cooperative Gameplay

Players must communicate and cooperate to:

- Carry heavy objects
- Navigate dangerous environments
- Escape enemies
- Complete missions

Teamwork is essential for survival.

---

# Mimic Monster System

One of the most important horror mechanics in the game is the **Mimic Monster**.

This creature can:

- Copy the appearance of a player
- Mimic player movement
- Replay previously recorded voice lines from players

This mechanic introduces **psychological horror**, where players cannot always trust their teammates.

---

## Mimic Behaviour Phases

### Observation

The monster secretly observes players and records their voice chat.

---

### Mimic

The monster selects a nearby player and copies:

- Character model
- Animation
- Player name

It then blends into the group.

---

### Voice Mimic

The monster can replay recorded voice lines.

Example:

A player previously said:

> "Come here, I found something."

Later, the monster may repeat the same sentence to lure other players.

---

### Attack

Once a player approaches, the monster reveals itself and attacks.

---

# Technology Stack

## Game Engine

Unity LTS with URP

---

## Networking

Photon Fusion 2

Features:

- Multiplayer networking
- Lobby system
- Player synchronization
- Object synchronization

---

## Physics System

Unity Rigidbody Physics

Used for:

- Object interactions
- Item carrying
- Environmental physics

Grab interactions are implemented using:

- Rigidbody
- Configurable Joint

---

## Artificial Intelligence

Unity NavMesh system

AI features include:

- Pathfinding
- Player detection
- Attack behavior
- Mimic behavior

---

## Voice Chat System

Photon Voice 2

Supports:

- Proximity voice chat
- Spatial audio
- Voice recording

---

# Voice Mimic System

The monster can replay previously recorded player voices.

## Voice Recording

Player voice chat is recorded and stored in a buffer.

Example:
VoiceBuffer

Player1
clip1
clip2
clip3

---

## Voice Playback

The monster selects a random audio clip from the buffer and plays it using spatial audio.

This makes the sound appear to come from the monster’s position.

---

# Game Architecture
Player Client
│
Input System
│
Player Controller
│
Gameplay Systems
│
├── Physics System
├── AI System
├── Loot System
│
Networking Layer (Photon Fusion)
│
Game Host

---

# System Architecture
Player Client
│
Networking Layer
│
├── Physics System
├── AI System
├── Voice Chat System
│
Game Manager

---

# Procedural Map Generation

The game uses **modular procedural generation** to create maps.

Room modules include:

- Corridor
- Storage Room
- Control Room
- Laboratory

---

## Map Generation Process
Start Game
→
Create Map Grid
→
Spawn Starting Room
→
Attach Random Rooms
→
Validate Room Connections
→
Spawn Loot Points
→
Spawn Enemy Locations
→
Spawn Exit Point


---

# Team Work Distribution

The project is developed by **two team members**, with responsibilities split evenly.

---

## Member 1 – Gameplay & Physics Programmer

Responsibilities:

- Player Controller
- Camera System
- Object Interaction System
- Loot System
- Cooperative Carry System
- Gameplay UI
- Mission Logic

Technologies used:

- Unity Physics
- Animation Rigging
- Unity UI

---

## Member 2 – Multiplayer & AI Programmer

Responsibilities:

- Photon Fusion Networking
- Lobby System
- Player Synchronization
- Object Network Sync
- Enemy AI
- Mimic Monster System
- Voice Mimic System
- Procedural Map Generation

Technologies used:

- Photon Fusion
- Photon Voice
- NavMesh AI

---

# Development Timeline (10 Weeks)

## Week 1–2

- Project setup
- Player controller
- Physics interaction

---

## Week 3–4

- Multiplayer lobby system
- Player synchronization

---

## Week 5–6

- Loot system
- Cooperative carry mechanics

---

## Week 7–8

- Enemy AI
- Mimic monster system

---

## Week 9–10

- Voice mimic system
- Bug fixing
- Performance optimization
- Final build

