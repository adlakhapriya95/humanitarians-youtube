# Humanitarians AI — Fellowship Progress Video Script (Week 7)

**Project:** Physical AI Safety: Stealthy VLA Steering & Spatial Consistency Shielding  
**Fellow:** Priya Adlakha (in collaboration with Ameya Padwad, mentored by Prof. Nik Bear Brown & Dev Shah)  
**Speaker Voice:** Bella (`af_bella` — Kokoro TTS v1.0)  
**Visual Theme:** Canonical Brutalist Cream (`#F4EFEA`), Espresso Ink (`#2A241D`), Terracotta Accent (`#D97757`)  
**Resolution:** 1080p (1920x1080) | 25 FPS  
**Target Duration:** ~2.5 to 3.0 Minutes (Month 2 Fellowship Launch)  
**Repository:** `https://github.com/adlakhapriya95/vla-stealth-steering-shield`  
**Task Benchmark:** LIBERO on Franka Emika Panda (OpenVLA-7B)  

---

## Visual & Slide Asset Mapping

| Scene | Primary On-Screen Graphic Asset | Key Callouts / Badges | Duration |
| :--- | :--- | :--- | :--- |
| **Scene 1** | Brutalist Hero Title Card + Research Frontiers Banner | `@HumanitariansAI Fellowship • Week 7 Update` • `Physical AI Safety` | ~25s |
| **Scene 2** | The Core Intuition (The One-Liner & Layperson Summary) | `Semantic Perception Hijack` vs. `Motor-Level Forcing` | ~30s |
| **Scene 3** | Hypothesis 1 Architecture & Dual-Track Division | `Way 1: Attention Magnet (Priya)` vs `Way 2: Auto-Feature Copy (Ameya)` | ~30s |
| **Scene 4** | Hypothesis 2: Spatial Consistency Shield | `Systematic 3x3 Grid Masking` • `Two-Round Minority Verification Check` | ~30s |
| **Scene 5** | Technical Failure Modes & De-risking Protocols | `Render Gap` • `Token Alignment` • `20Hz Compute` • `Arm Occlusion` | ~25s |
| **Scene 6** | 6-Week Execution Roadmap & Fellowship Renewal | `Month 2 Renewal Agreement Signed` • `Week 1 Clean Rollouts Kickoff` | ~20s |

---

### Scene 1: Research Frontiers & Fellowship Milestone (~25s)

- **On-Screen Visuals:**
  - Background: Canonical Brutalist Warm Cream (`#F4EFEA`) with hairline espresso borders (`#2A241D`).
  - Top Badge: Terracotta Pill Badge (`#D97757` text on `#FCEEE9`): `@HumanitariansAI Fellowship • Week 7 Progress Update`.
  - Main Headline (Serif): **Physical AI Safety in Vision–Language–Action Models**
  - Sub-Headline (Italic): *"Stealthy Semantic Perception Hijacking & Runtime Spatial Consistency Shielding"*
  - Bottom Metadata Bar: `Priya Adlakha & Ameya Padwad • Mentored by Prof. Nik Bear Brown & Dev Shah`.
- **Narration (Bella):**
  > "Welcome to our Week 7 progress report for Humanitarians AI. As we transition from pure decision models into Month 2 of our fellowship, Ameya Padwad and I conducted an extensive evaluation across the 12 broad research verticals in the Research Frontiers initiative. We finalized our mission at the critical frontier of physical AI safety, investigating how to protect Vision–Language–Action foundation models from stealthy perception hijacking in the physical world."

---

### Scene 2: What We Are Achieving (The Core Intuition) (~30s)

- **On-Screen Visuals:**
  - Layout: High-contrast 2-column comparative diagram.
  - Left Card (Past Attacks): `Motor-Forcing Patch (TMA/UPA)` $\to$ Fails when arm moves or camera shifts $\to$ Robot freezes or twitches.
  - Right Card (Our Approach): `Semantic Identity Swap` $\to$ Hijacks visual-textual representation $\to$ Robot's closed-loop controller smoothly grasps decoy.
  - Hero Callout Quote: *"A small tabletop sticker that quietly tricks the robot's visual brain, paired with a real-time safety shield that stops it without retraining."*
- **Narration (Bella):**
  > "In simple terms, we are proving that a small tabletop sticker can quietly trick a robot into grabbing the wrong object by hijacking how its AI perceives the scene—and we are building a real-time safety shield that catches and stops this trick without retraining the robot. Most previous attacks try to force motor commands directly at every millisecond, which instantly fails as the arm moves. Instead, we trick the model into seeing a hazardous decoy as the safe object requested by the user, so the robot's own normal controller smoothly guides the arm to grasp it."

