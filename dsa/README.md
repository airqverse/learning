# DSA Study Vault - System Guide

This repository is an Obsidian vault designed for learning Data Structures and Algorithms through a highly interconnected graph-based approach.

## 🏗 Architecture
The vault follows a **Map of Content (MOC)** hierarchy to ensure the Graph View remains organized and readable:

- `00_Index/`: Central hub and category indices.
- `01_Data_Structures/`: Notes on specific data structures.
- `02_Algorithms/`: Logic and implementations.
- `03_Techniques/`: Higher-level patterns (e.g., Sliding Window).
- `04_Complexity/`: Theoretical efficiency classes.
- `05_Problems/`: Solved exercises/LeetCode problems (the "glue" of the graph).
- `99_Templates/`: Blueprint for every note type.

## 🔗 Linking Strategy (Crucial for Graph View)
To maintain a meaningful Graph View, every new note **must** follow these rules:
1. **Vertical Links**: Every note must link back to its respective MOC (e.g., `[[00_Index/01_Data_Structures_MOC|Back to Index]]`).
2. **Horizontal Links**:
   - **Algorithms** must link to their **Complexity** and **Data Structures** used.
   - **Problems** must link to the **Data Structure**, **Technique**, and **Complexity** class.
3. **Pathing**: Use explicit relative paths for links to ensure compatibility (e.g., `[[04_Complexity/O(n) - Linear|O(n)]]`).

## 🤖 Instructions for AI Agents
When asked to add or update notes:
1. **Use Templates**: Always refer to the files in `99_Templates/` for structure.
2. **Auto-Linking**: 
   - Identify the Time and Space complexity and link to the relevant files in `04_Complexity/`.
   - If a Python implementation is requested, place it in a `python` code block.
3. **Consistency**: Use `#tags` for status (e.g., `#to-solve`, `#review-needed`) and `[[links]]` for knowledge connections.
4. **Maintenance**: When adding a new note, check if it needs to be listed in its category's `MOC` file in `00_Index/`.

## 🛠 Workflow for adding a Problem
1. Create `05_Problems/Problem Name.md`.
2. Apply `99_Templates/05_Problem_Template.md`.
3. Populate links to DS, Techniques, and Complexity.
4. Add the problem to `00_Index/05_Problems_MOC.md`.
