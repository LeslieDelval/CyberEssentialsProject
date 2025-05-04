# CyberEssentialsProject
HackTheBox Project 
🧬 Shiny Hunter
Group 6

Leslie Delval

Shipra Sinha

Praneeth Reddy Gunna

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
ShinyHunter.py is the game itself
script.py is the bruteforce script

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

🎮 Why Shiny Hunter?
Shiny Hunter is an HTB (Hack The Box) challenge disguised as a Pokémon-themed terminal game. The goal is to capture a shiny Pokémon and retrieve a hidden flag.

Reasons for choosing this project:

📘 Game-Based: Engaging and interactive, simulating a classic Pokémon adventure.

🐍 Python-Based: Aligned with our team’s programming expertise.

🎯 Clear Objective: Catch a shiny Pokémon to get the flag.

🔐 Vulnerabilities: Despite using random, the game logic is predictable.

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Uses Python’s random module (predictable output).

LCG-based (Linear Congruential Generator) seed generation logic can be reverse-engineered.

The flag is embedded and returned on shiny encounter.

🧠 Explored Strategies
❌ Reverse Engineering
Requires full access to game binaries or source.

Often blocked in CTFs.

Not feasible when logic is hidden server-side.

✅ Brute Force (Used)
Based on mathematical knowledge of the game logic.

Efficient: Only needs partial knowledge (e.g., MAC address, time).

Works without direct access to game internals.

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

🕹️ Game Components
Generates a random MAC address.

Introduces player using ASCII-art Professor.

Player enters name and selects a starter Pokémon.

Pokémon stats are randomly generated using PRNG logic.

If generated Pokémon is shiny (value < 8), the flag is shown.

Key Logic & Libraries:

random, time, uuid, os, sys

Uses LCG:

python
Copy
Edit
def lcg(seed, a=1664525, c=1013904223, m=2**32):
    return (a * seed + c) % m
Shiny value determined from:

Trainer ID

Secret ID

Personal ID

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

🛠️ Brute Force Strategy
Game seed is time-based and sensitive to system clock.

Script tries combinations of:

MAC addresses

Wait times (to sync with server's clock)

Extracts MAC from game prompt.

Loops through inputs to find shiny-producing seed.

Used Functions:

lcg()

generate_ids()

generate_poketmon()

Once a shiny is found, the script:

Auto-enters name

Selects a starter

Retrieves the flag
