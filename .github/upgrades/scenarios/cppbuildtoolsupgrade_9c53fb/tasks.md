# C++ Build Tools Upgrade Warning Fixes Tasks

## Overview

This document tracks the execution of fixes for 94 compiler warnings (71× C4018 signed/unsigned mismatch, 23× C4101 unreferenced variables) generated after upgrading to Visual Studio Build Tools v143. Fixes will be applied surgically by project in build order, followed by solution-wide verification.

**Progress**: 0/7 tasks complete (0%) ![0%](https://progress-bar.xyz/0)

---

## Tasks

### [▶] TASK-001: Create warning fixes branch
**References**: Plan §TASK-001

- [▶] (1) Create new branch `fix/cpp-build-warnings` from current branch
- [ ] (2) Current branch is `fix/cpp-build-warnings` (**Verify**)

---

### [ ] TASK-002: Fix hlbsp project warnings (7 total)
**References**: Plan §TASK-002, Plan §Root Cause Analysis

- [ ] (1) Fix portals.cpp C4018 warnings at lines 223, 238: cast `w->m_NumPoints` to `(int)` per Plan §TASK-002-A
- [ ] (2) Fix solidbsp.cpp C4018 warning at line 2116: cast `p->winding->m_NumPoints` to `(int)` per Plan §TASK-002-B
- [ ] (3) Fix solidbsp.cpp C4101 warnings at lines 483, 660: remove unused variable declarations (`j`, `l`, `p2`) per Plan §TASK-002-B
- [ ] (4) Fix surfaces.cpp C4101 warning at line 225: move `newsize[2]` declaration inside `#else` block per Plan §TASK-002-C
- [ ] (5) Fix tjunc.cpp C4101 warning at line 55: move `newsize[2]` declaration inside `#else` block per Plan §TASK-002-D
- [ ] (6) Build hlbsp project
- [ ] (7) hlbsp builds with 0 errors and 0 warnings (**Verify**)

---

### [ ] TASK-003: Fix hlvis project warnings (27 total)
**References**: Plan §TASK-003, Plan §Root Cause Analysis

- [ ] (1) Fix flow.cpp C4018 warnings per Plan §TASK-003-A: cast unsigned comparisons at lines 154, 249, 274, 459, 469, 541, plus verify and fix lines 1516-1729 comparisons
- [ ] (2) Fix flow.cpp C4101 warnings at lines 1494, 1498, 1500: move variable declarations (`c`, `d`, `delta`, `new_dist`) inside `#else` blocks per Plan §TASK-003-A
- [ ] (3) Fix vis.cpp C4018 warnings per Plan §TASK-003-B: change `min` to unsigned at line 368, cast `g_leafcounts` to unsigned at lines 685/711, cast `g_overview_count` to unsigned at lines 1159/1178
- [ ] (4) Fix zones.cpp C4018 warnings at lines 81, 106, 133: cast `g_nummodels` and `mod->numfaces` to `(UINT32)` per Plan §TASK-003-C
- [ ] (5) Build hlvis project
- [ ] (6) hlvis builds with 0 errors and 0 warnings (**Verify**)

---

### [ ] TASK-004: Fix hlrad project warnings (47 total)
**References**: Plan §TASK-004, Plan §Root Cause Analysis

- [ ] (1) Fix lerp.cpp C4018 warnings at lines 1124, 1135: cast `m_NumPoints` to `(int)` per Plan §TASK-004-A
- [ ] (2) Fix lightmap.cpp C4018 warnings at lines 52, 1388, 1407, 1612, 1968, 5099, 5693: cast `m_NumPoints` to `(int)` per Plan §TASK-004-B
- [ ] (3) Fix lightmap.cpp C4101 warnings at lines 5990, 7578, 8651: remove unused variable declarations (`delta`, `i`, `v`) per Plan §TASK-004-B
- [ ] (4) Fix loadtextures.cpp C4018 warning at line 185: cast `strlen(value)+1` to `(int)` per Plan §TASK-004-C
- [ ] (5) Fix mathutil.cpp C4018 warnings at lines 198, 549, 955: cast values to `(int)` per Plan §TASK-004-D
- [ ] (6) Fix qrad.cpp C4018 warnings at lines 770, 856, 943, 1887, 2286, 3940: cast `m_NumPoints` to `(int)` per Plan §TASK-004-E
- [ ] (7) Fix qrad.cpp C4101 warnings at lines 3910, 3912: remove unused variable declarations (`i`, `j`) per Plan §TASK-004-E
- [ ] (8) Fix qradutil.cpp C4018 warnings at lines 263, 268, 727, 735, 762, 988: cast `g_opaque_face_count` to `(int)` per Plan §TASK-004-F
- [ ] (9) Fix sparse.cpp C4018 warnings at lines 73, 77, 107, 112, 139, 144, 702: apply appropriate casts per Plan §TASK-004-G
- [ ] (10) Fix sparse.cpp C4101 warnings at lines 638, 641: remove unused variable declarations (`lface`, `leaf`) per Plan §TASK-004-G
- [ ] (11) Fix trace.cpp C4018 warnings at lines 612, 614, 753: cast `m_NumPoints` to `(int)` per Plan §TASK-004-H
- [ ] (12) Fix vismatrix.cpp C4101 warnings at lines 284, 287: remove unused variable declarations (`lface`, `leaf`) per Plan §TASK-004-I
- [ ] (13) Fix vismatrixutil.cpp C4018 warning at line 45: cast `offset` to `(int)` per Plan §TASK-004-J
- [ ] (14) Fix vismatrixutil.cpp C4101 warnings at lines 237, 735: remove unused `send` variable declarations per Plan §TASK-004-J
- [ ] (15) Build hlrad project
- [ ] (16) hlrad builds with 0 errors and 0 warnings (**Verify**)

---

### [ ] TASK-005: Fix hlcsg project warnings (13 total)
**References**: Plan §TASK-005, Plan §Root Cause Analysis

- [ ] (1) Fix brush.cpp C4018 warnings at 6 locations: cast `m_NumPoints` to `(int)` per Plan §TASK-005-A
- [ ] (2) Fix map.cpp C4018 warning at line 1424: verify type mismatch and apply appropriate cast per Plan §TASK-005-B
- [ ] (3) Fix qcsg.cpp C4018 warnings at lines 499, 655, 704, 1065: cast `m_NumPoints` to `(int)` per Plan §TASK-005-C
- [ ] (4) Fix qcsg.cpp C4101 warning at line 1731: remove unused `type` variable declaration per Plan §TASK-005-C
- [ ] (5) Fix wadpath.cpp C4101 warning at line 15: remove unused `i` variable declaration per Plan §TASK-005-D
- [ ] (6) Build hlcsg project
- [ ] (7) hlcsg builds with 0 errors and 0 warnings (**Verify**)

---

### [ ] TASK-006: Rebuild solution and verify all warnings resolved
**References**: Plan §TASK-006

- [ ] (1) Rebuild entire solution (F:\GitHub\VHLT-V34\src\zhlt-vluzacn\zhlt.sln)
- [ ] (2) Solution builds with 0 errors (**Verify**)
- [ ] (3) Solution builds with 0 warnings (**Verify**)

---

### [ ] TASK-007: Commit all warning fixes
**References**: Plan §TASK-007

- [ ] (1) Stage all changes: `git add -A -- ":!.vs"`
- [ ] (2) Commit with message: "fix: resolve all 94 C++ build warnings after v143 toolset upgrade - C4018 (71): Add explicit casts for signed/unsigned comparisons - C4101 (23): Remove unused variable declarations / move into inactive #ifdef branches"

---
