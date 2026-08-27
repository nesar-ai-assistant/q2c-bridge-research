# Q2C Bridging Topics: Scope Assessment & Publication Viability

**Date:** 2026-08-27  
**Status:** Pre-implementation analysis  
**Goal:** Determine which bridging directions are (a) close to observations, (b) have genuine novelty potential, and (c) are suitable for MCP-server-based quantitative tools.

---

## Direction 1+2: BBN + Sterile Neutrinos — ✅ STRONG CANDIDATE

### The Physics Case

The BBN ↔ sterile neutrino bridge is one of the tightest particle↔cosmology connections because:

1. **eV-scale sterile neutrinos** affect BBN directly via ΔN_eff (extra thermalized species). Primordial D/H and Yp constrain this parameter to ΔN_eff < 0.4 (95% CL).

2. **keV-scale sterile neutrinos** are warm dark matter candidates. Their mass and mixing angle are jointly constrained by:
   - X-ray line searches (NuSTAR, XMM-Newton, Chandra — the 3.5 keV line debate)
   - Lyman-α forest (free-streaming length → structure formation)
   - BBN (lifetime and decay products inject energy)

3. **MeV-to-GeV scale (heavy neutral leptons)** are constrained by BBN through their production and decay during nucleosynthesis. Recent work (Chen & Zhang, PRD 111, 2025) shows the *complete* BBN exclusion portrait using PRyMordial — this is an active, publication-generating area.

### Observational Accessibility — EXCELLENT

| Observable | Current Data | Near-Future |
|---|---|---|
| Primordial D/H | ±1.2% (Cooke+ 2018) | JWST + 30m-class telescopes |
| Primordial Yp | ±0.4% (Aver+ 2021) | New emission-line surveys |
| ΔN_eff from CMB | Planck: 2.99 ± 0.17 | CMB-S4: σ(N_eff) ≈ 0.03 |
| X-ray decay line | NuSTAR limits | XRISM (operating), Athena, LEM |
| SBL oscillations | BEST anomaly, STEREO null | SBN Program at FNAL (ongoing) |
| BBN+CMB joint | DESI+Planck (2024-25) | DESI full + Euclid + CMB-S4 |

### What Exists Already

- **BBNet** (Zhang+ 2025, PRD 114): A neural network emulator for primordial abundances (Yp, D/H) trained on PArthENoPE and AlterBBN. Achieves 10⁴× speedup. Published in PRD.
- **LINX** (Giovanetti+ 2024): JAX-based differentiable BBN code.
- **PRyMordial** (Pitrou+ 2024): Python BBN code with BSM portal.
- **SBI for sterile neutrinos** (Villarreal+ 2025): ML-based Feldman-Cousins for sterile ν global fits. Published in MLST.
- **Your bbn-mcp-server**: MCP wrapper around BBN computation.

### Gap / Novelty Opportunity

**BBNet** emulates standard+ΔN_eff+stiff-EoS BBN. But nobody has built:
1. A **joint BBN + sterile-ν production** tool that takes (m_s, sin²2θ, mechanism) → {ΔN_eff, Yp, D/H} in one call, self-consistently computing the production (Dodelson-Widrow or Shi-Fuller) AND the BBN impact.
2. An **MCP server** that chains this with CMB constraint checking (Planck N_eff posterior) and X-ray line predictions.
3. A tool that answers: *"Given BEST's preferred sterile ν parameters, what primordial abundances does this predict, and is it consistent with observed D/H?"*

This is genuinely new — current codes are separate silos. The MCP architecture makes them interoperable. **Publication-worthy: YES** (tool paper + physics application).

### Verdict: ✅ PROCEED — First implementation target

---

## Direction 3: Modified Gravity / Dark Energy — ⚠️ NEEDS REFRAMING

### The Honest Assessment

The current summary (03) is indeed shallow on the particle↔cosmology bridge. Here's why:

**The traditional MG/DE landscape (hi_class, MGCAMB, EuclidEmulator2, etc.) is purely gravitational.** These codes modify the Friedmann equations or perturbation theory but do not connect to any particle physics Lagrangian in a calculable way. There is no "nuclear reaction network" or "cross section" on the other side — just effective parameters (μ, Σ, c_s²).

### But: A Real Bridge IS Emerging (June 2026!)

**Bashyam, Gurrola, Florez & Rodriguez (arXiv:2606.27441, June 2026)** — "Collider Probes of Dark Energy Microphysics" — construct an EFT where:
- A k-essence dark energy scalar φ couples to a BSM pseudoscalar mediator via derivative interactions
- The mediator (in a 2HDM+a model) can be produced at the LHC
- The **invisible decay width** of the mediator depends on the dark energy sound speed c_s²
- LHC resonance measurements can therefore **probe dark energy microphysics**

