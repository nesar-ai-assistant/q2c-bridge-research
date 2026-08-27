# Sterile Neutrinos: The Particle↔Cosmology Bridge

**Last updated:** 2026-08-27

## 1. The Science

Sterile neutrinos are hypothetical neutral fermions that interact only through gravity and mixing with active neutrinos. They appear naturally in extensions of the Standard Model (e.g., seesaw mechanism) and are compelling because they simultaneously address:

- **Neutrino mass generation** (Type-I seesaw)
- **Dark matter** (keV-scale sterile ν)
- **Baryon asymmetry** (leptogenesis via GeV-scale sterile ν)
- **Short-baseline anomalies** (eV-scale, though increasingly disfavored)

### Mass Windows and Their Physics

| Mass Scale | Particle Physics Role | Cosmological Signature |
|---|---|---|
| **eV scale** | Reactor/accelerator anomalies | Extra N_eff, modified CMB, slight LSS suppression |
| **keV scale** | Warm dark matter candidate | Small-scale structure suppression, Lyman-α forest, X-ray line |
| **MeV–GeV scale** | Leptogenesis, heavy neutral leptons | Displaced vertices at LHC, modified BBN |
| **TeV+ scale** | Seesaw mechanism | Collider signatures, no direct cosmo effect |

## 2. Bridging Topics

### 2.1 eV-Scale Sterile ν + Cosmology (Most Active)

**Key recent results:**
- Cosmological search after DESI 2024 (arXiv:2501.10785): In w₀wₐCDM+Sterile, m_eff = 0.50⁺⁰·³³₋₀.₂₇ eV at ~2σ with CBS+DESY3 data. N_eff = 3.076⁺⁰·⁰¹¹₋₀.₀₁₇.
- The dark energy model strongly affects sterile ν constraints — highlighting the degeneracy between DE dynamics and neutrino physics.
- ΛCDM+Sterile alone is disfavored (ln B = -6.66 vs ΛCDM).

**Tools needed:** CAMB/CLASS with sterile ν, Cobaya/MontePython for MCMC, DESI + Planck + DES likelihoods.

### 2.2 keV Sterile ν Dark Matter

**Key recent results:**
- Lyα forest bounds via neutrino self-interactions (arXiv:2602.17821): Using modified CLASS with neural network emulator for mixing angle. Strongest observational constraints from eBOSS Lyα EFT + PRIYA likelihoods.
- Shi-Fuller mechanism revival (arXiv:2507.18752): Large lepton asymmetries L ≳ 0.5 open viable parameter space for m_s ≳ 10 keV with sin²(2θ) ≲ 10⁻¹⁴. Compatible with BBN and X-ray (NuSTAR, INTEGRAL/SPI) constraints.

**Tools needed:** Modified CLASS/CAMB for non-thermal distributions, N-body simulations with WDM transfer functions, X-ray spectrum fitting codes.

### 2.3 Sterile ν in N-body Simulations

**Key recent work:**
- N-body simulations with eV-scale sterile ν (arXiv:2501.16908): Modified Gadget-2 with linear response approach (LRA). Suppression up to 40% in P(k) for m_eff = 0.8 eV. Fitting formulae for power spectrum, halo mass function, pairwise velocity deviations.
- νGAN (arXiv:2505.03936): GAN-based emulator for neutrino mass effects on cosmic web, ~5% accuracy on P(k) to k ~ 0.5 h/Mpc.

### 2.4 Connection to Collider Physics (ArgoLOOM)

The ArgoLOOM paper (arXiv:2510.02426) explicitly uses sterile neutrinos as the BSM case study for cross-frontier analysis:
- Cosmological effects via CLASS (N_eff, LSS)
- Collider signatures via MadGraph5 (displaced vertices, heavy neutral leptons)
- Nuclear/DIS effects via kinematic mapping codes

## 3. Existing Computational Tools

### Particle Physics Side

| Code | Purpose |
|---|---|
| **MadGraph5_aMC@NLO** | Monte Carlo event generation for sterile ν production at colliders |
| **HNL tools (various)** | Heavy neutral lepton phenomenology, decay rates, branching ratios |
| **MARLEY** | Low-energy neutrino event generator for nuclear targets |
| **GLoBES** | Neutrino oscillation experiment simulation |
| **ParticlePhysics-MCP-Server** | PDG data lookup via MCP (github.com/uzerone) |

### Cosmology Side

| Code | Purpose |
|---|---|
| **CLASS** (with sterile ν module) | CMB + LSS power spectra with extra species |
| **CAMB** (with N_eff) | Same, alternative solver |
| **Gadget-2/4** (modified) | N-body with sterile ν via LRA |
| **MP-Gadget** | N-body with improved massive neutrino treatment |
| **Goku suite / GokuEmu** | 10-parameter emulator including N_eff (arXiv:2501.06296) |
| **COMET v2** | Galaxy clustering emulator with massive neutrinos (arXiv:2503.16160) |
| **CosmoPower** | Neural network emulator for CMB/LSS spectra |
| **OLÉ** | Online Learning Emulator for cosmological inference (arXiv:2503.13183) |

### BBN Connection

| Code | Purpose |
|---|---|
| **PRyMordial** | BBN with arbitrary ΔN_eff from sterile ν |
| **AlterBBN** | BBN with non-standard cosmologies |

## 4. MCP Server Opportunities

### Proposed: `sterile-neutrino-mcp-server`

**Tools to expose:**
1. `compute_sterile_relic_density(mass, mixing_angle, mechanism)` — Dodelson-Widrow, Shi-Fuller, etc.
2. `compute_neff_contribution(mass, mixing_angle, T_decoupling)` — ΔN_eff from thermalization
3. `predict_xray_flux(mass, mixing_angle, distance, exposure)` — Radiative decay signal for X-ray searches
4. `compute_lss_suppression(mass, delta_neff)` — Matter power spectrum suppression factor
5. `bbn_constraints(mass, mixing_angle)` — BBN-allowed parameter space
6. `collider_reach(mass, mixing_angle, experiment)` — LHC/FCC-ee sensitivity

**Cross-server queries:**
- BBN server: "What ΔN_eff is allowed by D/H?" → sterile ν server: "What mass/mixing gives that ΔN_eff?"
- CMB server: "What's the current Planck bound on N_eff?" → sterile ν server: "Map to mixing angle exclusion"

## 5. Key References

- Boyarsky et al., "Sterile neutrino Dark Matter", Prog. Part. Nucl. Phys. 104 (2019) 1 [arXiv:1807.07938]
- Adhikari et al., "A White Paper on keV sterile neutrino DM", JCAP 01 (2017) 025
- Gao, Zhang et al., "Cosmological search for sterile neutrinos after DESI 2024", arXiv:2501.10785
- Parashari et al., "Lyα forest bounds on sterile ν via self-interactions", arXiv:2602.17821
- "Return of the Lepton Number: Shi-Fuller Mechanism", arXiv:2507.18752
- Zhang et al., "eV sterile ν in N-body simulations", arXiv:2501.16908
- ArgoLOOM paper: Bakshi et al., arXiv:2510.02426
