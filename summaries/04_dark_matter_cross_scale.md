# Dark Matter Cross-Scale: From Particle Interactions to Cosmic Structure

**Last updated:** 2026-10-24

## 1. The Science

Dark matter makes up ~85% of the matter in the universe. Its properties bridge particle physics (mass, interaction cross-sections, production mechanisms) and cosmology (relic abundance, structure formation, halo profiles). The key insight: **the same microphysics that determines DM production in the early universe also determines its signal in detectors and its impact on cosmic structure.**

### The WIMP Paradigm and Beyond

| DM Candidate | Mass Range | Production | Detection | Cosmo Signature |
|---|---|---|---|---|
| **WIMP** | 1 GeV – 100 TeV | Thermal freeze-out | Direct detection (nuclear recoil), LHC | CDM-like, standard halo |
| **Sterile ν (WDM)** | keV | Dodelson-Widrow, Shi-Fuller | X-ray line | Small-scale suppression |
| **Axion** | μeV – meV | Misalignment, strings | Axion haloscopes (ADMX) | CDM-like, minihalos |
| **SIDM** | Various | Various | Indirect, direct | Cored halos, diverse rotation curves |
| **Fuzzy DM** | ~10⁻²² eV | Misalignment | Lyman-α | Solitonic cores, interference |

## 2. Bridging Topics

### 2.1 Relic Abundance ↔ Direct Detection
The thermal relic cross section ⟨σv⟩ ~ 3×10⁻²⁶ cm³/s directly connects to:
- Direct detection cross section σ_SI (spin-independent) or σ_SD (spin-dependent)
- Indirect detection (annihilation in halos → γ-rays, positrons)
- Collider production cross section

**NEW (2026-09): LUX-ZEPLIN 248 keV Event**
Multiple groups have responded to a high-energy nuclear recoil event in LZ:
- Higgsino DM interpretation (arXiv:2609.01583, 2609.01590, 2609.01504) — TeV-scale MSSM neutralino
- Inelastic DM interpretation (arXiv:2609.01475) — scalar portal with mass splitting
- Fermionic DM absorption (arXiv:2609.01592)
- **NEW (2026-09-10):** Transition magnetic-dipole DM (arXiv:2609.10453) — endothermic recoil + delayed photon
- **NEW (2026-09-10):** Exothermic DM (arXiv:2609.05204) — complementary to endothermic scenarios
- **NEW (2026-09-10):** Seasonal modulation prediction (arXiv:2609.04181) — ~5 events in full LZ exposure, 3σ for δ > 374 keV. Testable by XLZD and PandaX.
- **NEW (2026-09-10):** LZ→Colliders connection (arXiv:2609.08712) — Higgsino mass splitting from DD mapped to collider signatures
- **NEW (2026-09-10):** Solar capture constraints (arXiv:2609.02775) — complements DD for Higgsino DM
This is a prime example of cross-scale physics: the same particle model determines relic abundance, collider signatures, and direct detection signals. The event count is now 8+ interpretation papers in 10 days.

**NEW (2026-10-08): LZ Theory Response Explosion**
The theory response to LZ230616 has now exceeded 50 papers in ~5 weeks. Key new developments:
- **Inelastic DM via higher-dimensional operator** (arXiv:2610.00645, Oct 1): Dimension-6 operator simultaneously determines relic abundance from freeze-out and inelastic DD signal. Self-consistent model with m_χ ~ few hundred GeV, Δm ~ 300 keV. Exemplary relic-density ↔ DD bridge.
- **Dark photon DM** (arXiv:2609.02868): Unified explanation of both LZ event and Fermi-LAT Galactic γ-ray excess via Sommerfeld-enhanced annihilation + inelastic scattering.
- **Asymmetric inelastic DM** (arXiv:2609.18564): Avoids tension between DD signal and annihilation constraints by depleting symmetric component.
- **Solar capture constraints** (arXiv:2609.21823): Rules out large ranges of elastic DM masses that would explain the LZ event.
- **Vector-like lepton interpretation** (arXiv:2609.08993): BSM lepton sector explaining high-recoil event.

**Dark Dimension DM** (arXiv:2610.04909, Oct 4): Swampland-derived KK graviton dark matter from a single micron-scale extra dimension. Relic abundance fixed by T_i ~ 1 GeV. Evolving dark dimension fits DESI DR2 without phantom crossing — apparent w evolution arises from evolving DM mass.

**NEW (2026-10-24): LZ Theory Response — Multi-Messenger Expansion**
Three more mechanisms added to the LZ 248 keV interpretation cluster this cycle:
- **Coscattering / conversion-driven freeze-out** (arXiv:2610.08648): Singlet-doublet fermion DM with ~100 keV mass splitting + light (250 MeV) dark photon. Conversion into the doublet sector sets the relic abundance (coscattering) while the same interaction is probed by the high-energy LZ recoil. Combining relic + recoil requirements selects m_χ ~ 750 GeV – 1.6 TeV. Clean numerically-specified benchmark for the relic-abundance↔DD calculator.
- **Gauged U(1)_X hidden sector with correlated GW signal** (arXiv:2610.18234): Singlet-scalar VEV simultaneously sets gauge-boson mass, pseudo-Dirac splitting for the inelastic LZ interpretation, AND the frequency/amplitude of a first-order-phase-transition gravitational-wave signal (detectable at μARES/THEIA). Third independent mechanism (after 2610.00645, 2610.08648) linking relic-abundance↔DD to a GW multi-messenger probe.
- **Halo-velocity-tail sensitivity for heavy-element complementarity** (arXiv:2610.21041): Shows the predicted signal in complementary heavy-element direct-detection experiments is highly sensitive to the assumed high-velocity tail of the DM distribution (LMC-perturbation-motivated halo models). **Actionable**: our lz-dark-sector-bridge MCP server should expose a configurable halo velocity-distribution parameter — currently missing.
- **Freeze-in via low reheating** (arXiv:2610.29543): Non-adiabatic low-reheating era boosts the coupling needed for correct freeze-in relic density, pushing some freeze-in benchmarks into direct-detection reach — extends our relic-density↔DD tooling beyond the WIMP paradigm.