This is genuinely new (submitted June 2026) and opens the door to collider↔cosmology bridging for DE. The ATLAS collaboration has already searched for light scalar particles contributing to cosmic acceleration (CERN Courier 2026).

### Connection to Direction 4 (Dark Matter)

**Yes, they connect — but through dark sector mediators, not directly.** The 2HDM+a model is *also* the leading simplified model for WIMP dark matter at colliders. The same pseudoscalar mediator that talks to dark energy in Bashyam+ also mediates DM annihilation. So:

- LZ/XENONnT exclusions on σ_SI constrain the mediator coupling
- Relic density (Ω_DM h²) constrains the annihilation cross section through the same mediator  
- The DE sound speed c_s² introduces a *third* observable via the invisible width

**The bridge**: Collider data (LHC mediator searches) → constrains couplings → simultaneously predicts relic density AND dark energy microphysics. This is the "Thermal Relic Encyclopedia" (arXiv:2512.03133) approach applied to dark energy.

### But: Is This Accessible to Observations?

| Channel | Status | Practical? |
|---|---|---|
| LHC mediator resonance | HL-LHC from 2030 (LS3 started June 2026) | ⚠️ Future |
| DE equation of state w | DESI w₀ = −0.55 ± 0.21, wₐ = −1.32 (+0.62/−0.51) | ✅ Now |
| DE sound speed c_s² | Unconstrained by cosmological obs | ❌ Very hard |
| DM direct detection | LZ 4.2 t·yr, XENONnT 3.1 t·yr | ✅ Now |
| DM relic density | Planck Ω_DM h² = 0.120 ± 0.001 | ✅ Now |

**Problem:** The c_s² connection that makes this genuinely novel requires collider data that won't exist until after HL-LHC starts taking data (~2030). The pure MG cosmological side (μ, Σ from Euclid/DESI) doesn't connect to particle physics without additional theoretical assumptions.

### Verdict: ⚠️ DEPRIORITIZE for now — monitor the Bashyam+ developments

The physics is fascinating but the key observable (collider measurement of c_s² via invisible width) isn't available yet. We could build the theoretical prediction tools (given a 2HDM+a model: predict Γ_inv(c_s²), relic density, direct detection σ) but it's more of a "what to look for" paper than a "here's what the data says" paper.

**If you want to pursue this later**: it would be a 2HDM+a MCP server that jointly predicts collider signatures + relic density + DE sound speed constraints.

---

## Direction 4: Dark Matter Cross-Scale — ⚠️ ACTIVE BUT SATURATED

### Honest Assessment

The WIMP miracle ↔ direct detection ↔ collider triangle is one of the most heavily studied areas in particle physics. The landscape:

- **"The Waning of the WIMP: Endgame?"** (Arcadi+ 2024, EPJC 85:152) — comprehensive review covering all WIMP models, combining LZ + XENONnT + Fermi-LAT + LHC. They explicitly show the relic density isocontour on every (m_DM, σ) plane.
- **"Thermal Relic Encyclopedia"** (arXiv:2512.03133) — systematic catalog of ALL scalar/fermionic DM + spin-0/1 mediator combinations coupled to quarks, with matrix elements, cross sections, relic densities.
- **"WIMPs Below the Radar"** (Arcadi & Profumo, JHEP 2025) — identifies blind spots below the neutrino floor.
- **"Charting WIMP Territories at the Neutrino Floor"** (PRD 2025) — roadmap for next-gen experiments.
- Tools: **micrOMEGAs**, **MadDM**, **DarkSUSY**, **GAMBIT** — all mature, well-maintained, heavily used.

### The Gap

The codes exist and the physics is well-mapped. Building an MCP server that wraps micrOMEGAs to compute relic density + direct detection σ would be **useful but not novel**. The physics insights are incremental at this point — unless we connect it to a specific BSM scenario that hasn't been explored (e.g., the 2HDM+a ↔ DE connection above).

### Verdict: ⚠️ NOT A STANDALONE DIRECTION — fold into Direction 3 if pursued

---

## Direction 5: Neutrino Mass & Cosmology — ❌ WELL-STUDIED, LOW NOVELTY FOR MCP

### Thorough Assessment (as requested)

**You're right to be skeptical.** Here's the evidence:

#### What Already Exists — It's Crowded

