# Research Frontiers — Exploration & Project Selection Review

**Fellow:** Priya Adlakha  
**Collaborator:** Ameya Padwad  
**Mentors:** Prof. Nik Bear Brown & Dev Shah  
**Affiliation:** Humanitarians AI (Iacon Optimus Fellowship Program)  
**Date:** October 26–30, 2026 (Week 7 Fellowship Milestone)  
**Project Track:** Physical AI / Vision–Language–Action (VLA) Safety & Robustness  

---

## 1. Executive Summary: What We Are Achieving in Simple Terms

### The One-Liner
> *"We are proving that a small tabletop sticker can quietly trick a robot into grabbing the wrong object by hijacking how its AI perceives the scene—and we are building a real-time safety shield that catches and stops this trick without needing to retrain the robot."*

### The Layperson Paragraph
> *"Today’s advanced robot foundation models (Vision–Language–Action models like OpenVLA) connect cameras directly to robot motors, translating live visual frames and natural language instructions into physical movements. Most previous adversarial attacks on robots try to brute-force the motor outputs at every millisecond—an approach that quickly breaks down in the real world because the robot's own movement changes the camera angle. Instead, our research shows that an attacker can place a small printed coaster or texture on the table that tricks the robot's visual perception into swapping the identities of two objects. When told 'Pick up the apple,' the robot genuinely believes the decoy object (e.g., a mug or hazard) is the apple, and its own internal controller smoothly guides the arm to grasp it. To defend against this, we introduce the 'Spatial Consistency Shield': by systematically masking out small parts of the camera view in real time and measuring whether the robot's intended path abruptly snaps back to the original object, our system detects perception hijacks and recovers the safe task on the fly—requiring zero retraining of the robot foundation model."*

---

## 2. Comprehensive Exploration Across the 12 Research Verticals

