Task: Reverse-engineer the current codebase to update and align the documentation (`README.md` and architecture documentation files).

Context & Philosophy:
Currently, the `README.md` and architecture files are outdated and are incorrectly treated as a rigid "bible" or specification. We need to shift to a "Living Documentation" approach. The actual implementation in the code is the ONLY Single Source of Truth (SSOT). 

Instructions:
1. Analyze the entire codebase to understand the current, real-world state of the project, its actual architecture, dependencies, data flow, and implemented features. **Se sei Jules (agente bash), usa i comandi per esplorare massivamente i file. Se sei Antigravity (chat), chiedi all'utente di caricare o mostrare i file salienti.**
2. Review the existing `README.md` and any architecture files (e.g., `ARCHITECTURE.md` or similar in subfolders).
3. Identify discrepancies where the documentation describes planned features, deprecated structures, or aspirational goals that do NOT match the current code.
4. Rewrite and update these documentation files so they strictly reflect the **state of the art (as-is)** of the codebase today. Remove or clearly label any "future/todo" features so they are not confused with current implementations.
5. Add a brief note in the introduction of the architecture documentation stating that this is an evolutionary, living document that reflects the actual implementation, not a rigid top-down specification.

**Se sei Jules**, scrivi direttamente le modifiche nei file `README.md` e `ARCHITECTURE.md` (o simili) e preparati a fare una PR o un commit se richiesto. **Se sei Antigravity**, fornisci i testi aggiornati all'interno della chat chiedendo all'utente di incollarli.