1. **GokuEmu / GokuNEmu** (2025): 10-parameter emulator for the nonlinear matter power spectrum, covering Σmν, N_eff, w₀, wₐ, α_s. Published, public, state-of-the-art.
2. **νGAN** (Ramachandra+ — that's you! — ApJ 2025): GAN emulator for 2D cosmic web with massive neutrinos. Up to 1.2 eV.
3. **SYREN-NEW** (Shao+ 2024): Symbolic regression formulae for P(k) with massive neutrinos + DE.
4. **Cosmic-Eν** (Upadhye+ 2024, MNRAS): Emulator for the neutrino power spectrum Δ²_ν(k).
5. **fast-νf** (Upadhye 2025): Fast multi-fluid linear response for neutrino clustering.
6. **CosmoPower** (Spurio Mancini+ 2022): Neural emulator for CMB/matter P(k) including mν.
7. **EuclidEmulator2**: 8-parameter emulator including Σmν.
8. **BBNet** (2025): Covers the BBN side of neutrino constraints.

#### The Observational Situation

- **DESI BAO + Planck**: Σmν < 0.05 eV (2σ) — this is *below the inverted hierarchy floor* of 0.1 eV!
- **Tension**: Cosmological upper bound appears inconsistent with oscillation lower bound (Σmν > 0.06 eV). This is being actively debated (lensing anomaly, Planck PR4 likelihoods, see Notari 2024).
- **Euclid forecast**: σ(Σmν) ≈ 23 meV with Planck, potentially 4σ detection with CMB-S4.
- The field is extremely active — July 2025 paper "Cosmological neutrino mass: a frequentist overview in light of DESI" (arXiv:2507.12401).

#### Why an MCP Server Adds Little

The emulators already exist and are better than anything we could build from scratch. The parameter inference pipelines (MontePython, Cobaya, CosmoMC) are mature. Wrapping them in an MCP server is a software exercise, not a physics contribution.

**The one genuine gap**: Nobody has built a joint BBN + CMB + LSS neutrino constraint tool that self-consistently combines primordial abundance predictions with power spectrum effects. But that's really a BBN server problem (Direction 1), not a standalone Direction 5.

### Verdict: ❌ DO NOT PURSUE AS STANDALONE — the physics insights would be incremental

The emulators are published, the constraints are being derived by dedicated collaborations (Euclid, DESI, Planck), and the novelty of "yet another emulator" is low. **Exception**: if the BBN + sterile ν server (Direction 1+2) naturally extends to active neutrino mass constraints via the N_eff connection, that's fine — but as a feature, not a separate project.

---

## Direction 6: AI Agents / Architecture — ⏸️ PARKED (per your request)

Not pursuing agentic architecture. Focus on physics.

---

## RECOMMENDED IMPLEMENTATION PLAN

### Phase 1 (Now): BBN + Sterile Neutrino Bridge Server

**Name**: `sterile-nu-bbn-server` (or extend `bbn-mcp-server`)

**Physics scope**:
- Input: (m_sterile, sin²2θ, production_mechanism, n_active_flavors)
- Compute: sterile ν production (DW/SF), thermalization, ΔN_eff
- Compute: BBN with modified N_eff → Yp, D/H, ⁷Li/H
- Compare: against observed primordial abundances
- Constrain: exclusion contours in (m_s, sin²2θ) plane
- Bonus: X-ray decay line prediction (keV sterile ν)

**Novel contribution**:
- First self-consistent, end-to-end tool from particle physics input to cosmological observables
- MCP server enabling agent-driven exploration of parameter space
- Joint BBN + X-ray + Ly-α constraint visualization
- Publication: tool paper with physics application (e.g., "What does BEST's preferred sterile ν imply for BBN?")

### Phase 2 (Later): 2HDM+a Mediator ↔ DM + DE Server

Only if Phase 1 succeeds and HL-LHC data motivates it.

### Phase 3 (Optional): Active Neutrino Mass Joint Constraint

As a feature of the Phase 1 server, not standalone.

---

## Summary Table

| Direction | Observational Access | Novelty of MCP Server | Existing Competition | **Verdict** |
|---|---|---|---|---|
| 1+2: BBN + Sterile ν | ✅ Excellent | ✅ High (no joint tool) | Medium (BBNet, PRyMordial) | **✅ GO** |
| 3: MG/DE | ⚠️ Cosmological yes, particle no | ⚠️ Low until HL-LHC | High (hi_class, MGCAMB) | **⚠️ WAIT** |
| 4: DM cross-scale | ✅ LZ/XENONnT | ❌ Low (micrOMEGAs exists) | Very high | **❌ FOLD IN** |
| 5: ν mass cosmo | ✅ DESI/Euclid | ❌ Low (GokuEmu, νGAN exist) | Very high | **❌ SKIP** |
| 6: AI agents | N/A | N/A | N/A | **⏸️ PARKED** |