As part of the fellowship renewal process and the transition from Month 1 (Autonomous Pure Decision Models) to Month 2, we conducted a systematic evaluation of all 12 broad research verticals opened under the **Humanitarians AI Research Frontiers** initiative. Below is the detailed analysis, candidate problems explored, and evaluation matrix that led to our final project selection.

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                        12 RESEARCH FRONTIERS EVALUATION MATRIX                         │
├───────────────────────────────┬──────────────────────────────────┬─────────────────────┤
│ Research Frontier Vertical    │ Candidate Problems Investigated   │ Verdict & Priority  │
├───────────────────────────────┼──────────────────────────────────┼─────────────────────┤
│ 1. Intelligence Measurement   │ VLA closed-loop robustness bench │ High (Integrated)   │
│ 2. Learning Environments      │ Dynamic physical sim testbeds    │ High (Integrated)   │
│ 3. Learning Algorithms        │ Offline RL vs. Action Chunking   │ Medium (Deprioritized)│
│ 4. Cognitive Architectures    │ Dual-system VLA fast/slow loops │ Medium (Future scope)│
│ 5. Security & Exploitation    │ Semantic steering & spatial shield│ Highest (Selected)  │
│ 6. Data & Knowledge           │ Cross-embodiment trajectory store│ Medium (Deprioritized)│
│ 7. Compute & Execution        │ Real-time 20Hz VLA quantization  │ High (Shield eng.)  │
│ 8. Formal Proof & Verification│ Reachability shields for 7-DoF   │ High (Theoretical)  │
│ 9. Causal Science             │ Counterfactual visual token cuts │ High (Integrated)   │
│ 10. Prediction & World Modeling│ Action-conditioned video models │ Medium (Compute-heavy)│
│ 11. Inverse Design & Invention│ Tabletop 3D adversarial textures │ High (Integrated)   │
│ 12. Sensing & Perception      │ Multi-view cross-attention leaks │ High (Integrated)   │
└───────────────────────────────┴──────────────────────────────────┴─────────────────────┘
```

---

### Vertical 1: Intelligence Measurement
* **Scope:** Find capabilities we cannot reliably measure. Invent evaluation methods, create benchmarks, test competing systems, and expose fundamental limitations.
* **Problems Explored:**
  1. *Closed-Loop Grounding vs. Open-Loop Accuracy:* Current VLA benchmarks (e.g., LIBERO, SimplerEnv) measure task success percentage, but fail to measure whether the robot completed the task because it genuinely understood the visual-semantic instruction or because it followed spatial/distance heuristics.
  2. *Kinematic Naturalness Metrics:* Existing robustness evaluations lack quantitative metrics for trajectory stealthiness (e.g., jerk, velocity profile variance, and step-to-step action entropy).
  3. *Measuring Perception–Action Decoupling:* How to measure when a model's internal representations are hijacked even if the immediate motor action appears momentarily correct.
* **Assessment:** Vital. While not chosen as an isolated vertical, its core methodologies (closed-loop trajectory consistency, kinematic jerk evaluation, and failure characterization) were directly integrated into our VLA benchmark design.

---

### Vertical 2: Learning Environments
* **Scope:** Identify behaviors worth teaching. Build environments, rewards, simulations, and challenges. Experiment with what produces better learning.
* **Problems Explored:**
  1. *Sim-to-Real Friction & Contact Physics Gaps:* Simulators like MuJoCo often reward policy exploits that rely on unrealistic contact friction or rigid body collision glitches.
  2. *Two-Object Tabletop Manipulation Suites:* Setting up controlled, multi-object manipulation benchmarks that test semantic disambiguation (e.g., picking Object A in the presence of hazardous Decoy B).
  3. *Adversarial Simulation Testbeds:* Developing simulated environments that dynamically introduce physical adversarial artifacts (3D coasters, textured surfaces) without manual XML hacking.
* **Assessment:** Highly actionable. We adopted the standardized LIBERO suite (`LIBERO-Object` and `LIBERO-Spatial`) on Franka Emika Panda arms as our primary simulation testbed to eliminate custom world-building artifacts.

---

### Vertical 3: Learning Algorithms
* **Scope:** Investigate where existing training methods fail. Invent new optimization techniques, learning rules, or adaptation mechanisms.
* **Problems Explored:**
  1. *Fine-tuning Stability in Vision–Language–Action Transformers:* Investigating why full fine-tuning of 7B VLAs degrades general vision-language capabilities (catastrophic forgetting).
  2. *Action-Chunking Optimization:* Comparing discrete autoregressive token prediction (OpenVLA) against continuous flow-matching / diffusion policy action chunks (Octo, ACT).
  3. *Reinforcement Learning from Physical Feedback (RLPF):* Training robot policies with negative penalties for spatial inconsistency.
* **Assessment:** Deprioritized for Month 2. Fine-tuning 7B models requires substantial multi-node GPU clusters (A100/H100 pools) that create training bottlenecks. Our chosen project focuses on frozen-weight evaluation and runtime defense, bypassing training bottlenecks entirely.

---

### Vertical 4: Cognitive Architectures
* **Scope:** Explore how intelligence should be structured. Experiment with reasoning, memory, planning, and decision-making architectures.
* **Problems Explored:**
  1. *Dual-System Fast/Slow VLA Control:* Pairing a slow high-level reasoning VLM (e.g., GPT-4V / Gemini) for goal decomposition with a fast 20 Hz low-level policy for motor actuation.
  2. *Episodic Spatial Memory for Robotic Manipulation:* Building 3D scene graphs that persist across camera occlusions.
  3. *Runtime Self-Correction Loops:* Enabling robots to detect slip or misalignment and replan without resetting the episode.
* **Assessment:** Promising for long-term research, but introduces complex latency overheads that obscure the core safety questions of foundation model perception.

---

### Vertical 5: Security & Exploitation (SELECTED PRIMARY VERTICAL)
* **Scope:** Investigate weaknesses in real systems. Discover and safely reproduce vulnerabilities in authorized targets, identify new classes of failures, and develop defenses.
* **Why This Vertical Won:**
  - Physical AI and robotics foundation models represent the frontier where digital intelligence touches the physical world. A software jailbreak outputs harmful text; a physical AI vulnerability commands a steel robot arm to swing a knife or grasp a hazardous chemical container.
  - Prior work in VLA security (TMA, UPA, EDPA) treats robot attacks like image classification attacks—optimizing patches to maximize motor action error. This is fragile: as soon as the robot moves 2 centimeters, camera perspective shifts, breaking the attack.
  - **The Novel Breakthrough Territory:** Moving from *motor-forcing attacks* to *semantic identity hijacking*, and moving from *passive input smoothing* to *active runtime spatial consistency shielding*.
* **Problems Formulated:**
  1. *Stealthy Semantic Hijacking:* Can a small 3D tabletop coaster make a VLA believe Object B is Object A without modifying user instructions?
  2. *Certified Runtime Shielding in Closed-Loop Systems:* Can we adapt input masking (PatchCleanser principles) to multi-step dynamic robot trajectories without retraining?

---

### Vertical 6: Data & Knowledge
* **Scope:** Find valuable information that is missing, inaccessible, or unreliable. Develop methods to discover, generate, organize, verify, and connect knowledge.
* **Problems Explored:**
  1. *Cross-Embodiment Demonstration Mining:* Normalizing trajectory datasets across different robot kinematics (Franka, UR5, Aloha, Google Robot).
  2. *Semantic Annotation of Failure Modes:* Automatically indexing where and why demonstration trajectories fail.
* **Assessment:** Essential for large-scale data teams, but secondary to fundamental physical AI safety and runtime vulnerability research.

---

### Vertical 7: Compute & Execution
* **Scope:** Identify fundamental bottlenecks in computation. Experiment with compilers, inference, distributed systems, hardware utilization, and execution architectures.
* **Problems Explored:**
  1. *Real-time 20 Hz Latency Constraints on 7B VLAs:* Running a 7B parameter vision-language model at 20 Hz requires sub-50ms inference. Running $K=9$ parallel masked views creates a severe compute bottleneck.
  2. *Asynchronous Action Execution & Chunking:* Decoupling high-frequency motor execution from lower-frequency spatial safety checks.
  3. *Quantized VLA Inference (AWQ / BitsAndBytes 4-bit):* Measuring whether 4-bit weight quantization degrades trajectory smoothness or increases adversarial susceptibility.
* **Assessment:** Integrated as a critical engineering component of our Hypothesis 2 defense architecture (lazy evaluation and batched GPU inference).

---

### Vertical 8: Formal Proof & Verification
* **Scope:** Find mathematical, software, or engineering claims that are difficult to guarantee. Formalize them, construct proofs or counterexamples, and develop automatic verification methods.
* **Problems Explored:**
  1. *Reachability Analysis for 7-DoF Manipulators:* Using Control Barrier Functions (CBFs) to formally prove that the robot end-effector cannot enter forbidden geometric volumes.
  2. *Certifiable Patch Robustness in OpenVLA:* Proving that if a patch occupies at most area $\delta$, at least one mask in a systematic grid will achieve 100% occlusion.
* **Assessment:** Provides the theoretical backbone for Method 2 in Hypothesis 2 (Systematic $3 \times 3$ Overlapping Grid Masking inspired by *PatchCleanser*).

---

### Vertical 9: Causal Science
* **Scope:** Find phenomena we can observe but cannot explain. Develop hypotheses, identify underlying causes, design interventions, and experimentally establish what changes outcomes.
* **Problems Explored:**
  1. *Causal Attribution of VLA Decisions:* Does OpenVLA grasp an object because of its visual appearance, its spatial coordinate relative to the base, or language attention?
  2. *Intervention via Token Dropping:* By selectively masking visual tokens or attention heads, we can establish the causal graph linking prompt nouns ("apple") to visual tokens and subsequent motor actions.
* **Assessment:** Directly utilized in our cross-attention analysis (Engineer 1 track) to prove whether the patch causes trajectory redirection by manipulating attention weights or visual token embeddings.

---

### Vertical 10: Prediction & World Modeling
* **Scope:** Pick complex systems we cannot accurately predict. Build models, forecast unseen outcomes, test against reality, and improve accuracy and uncertainty estimates.
* **Problems Explored:**
  1. *Action-Conditioned Video Generation:* Predicting future camera frames given current motor commands to verify safety before physical execution.
  2. *Dynamics Discrepancy Detection:* Comparing predicted physics states with observed MuJoCo states to detect external manipulation.
* **Assessment:** Requires massive generative video backbones (Sora/Cosmos-style) that exceed local and cloud fellowship compute budgets for Month 2.

---

### Vertical 11: Inverse Design & Invention
* **Scope:** Start with a desired property rather than an existing solution. Search enormous design spaces, generate candidates, simulate their behavior, and discover better designs.
* **Problems Explored:**
  1. *Inverse Optimization of 3D Textures:* Generating continuous texture maps that optimize a target loss across arbitrary 3D camera projections.
  2. *Differentiable Tabletop Warping:* Inversely optimizing a planar $50 \times 50$ patch using homography matrices to satisfy feature-level invariance.
* **Assessment:** Integrated directly into Stage A of our experimental pipeline (Two-stage patch optimization).

---

### Vertical 12: Sensing & Perception
* **Scope:** Find things in the physical world that are difficult to observe or measure. Explore sensor signals, imaging, microscopy, and new measurement techniques.
* **Problems Explored:**
  1. *Multi-Camera Feature Fusion in Robotics:* Analyzing how eye-in-hand cameras interact with static overhead cameras during adversarial perturbation.
  2. *Simulated Sensor Artifacts:* Evaluating how lighting shifts, motion blur, and sensor noise affect VLA action predictability.
* **Assessment:** Reserved as Phase 2 future scope (Real-World Camera Noise and sensor degradation).

---

## 3. Final Project Selection & Fellowship Alignment

### The Chosen Intersection
We selected the intersection of **Vertical 5 (Security & Exploitation)**, **Vertical 1 (Intelligence Measurement)**, and **Vertical 8 (Formal Verification & Defense)**:

> **Project Title:** *Stealthy Semantic Perception Hijacking & Runtime Spatial Consistency Shielding in Vision–Language–Action (VLA) Models*

### Key Strategic Decisions Made During Week 7 Review:
1. **Division of Labor (Two-Engineer Parallel Execution):**
   - **Engineer 1 (Priya Adlakha / Track 1):** Owns "The Attention Magnet Patch" (Cross-Attention Hijacking in `Llama-2-7B`), differentiable perspective warping, and `LIBERO-Object` task suites.
   - **Engineer 2 (Ameya Padwad / Track 2):** Owns "The Auto-Feature Copy Patch" (Vision Encoder Shortcut in `SigLIP + DINOv2`), native MuJoCo 3D coaster XML integration, and `LIBERO-Spatial` task suites.
2. **De-risking Protocol Established:**
   - Addressed the differentiable-to-native rendering transfer gap via domain randomization.
   - Resolved spatial token correspondence via dynamic bounding-box token pooling rather than fixed grid matching.
   - Resolved real-time 20 Hz compute bottlenecks through lazy/anomaly-triggered safety checks.
   - Constrained grid masking to exclude the robot arm kinematics to eliminate clean-task false alarms.
3. **Approval & Mentorship Handoff:**
   - Reviewed daily with Ameya Padwad (3:00 PM PST connects, 2.5 hours total across Week 7).
   - Structured for formal sign-off from Dev Shah and Prof. Nik Bear Brown.
   - Formalized within the fellowship renewal agreement for Month 2.
