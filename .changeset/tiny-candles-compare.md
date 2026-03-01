---
"@ts-graphviz/react": patch
---

Add comprehensive unit tests for GraphPortal component and fix portal timing bug.

**New Features:**
- Added 18 unit tests covering GraphPortal functionality including basic rendering, prop handling, context behavior, and real-world use cases

**Bug Fixes:**
- Fixed GraphPortal timing issue where portaling into subgraphs didn't work when the portal was placed outside the target subgraph
- Graph, Digraph, and Subgraph components now register in GraphMap during render phase (when .id is defined) instead of in useEffect, ensuring synchronous availability for GraphPortal lookups
- Added cleanup logic using useLayoutEffect to remove stale GraphMap entries on component unmount or ID changes, preventing memory leaks

**Implementation Changes:**
- Removed unused useEffect imports from Graph, Digraph, and Subgraph components
- GraphMap registration now happens synchronously during render for proper portal behavior
- Cleanup functions properly capture ID in closure to handle ID changes correctly
