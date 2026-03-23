# DSA Knowledge Base (Dynamic Pair-Programming Readiness)

This repository is a highly structured, interconnected Obsidian vault designed to build **unshakeable fundamental muscle memory** and **pattern recognition** for live, dynamic pair-programming Data Structures and Algorithms (DSA) interviews. 

All code examples in this vault are standardized in **Python** (per global preference), prioritizing clean, readable, and idiomatic interview-ready implementations.

## 📁 Folder Structure

- **`00_Index/`**: The Map. Entry points and category-specific Maps of Content (MOC).
- **`01_Data_Structures/`**: Core memory layouts (Arrays, Trees, Graphs, Hash Tables).
- **`02_Algorithms/`**: Core logic and traversals (BFS, DFS, Binary Search, Sorting).
- **`03_Techniques/`**: Meta-patterns for problem-solving (Sliding Window, Two Pointers).
- **`04_Complexity/`**: Theoretical efficiency classes (Big O Time/Space trade-offs).
- **`05_Problems/`**: The "Glue." Specific LeetCode/interview problems mapping back to DS & Algo.
- **`98_Flashcards/`**: Spaced-repetition flashcard files for active recall and muscle memory.
- **`99_Templates/`**: Blueprints for automation with AI Assistants.

## 🏆 Interview Readiness Strategy

Passing a live pair-programming interview is not about memorizing 500 LeetCode solutions; it is about pattern matching, communicating trade-offs, and flawlessly executing core mechanics without hesitation.

### Phase 1: Core Muscle Memory (The "2-Minute Rule")
You must be able to write the standard implementation of BFS, DFS, Binary Search, and a Trie in under 2 minutes without syntax errors. 
- **Action:** Drill the core templates in `01_Data_Structures` and `02_Algorithms`. Use transclusion flashcards to memorize the exact Python syntax.

### Phase 2: Pattern Recognition (The "Aha!" Moment)
Interviewers test your ability to map a vague prompt to a known algorithmic technique.
- **Action:** Internalize the notes in `03_Techniques/`. (e.g., "Sorted array + find pairs" -> Two Pointers; "Contiguous subarray" -> Sliding Window). 

### Phase 3: Communication & Trade-offs (The "Big O" Defense)
You must proactively state the Time and Space complexity of your brute force *before* writing optimized code.
- **Action:** Every algorithmic decision must be defended using the notes in `04_Complexity/`. Know exactly *why* a Hash Map is amortized O(1) vs. worst-case O(n).

---

## 🛠 Guidelines for AI Assistants (Gemini/Cursor)

When modifying or adding new notes, strictly adhere to these principles:

1. **Python Exclusivity**: All code snippets, templates, and problem solutions MUST be written in Python unless explicitly requested otherwise.
2. **Path-Based Tagging**: The tag structure MUST correspond directly to the physical folder path of the knowledge base (excluding the numerical prefixes).
   - `00_Index/` -> `#index` (Flat tag for MOCs).
   - `01_Data_Structures/` -> `#data_structures/trees`
   - `03_Techniques/` -> `#techniques/sliding_window`
3. **Template Fidelity**: Always refer to the files in `99_Templates/` for structure.
4. **Graph Optimization**: 
   - **Algorithms** must link to their **Complexity** and **Data Structures**.
   - **Problems** must link to the **Data Structure**, **Technique**, and **Complexity** class.
5. **MOC Anchor Linking**: When generating a new note, you MUST automatically add a link to it in the corresponding `00_Index/` MOC file.

---

## 🧠 Flashcard Ecosystem (Spaced Repetition)

The `98_Flashcards/` directory is designed to build rapid recall for dynamic interviews. It follows the exact same architectural rules as the `google_cloud` vault:

### 1. Mirrored Directory Structure
The `98_Flashcards/` folder MUST mirror the structural paths of the broader vault.
- *Example:* `02_Algorithms/BFS.md` -> `98_Flashcards/02_Algorithms/BFS_Flashcards.md`.

### 2. Strict Tag Hierarchy (Logical Routing)
- The absolute root tag MUST be: `#flashcards/`
- *Example:* `#flashcards/algorithms/bfs` or `#flashcards/techniques/sliding_window`.

### 3. DSA-Specific Flashcard Formats
To maximize interview readiness, use the following flashcard formats:

1. **Muscle Memory Code Blocks (`?`):** Test the exact implementation of a core algorithm.
   - *Prompt:* Implement the standard template for Binary Search in Python. `?`
   - *Answer:* Embed the actual code block via transclusion (`![[Binary_Search^python-template]]`) to maintain DRY principles.
2. **Cloze Deletions (`==text==`) for Complexity:** Force recall of exact Big O bounds and trade-offs.
   - *Example:* "In a perfectly balanced Binary Search Tree, lookup is ==O(log n)==, but in a degenerate tree it becomes ==O(n)==, acting like a Linked List."
3. **Pattern Matching Scenarios (`?`):** Provide a generic interview prompt and ask for the optimal technique.
   - *Prompt:* "Find the longest substring without repeating characters. What is the optimal technique and its time complexity?" `?`
   - *Answer:* "Technique: Sliding Window with a Hash Set. Time Complexity: O(n)."
4. **Comparative Differentiators (`::`):** 
   - *Example:* "When to use BFS vs DFS for finding a path? :: BFS guarantees the shortest path in an unweighted graph, but takes more memory (O(V)). DFS is more memory efficient (O(h)) but does not guarantee the shortest path."