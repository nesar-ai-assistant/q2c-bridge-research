# Modified Gravity & Dark Energy: Bridging Fundamental Theory and Large-Scale Structure

**Last updated:** 2026-08-27

## 1. The Science

The accelerated expansion of the universe (discovered 1998) can be explained by either:
- A **cosmological constant** Λ (simplest, fine-tuning problem)
- **Dynamical dark energy** — a new field with time-varying equation of state w(a)
- **Modified gravity** — alterations to GR on cosmological scales

DESI 2024 BAO data hints at w₀wₐCDM being preferred over ΛCDM at ~3.9σ (with DESY5 + Planck + ACT), reinvigorating interest in both dynamical DE and modified gravity.

### Key Frameworks

| Model Class | Examples | Screening | Key Observable |
|---|---|---|---|
| **f(R) gravity** | Hu-Sawicki | Chameleon | Enhanced P(k) at k > 0.1 h/Mpc, modified HMF |
| **Horndeski / scalar-tensor** | Galileon, K-essence, Brans-Dicke | Various | Scale-dependent growth, ISW effect |
| **DGP braneworld** | nDGP | Vainshtein | Modified growth rate f(z) |
| **w₀wₐCDM** | CPL parameterization | N/A | BAO, distances, growth |
| **μ-Σ parameterization** | Phenomenological | N/A | Metric potentials vs matter |

## 2. Bridging Topics

### 2.1 Particle Physics Origins of Dark Energy
- Quintessence fields connect to high-energy physics (axion-like particles, moduli)
- f(R) gravity can be seen as a scalar field theory (scalaron) with specific potential
- Screening mechanisms have analogs in particle physics (symmetron ↔ symmetry breaking)

### 2.2 Modified Gravity ↔ Neutrino Mass Degeneracy
- f(R) gravity and massive neutrinos produce degenerate effects on P(k) at k ~ 0.1-1 h/Mpc (Baldi et al. 2014)
- Breaking this degeneracy requires multi-probe analysis (CMB lensing + galaxy clustering + cluster counts)
- MG-NECOLA (arXiv:2604.19613): Field-level emulator for f(R) + massive neutrino cosmologies

### 2.3 BBN Constraints on Dark Energy
- Early Dark Energy models are constrained by BBN: modified expansion rate at T ~ MeV shifts light element abundances (arXiv:2512.11163)
- Fisher analysis shows D/H and Y_p are most sensitive to EDE at T ~ 0.01-1 MeV

### 2.4 Dark Energy ↔ Dark Matter
- Some unified models have DE and DM as aspects of a single field
- Interacting DE-DM models modify both expansion history and structure growth

## 3. Existing Computational Tools

### Linear Boltzmann Solvers (Modified Gravity)

| Code | Base | MG Models | Status |
|---|---|---|---|
| **MGCAMB** | CAMB | μ-Σ, f(R), symmetron, dilaton, DES param. | Active, nonlinear extension via ReACT (2024) |
| **hi_class** | CLASS | Full Horndeski, EFT of DE | Active v3.0, used by DESI 2024 for MG constraints |
| **EFTCAMB / H-EFTCAMB** | CAMB | EFT of DE, Horndeski (Python-wrapped) | Active |
| **mochi_class** | CLASS | Stability-by-construction parametrizations | Active |
| **MGCLASS II** | CLASS | μ-Σ parameterization | Active |
| **ISiTGR** | CAMB | μ-Σ, growth index | Active |

### N-body Codes for Modified Gravity

| Code | Base | MG Models | Notes |
|---|---|---|---|
| **ECOSMOG** | RAMSES | f(R), DGP, symmetron | AMR, most accurate |
| **MG-GADGET** | Gadget | f(R) | Tree-PM |
| **ISIS** | RAMSES | f(R), symmetron, DGP | AMR |
| **PySCo** | Python | f(R), MOND, time-dep G | Fast PM, ~1 CPU-hr for 512³, ideal for emulators |
| **MG-PICOLA** | COLA | f(R), DGP | Approximate, fast |
| **RayMOND** | RAMSES | MOND | AMR |

### Emulators

| Emulator | Parameters | Observable | Accuracy |
|---|---|---|---|
| **FREmu** | f(R) + ΛCDM params | Nonlinear P(k) | Trained on Quijote-MG |
| **e-MANTIS** | f(R) + wCDM | Halo mass function | Percent-level |
| **GokuEmu** | 10-param (w₀, wₐ, Σmν, Neff, αs + 5 base) | P(k) to k~10 h/Mpc | 1-5% |
| **COMET v2** | ΛCDM + mν | Galaxy P(k) multipoles (EFT/VDG) | Sub-percent |
| **MG-NECOLA** | f(R) + massive ν | Field-level density | ~1% P(k) to k~1 h/Mpc |
| **cGAN f(R)→ΛCDM** | f(R) | Full density field | arXiv:2407.15934 |
| **EuclidEmulator2** | 8-param (w₀, wₐ, mν) | P(k) | Percent-level |
| **CosmoPower** | Various | CMB + P(k) (neural net) | Fast, differentiable |
| **OLÉ** | Any (online learning) | Any observable | 30-350× speedup, auto-adapts |

### Inference Frameworks

| Framework | Description |
|---|---|
| **Cobaya** | Modular Bayesian inference (MCMC, nested sampling) |
| **MontePython** | MCMC for CLASS-based analyses |
| **CosmoSIS** | Modular cosmological parameter estimation |
| **Cosmosis** | Pipeline-based inference |

## 4. MCP Server Opportunities

### Proposed: `modified-gravity-mcp-server`

**Tools to expose:**
1. `compute_mg_power_spectrum(model, params)` — P(k) for f(R), nDGP, Horndeski via hi_class/MGCAMB
2. `compute_growth_rate(model, params, z)` — f(z)σ₈(z) predictions
3. `compare_with_data(model, params, dataset)` — Quick χ² against DESI BAO, DES cosmic shear
4. `screening_scale(model, params, environment)` — Where does screening kick in?
5. `mg_bbn_constraints(model, params)` — Cross-check with BBN bounds (connect to bbn-mcp-server)
6. `emulate_fR_pk(fR0, n, omega_m, ...)` — Fast FREmu predictions

### Cross-server Architecture
```
CMB-MCP (CLASS) ←→ MG-MCP (hi_class) ←→ BBN-MCP (PRyMordial)
         ↕                    ↕
    LSS-MCP (emulators)   Collider-MCP (MadGraph)
```

## 5. Key References

- DESI Collaboration, "DESI 2024 VI: Constraints on Models of Dark Energy", arXiv:2404.03002
- Wang et al., "Extending MGCAMB tests of gravity to nonlinear scales", JCAP 11 (2024) 003
- Bellini et al., "hi_class: Horndeski in CLASS", JCAP 02 (2020) 008
- Hu & Sawicki, "Models of f(R) Cosmic Acceleration", PRD 76 (2007) 064004
- Bai & Xia, "FREmu: Power Spectrum Emulator for f(R)", arXiv:2405.05840
- Saadeh et al., "MG-NECOLA", arXiv:2604.19613
- PySCo: Music et al., A&A (2025), arXiv:2410.xxxxx
- Giovanetti et al., "Insights for EDE with BBN", arXiv:2512.11163
- Yang et al., "GokuEmu", arXiv:2501.06296
