# Comprehensive Tool Inventory: Quarks-to-Cosmos Codes

**Last updated:** 2026-08-27

## Boltzmann Solvers (Linear Cosmology)

| Code | Language | URL | Key Features |
|---|---|---|---|
| CLASS | C/Python | github.com/lesgourg/class_public | Standard, modular, Python wrapper |
| CAMB | Fortran/Python | github.com/cmbant/CAMB | Standard, fast, well-documented |
| hi_class | C/Python | github.com/miguelzuma/hi_class_public | Horndeski gravity in CLASS |
| MGCAMB | Fortran/Python | github.com/sfu-cosmo/MGCAMB | μ-Σ modified gravity in CAMB |
| EFTCAMB | Fortran | github.com/EFTCAMB | EFT of Dark Energy |
| mochi_class | C/Python | — | Stability-by-construction parametrizations |

## BBN Codes

| Code | Language | URL | Key Features |
|---|---|---|---|
| PRyMordial | Python | github.com/vallima/PRyMordial | 63-reaction network, BSM extensions |
| PArthENoPE | Fortran/Python | — | 100+ reactions, web interface |
| AlterBBN | C | alterbbn.hepforge.org | Non-standard cosmologies |
| PRIMAT | Mathematica | — | 423 reactions, highest precision |
| ACROPOLIS | Python | github.com/... | Photodisintegration from BSM |
| linx | Python/JAX | — | Differentiable BBN |

## N-body / Structure Formation

| Code | Language | MG Support | Key Features |
|---|---|---|---|
| Gadget-4 | C++ | No (mods exist) | Tree-PM, standard workhorse |
| AREPO | C | No | Moving mesh, hydrodynamics |
| RAMSES | Fortran | ECOSMOG, ISIS | AMR, MG via extensions |
| MP-Gadget | C | No | Massive neutrino LRA |
| PySCo | Python | f(R), MOND | Fast PM, ideal for emulators |
| MG-PICOLA | C++ | f(R), DGP | Approximate, very fast |
| CONCEPT | Python | No | Relativistic species |

## Emulators

| Emulator | Parameters | Observable | URL/Ref |
|---|---|---|---|
| GokuEmu | 10 (incl Neff, αs) | P(k) | github.com/astro-YYH/GokuEmu |
| EuclidEmulator2 | 8 (incl w₀, wₐ) | P(k) | Euclid Consortium |
| FREmu | f(R) + 6 base | P(k) | arXiv:2405.05840 |
| e-MANTIS | f(R) + wCDM | HMF | arXiv:2410.05226 |
| COMET v2 | ΛCDM + mν | Galaxy P(k) | gitlab.com/aegge/comet-emu |
| CosmoPower | Various | CMB + P(k) | github.com/alessiospuriomancini |
| OLÉ | Any (online) | Any | github.com/svenguenther/OLE |
| νGAN | Σmν | 2D cosmic web | arXiv:2505.03936 |
| MG-NECOLA | f(R) + mν | Density field | arXiv:2604.19613 |

## Particle Physics / BSM

| Code | Purpose | URL |
|---|---|---|
| MadGraph5_aMC@NLO | Monte Carlo event generation | launchpad.net/mg5amcnlo |
| micrOMEGAs | DM relic density, detection rates | lapth.cnrs.fr/micromegas |
| MadDM | DM in MadGraph framework | — |
| DarkSUSY | SUSY DM phenomenology | darksusy.hepforge.org |
| GAMBIT | Global BSM fitting | gambit.hepforge.org |
| CheckMATE | LHC recast | checkmate.hepforge.org |
| SModelS | Simplified model spectra | smodels.github.io |
| FeynRules | Lagrangian → UFO model | feynrules.irmp.ucl.ac.be |
| SARAH | BSM model generator | sarah.hepforge.org |
| MARLEY | Low-energy ν event generator | — |
| GLoBES | ν oscillation experiment sim | — |
| PPPC4DMID | DM annihilation spectra | — |

## Inference / MCMC

| Framework | Base Solver | URL |
|---|---|---|
| Cobaya | CAMB or CLASS | cobaya.readthedocs.io |
| MontePython | CLASS | baudren.github.io/montepython |
| CosmoMC | CAMB | cosmologist.info/cosmomc |
| CosmoSIS | Modular | bitbucket.org/joezuntz/cosmosis |

## MCP Servers (Existing)

| Server | Domain | Port | Source |
|---|---|---|---|
| bbn-mcp-server | BBN | 8003 | nesar |
| spectra-mcp-server | Spectroscopy | 8000 | HEP-KE |
| gaia-mcp-server | Astrometry | 8001 | HEP-KE |
| ParticlePhysics-MCP | PDG data | — | uzerone |
| hydroemu-mcp-server | Hydro sims | — | nesar-ai-assistant |