**NEW (2026-09): Sub-GeV Thermal-Relic Targets**
- New targets identified via gauged U(1) extensions: L_i-L_j, B-L, B-3L_i (arXiv:2603.03444, Fermilab). Unsuppressed scattering cross sections for complex scalar and Dirac fermion DM accessible at current and future direct detection experiments.
- Scalar portal light DM with non-standard pre-BBN cosmology (arXiv:2609.02501): correlates direct detection with GW signatures (LISA/DECIGO).

**Quantitative pipeline:** Given a BSM model (e.g., MSSM, singlet-doublet, etc.):
1. Compute relic density Ωh² using **micrOMEGAs** or **MadDM**
2. Predict σ_SI, σ_SD for direct detection comparison
3. Predict ⟨σv⟩ for indirect detection
4. Compute collider signatures with **MadGraph5**

### 2.2 Small-Scale Structure Problems
- **Core-cusp problem**: CDM predicts cuspy halos, observations show cores
- **Missing satellites**: Fewer observed dwarfs than predicted
- **Too-big-to-fail**: Predicted massive subhalos not observed
- **Resolution**: Could be baryonic feedback OR new DM physics (SIDM, WDM, fuzzy DM)

### 2.3 DM Direct Detection × Nuclear Physics
- Nuclear form factors F(q) are critical for translating particle-level σ to experimental rates
- Helm form factor (standard) vs. more sophisticated nuclear structure calculations
- Spin-dependent interactions require nuclear shell model calculations
- Connection to nuclear physics codes used in neutrino physics

### 2.4 DM Annihilation × Cosmology
- DM annihilation during recombination modifies CMB (ionization history)
- Planck constrains ⟨σv⟩/m_DM via CMB anisotropies
- Cross-check with relic abundance → powerful consistency test

## 3. Existing Computational Tools

### Particle Physics / BSM

| Code | Purpose |
|---|---|
| **micrOMEGAs** | Relic density, direct/indirect detection rates for arbitrary BSM models |
| **MadDM** | DM phenomenology within MadGraph5 framework |
| **DarkSUSY** | SUSY DM calculations (relic density, detection) |
| **GAMBIT** | Global BSM fitting framework |
| **CheckMATE** | LHC recast tool for BSM searches |
| **SModelS** | Simplified model spectrum database for LHC |
| **DDCalc** | Direct detection rate calculator |
| **nulike** | Neutrino telescope likelihood for DM |
| **PPPC4DMID** | DM annihilation spectra (γ, e⁺, p̄, ν) |

### Cosmological

| Code | Purpose |
|---|---|
| **CLASS** / **CAMB** | CDM/WDM/mixed DM power spectra |
| **ExoCLASS** | CLASS extension for exotic energy injection (DM annihilation/decay) |
| **ETHOS** | Effective Theory of Structure Formation (maps particle physics → LSS) |
| **N-body codes** | Structure formation simulations (Gadget, AREPO, etc.) |
| **Colossus** | Halo model calculations in Python |
| **HMFcalc** | Halo mass function calculator |
| **halomod** | Halo model framework in Python |

### Nuclear Physics

| Code | Purpose |
|---|---|
| **TALYS** | Nuclear reaction code (also relevant for neutron capture, etc.) |
| **NuShellX** | Nuclear shell model for form factors |

## 4. MCP Server Opportunities

### Proposed: `dark-matter-mcp-server`

**Tools to expose:**
1. `compute_relic_density(model, params)` — Ωh² via micrOMEGAs-like calculation
2. `predict_direct_detection(m_dm, sigma_si, target_element)` — Expected recoil spectrum + rate
3. `predict_indirect_signal(m_dm, sigma_v, channel, target)` — γ-ray/ν flux predictions
4. `compute_halo_profile(model, mass, concentration)` — NFW, Einasto, cored profiles
5. `lss_constraints(m_dm, model_type)` — Lyman-α, satellite counts, P(k) suppression
6. `exclusion_plot(experiment, model)` — Current exclusion limits (LZ, XENONnT, DESI)

## 5. Key References

- Jungman et al., "Supersymmetric dark matter", Phys. Rept. 267 (1996) 195
- Feng, "Dark Matter Candidates from Particle Physics", ARAA 48 (2010) 495
- Hochberg et al., "New Thermal-Relic Targets for sub-GeV DM Direct Detection", arXiv:2603.03444
- Freese & Theodosopoulos, "Higgsino DM Interpretation of the LZ 248 keV Event", arXiv:2609.01583
- Cirelli et al., "Tools for model-independent bounds in direct DM searches", JCAP 10 (2013) 019
- Bélanger et al., "micrOMEGAs5.0", CPC 231 (2018) 173
- Amruth et al., "ETHOS", ApJ (2018)
- Tulin & Yu, "Dark Matter Self-interactions", Phys. Rept. 730 (2018) 1
- "Testing Dark Matter Coscattering with the High-Energy LZ Recoil", arXiv:2610.08648 (2026-10-24)
- "Signature of GW from the Hidden Sector in light of the Recent LZ Event", arXiv:2610.18234 (2026-10-24)
- "Testing the inelastic dark matter interpretation of the LZ event with heavy-element experiments" (halo velocity-tail sensitivity), arXiv:2610.21041 (2026-10-24)
- "Detectable Dark Matter Freeze-in via Low Reheating", arXiv:2610.29543 (2026-10-24)
