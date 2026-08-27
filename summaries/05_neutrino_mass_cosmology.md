# Neutrino Mass & Cosmology: The Last Unknown in the Standard Model

**Last updated:** 2026-08-27

## 1. The Science

Neutrino oscillations prove neutrinos are massive, but oscillations only measure mass-squared differences. Cosmology provides the most sensitive probe of the **absolute neutrino mass scale** via its gravitational effect on structure formation.

### What We Know
- **Oscillation data**: Δm²₂₁ ≈ 7.5×10⁻⁵ eV², |Δm²₃₁| ≈ 2.5×10⁻³ eV²
- **Minimum Σmν**: ~0.06 eV (normal hierarchy) or ~0.10 eV (inverted hierarchy)
- **Cosmological upper bound**: Σmν < 0.12 eV (Planck 2018, 95% CL, ΛCDM)
- **DESI 2024 + Planck + DESY5**: Hints of tighter bounds, potentially ruling out inverted hierarchy
- **KATRIN**: Direct kinematic limit m_νe < 0.45 eV (2024)

### The Massive Neutrino Effect on LSS
1. **Free-streaming**: Neutrinos with v ~ c suppress P(k) on scales k > k_fs ≈ 0.018 Ωm^(1/2) (mν/eV) h/Mpc
2. **Suppression factor**: ΔP(k)/P(k) ≈ -8 Ων/Ωm ≈ -8 Σmν/(93.14 h² Ωm) (linear theory, ~5% per 0.1 eV)
3. **Scale-dependent growth factor**: Growth is suppressed below the free-streaming scale
4. **Phase shift in BAO**: Neutrinos cause a small but measurable phase shift in the BAO signal

## 2. Bridging Topics

### 2.1 Particle Physics → Cosmology
- Neutrino mass hierarchy (normal vs inverted) → Different minimum Σmν → Different LSS signatures
- Dirac vs Majorana nature → Different cosmological implications via leptogenesis
- Sterile neutrino mixing → Additional N_eff and free-streaming effects

### 2.2 Laboratory ↔ Cosmological Constraints
| Measurement | Probe | Current Bound |
|---|---|---|
| Cosmology (Planck+BAO) | Σmν | < 0.12 eV |
| KATRIN | m_νe (kinematic) | < 0.45 eV |
| 0νββ | m_ee (Majorana) | < 0.036–0.156 eV |
| Oscillations | Δm² only | Minimum Σmν ≈ 0.06 eV |

### 2.3 Neutrino Mass × Dark Energy Degeneracy
- Σmν and w₀, wₐ are strongly degenerate in CMB + BAO analyses
- Breaking the degeneracy requires galaxy surveys (DESI, Euclid, LSST) + CMB lensing
- Critical for next-generation surveys to correctly account for both

### 2.4 N_eff: Counting Relativistic Species
- Standard Model: N_eff = 3.044 (accounting for QED corrections, non-instantaneous decoupling)
- Any deviation → new physics: sterile neutrinos, dark radiation, early DE, modified gravity
- BBN + CMB provide complementary N_eff measurements at different epochs

## 3. Existing Computational Tools

### Boltzmann Solvers with Neutrino Support
| Code | Neutrino Treatment | Notes |
|---|---|---|
| **CLASS** | Exact (Boltzmann hierarchy) | Multiple mass states, N_eff |
| **CAMB** | Exact | Supports massive + massless species |
| **CONCEPT** | N-body with neutrino particles | Full nonlinear treatment |

### Emulators Including Neutrino Mass
| Emulator | Σmν Range | Other Extensions | Source |
|---|---|---|---|
| **GokuEmu** | 0–0.6 eV | w₀, wₐ, N_eff, αs | arXiv:2501.06296 |
| **EuclidEmulator2** | 0–0.15 eV | w₀, wₐ | Euclid Collaboration |
| **COMET v2** | Full range | RSD, EFT model | arXiv:2503.16160 |
| **CosmoPower** | Various | Neural net, differentiable | arXiv:2106.03846 |
| **OLÉ** | Any (online) | Auto-adapts to model | arXiv:2503.13183 |
| **νGAN** | 0–0.4 eV | 2D cosmic web generation | arXiv:2505.03936 |
| **Lyα forest emulator** | Including mν | Beyond-ΛCDM | UCL (2024) |

### Inference Frameworks
- **Cobaya** + CAMB/CLASS — standard MCMC pipeline
- **MontePython** + CLASS — alternative
- **CosmoSIS** — modular pipeline with neutrino support

## 4. MCP Server Opportunities

### Enhancement to existing servers
The `bbn-mcp-server` already handles N_eff. A CMB-focused MCP server could provide:
1. `predict_cmb_spectra(params_including_mnu)` — C_ℓ^TT, TE, EE with massive ν
2. `predict_pk(params, z, k_range)` — Matter P(k) with neutrino suppression
3. `compute_sigma8_mnu(params)` — σ₈ accounting for neutrino mass
4. `forecast_mnu_sensitivity(survey, probes)` — Fisher forecast for Σmν
5. `hierarchy_test(sigma_mnu, method)` — Can we distinguish NH from IH?

## 5. Key References

- Lesgourgues & Pastor, "Massive neutrinos and cosmology", Phys. Rept. 429 (2006) 307
- Lattanzi & Gerbino, "Status of neutrino mass and mass hierarchy determination", Front. Phys. 5 (2018) 1
- DESI Collaboration, "DESI 2024 VII: Neutrino Masses", arXiv:2404.xxxxx
- Aker et al. (KATRIN), "Direct neutrino-mass measurement", Nature Physics 18 (2022) 160
- Brinckmann et al., "The promising future of a robust cosmological neutrino mass measurement", JCAP 01 (2019) 059
