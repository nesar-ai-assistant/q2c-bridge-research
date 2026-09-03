# Big Bang Nucleosynthesis: Bridging Nuclear/Particle Physics and Cosmology

**Last updated:** 2026-09-03

## 1. The Science

Between ~1 second and ~20 minutes after the Big Bang, the universe ran a nuclear reactor. The primordial abundances of light elements (⁴He, D, ³He, ⁷Li) depend on:

- **Baryon density** Ω_b h² — how much ordinary matter exists
- **Extra relativistic species** ΔN_eff — any light particle beyond the 3 SM neutrinos (dark radiation, sterile states, axions)
- **Neutron lifetime** τ_n — sets the n/p ratio at weak freeze-out; currently shows a ~10s discrepancy ("bottle vs beam" puzzle)
- **Nuclear reaction rates** — especially d(p,γ)³He, measured by LUNA collaboration

### Key Open Problems

1. **Lithium Problem**: BBN predicts ⁷Li/H ~3× higher than the observed Spite plateau. Status: unsolved since 1982.
2. **Bottle vs Beam Neutron Lifetime**: τ_bottle ≈ 878.4s vs τ_beam ≈ 888.0s. A ~10s discrepancy with >4σ significance.
3. **Dark Radiation / N_eff**: Planck measures N_eff = 2.99 ± 0.17. BBN is sensitive to any extra relativistic species at T ~ 1 MeV.
4. **Concordance**: BBN + CMB agree on Ω_b h² — a spectacular success that constrains new physics at t ~ 1s.

## 2. The Particle↔Cosmology Bridge

BBN is the premier example of particle/nuclear physics constraining cosmology:

| Particle/Nuclear Input | Cosmological Observable |
|---|---|
| Neutron lifetime τ_n | ⁴He abundance Y_p |
| ΔN_eff (sterile ν, axions, dark photons) | Y_p, D/H |
| Nuclear cross sections (LUNA, n_TOF) | All primordial abundances |
| Baryon asymmetry η | D/H, ⁷Li/H |
| BSM particles decaying during BBN | Non-standard abundance patterns |
| Grand unification (varying α, G_N) | Shifted freeze-out, modified rates |

### Specific Bridging Questions

- **Sterile neutrinos**: If ΔN_eff > 0 from a sterile ν, how does that shift Y_p and D/H? What mass/mixing parameters are allowed?
- **Early Dark Energy**: Does EDE at T ~ MeV modify the expansion rate enough to shift BBN predictions? (arXiv:2512.11163)
- **Varying constants**: If α or G_N changed since BBN, primordial abundances shift — constrains GUT-scale physics.
- **Probing unification scenarios**: PRyMordial extended to predict BBN abundances under varying fundamental constants (arXiv: Phys. Rev. D 2024).

## 3. Existing Computational Tools

### BBN Codes

| Code | Language | Features | Status |
|---|---|---|---|
| **PRyMordial** | Python | Full 63-reaction network, BSM extensions, precision N_eff | Active, GPL-3.0 |
| **PArthENoPE** | Fortran/Python | 100+ reactions, error propagation, web interface | Active, ~96 citations |
| **AlterBBN** | C | Fast, includes non-standard cosmologies, decaying particles | Active |
| **PRIMAT** | Mathematica | High-precision nuclear network, 423 reactions | Active |
| **ACROPOLIS** | Python | Photodisintegration from late-decaying BSM particles | Active |
| **linx** | Python/JAX | Differentiable BBN, gradient-based inference | Recent (2024) |

### Related Cosmological Codes

| Code | Purpose |
|---|---|
| **CLASS** / **CAMB** | CMB power spectra, Ω_b h² from CMB |
| **Cobaya** / **MontePython** | MCMC inference framework |
| **CosmoMC** | Parameter estimation |

### MCP Server (Existing)

- **[bbn-mcp-server](https://github.com/nesar/bbn-mcp-server)** — Built on PRyMordial. Tools: `compute_abundances`, `scan_baryon_density`, `scan_neff`, `scan_neutron_lifetime`, `fit_baryon_density`, plus plotting tools. Port 8003.

## 4. What's Missing / Opportunities for MCP Development

1. **BBN + CMB joint analysis server**: Connect bbn-mcp-server with a CMB server (CLASS-based) for joint Ω_b h² inference
2. **BSM BBN extensions**: Add tools for decaying particle scenarios (ACROPOLIS integration), varying constants
3. **Nuclear rate uncertainty propagation**: Monte Carlo over LUNA/n_TOF rate uncertainties
4. **Gradient-based inference**: Leverage linx (JAX-based differentiable BBN) for fast parameter estimation

## 5. Key References

- Burns, Tait & Valli, "PRyMordial: the first three minutes", EPJC 84 (2024) 86 [arXiv:2307.07061]
- Burns et al., "Inside the Black Box of BBN: Sensitivity Atlas", arXiv:2603.22414 (77-parameter atlas using PRyMordial + LBT He-4 data)
- Dreyer & Martins, "Probing Unification Scenarios with BBN", arXiv:2604.04870 (PRyMordial + GUT varying couplings)
- Schöneberg, "What could an emerging BBN discrepancy be hinting at?", arXiv:2607.20635 (~3.1σ D/H tension with PRIMAT; vEDE proposed)
- "BBN & WIMP Freeze-Out as Probes of Yukawa Cosmology", arXiv:2608.09390 (BBN + DM relic abundance as complementary MG probes)
- Gariazzo et al., "PArthENoPE revolutions", CPC 271 (2022) 108205
- Pitrou et al., "PRIMAT", Physics Reports 754 (2018) 1-66
- Hufnagel et al., "ACROPOLIS", JCAP 11 (2021) 032
- Giovanetti et al., "Insights for Early Dark Energy with BBN", arXiv:2512.11163
- Fields, "Big Bang Nucleosynthesis", Ann. Rev. Nucl. Part. Sci. 61 (2011) 47
- Cyburt et al., "Big Bang Nucleosynthesis: Present status", Rev. Mod. Phys. 88 (2016) 015004