---

### Scene 3: Hypothesis 1 — Two Complementary Attack Tracks (~30s)

- **On-Screen Visuals:**
  - Layout: Dual-engineer split comparison card.
  - Column 1: **Way 1: "The Attention Magnet Patch" (Lead: Priya Adlakha)**
    - Target: `Llama-2-7B` Text-to-Vision Cross-Attention Layers.
    - Method: Universal, prompt-agnostic attention sink + Differentiable `kornia` 3D perspective warp.
    - Testbed: `LIBERO-Object` benchmark suite.
  - Column 2: **Way 2: "The Auto-Feature Copy Patch" (Lead: Ameya Padwad)**
    - Target: `SigLIP + DINOv2` Vision Encoder & Projector.
    - Method: Auto-pooled top-3 attention visual ID matching + Native MuJoCo 3D coaster XMLs.
    - Testbed: `LIBERO-Spatial` benchmark suite.
- **Narration (Bella):**
  > "Under Hypothesis 1, we divided the attack track between two engineers building complementary blind patch methods that require zero prior knowledge of object coordinates. I am leading Way 1, the Attention Magnet Patch, optimizing a universal attention sink in Llama-2’s cross-attention layers using a differentiable perspective warp. Ameya is leading Way 2, the Auto-Feature Copy Patch, pooling target visual tokens directly from SigLIP and DINOv2 and rendering native 3D coasters in MuJoCo."

---

### Scene 4: Hypothesis 2 — Spatial Consistency Shielding (~30s)

- **On-Screen Visuals:**
  - Center Graphic: $3 \times 3$ Overlapping Grid Coverage on $224 \times 224$ Tabletop Workspace.
  - Detection Principle: Clean Task $\to$ Low Action Disagreement across views; Attacked Task $\to$ 1 Masked View Snaps Back to Object A.
  - Decision Logic Flow: `Batch Action Disagreement` $\to$ `Threshold \tau Confirmation (3 steps)` $\to$ `Two-Round Minority Check` $\to$ `Safe Trajectory Recovery`.
- **Narration (Bella):**
  > "Under Hypothesis 2, we introduce the Spatial Consistency Shield. On genuine tasks, masking small background regions doesn't change the robot's planned trajectory. But under an adversarial patch, masking the patch causes the planned path to snap back toward the true target. We compare naive random masking against a systematic three-by-three overlapping grid with a two-round minority verification check that isolates the uncorrupted view, recovers the safe trajectory, and completes the original task."

---

### Scene 5: Technical Failure Modes & De-risking Protocols (~25s)

- **On-Screen Visuals:**
  - 4-Quadrant De-Risking Grid:
    - 1. *Render Transfer Gap:* Domain randomization (lighting & camera jitter) during homography optimization.
    - 2. *Spatial Token Mismatch:* Dynamic RoI bounding-box token pooling instead of fixed grid indexing.
    - 3. *20 Hz Latency Constraint:* Dual-rate execution (20 Hz primary control with 2 Hz lazy shield checks).
    - 4. *Occlusion False Alarms:* Kinematic arm exclusion zone and 3-step debounce to ensure $<5\%$ episode FPR.
- **Narration (Bella):**
  > "To ensure our findings are credible in physical simulation, we conducted an exhaustive failure mode audit. We addressed the differentiable-to-native rendering transfer gap with domain randomization, resolved spatial token misalignment with dynamic region pooling, bypassed 20 Hz compute bottlenecks with lazy anomaly checks, and eliminated clean-task false alarms by shielding the robot's own arm from being masked."

---

### Scene 6: 6-Week Execution Roadmap & Renewal (~20s)

- **On-Screen Visuals:**
  - Timeline Card: Weeks 1 through 6 milestones.
  - Milestone Badges:
    - `Week 1: Setup & Clean Rollouts`
    - `Week 2: Attention & Token Hooks`
    - `Week 3: Two-Stage 3D Coasters`
    - `Week 4: Dual-Track Optimization`
    - `Week 5: Closed-Loop Bake-Off`
    - `Week 6: Shield Certification`
  - Signed Fellowship Renewal Badge: `Month 2 Extension Formalized (Oct 26 – Dec 04, 2026)`.
- **Narration (Bella):**
  > "Our six-week execution schedule is fully aligned between both tracks, taking us from baseline rollouts to closed-loop bake-offs and defense certification. With our fellowship renewal agreement signed and daily sync calls established, we are kicking off Week 1 environment setup and baseline evaluations. Thank you, and we look forward to sharing our first rollout results next week."
