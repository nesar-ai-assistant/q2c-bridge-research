# Q2C Bridge Research

**Quarks-to-Cosmos: Bridging Particle Physics and Cosmology with AI**

Systematic knowledge base and executable tools for multi-scale physics bridging topics — mapping the connections between particle physics parameters and cosmological observables through AI/ML.

## Topics

1. **Big Bang Nucleosynthesis (BBN)** — Primordial abundances, neutron lifetime puzzle, dark radiation
2. **Sterile Neutrinos** — keV-MeV dark matter, cosmological constraints, direct detection
3. **Modified Gravity / Dark Energy** — f(R), Horndeski, w0waCDM, screening mechanisms
4. **Dark Matter Cross-Scale** — WIMP phenomenology, direct detection ↔ relic abundance
5. **Neutrino Mass & Cosmology** — Active neutrino mass from LSS, N_eff constraints
6. **AI Agents for Multi-Scale Physics** — ArgoLOOM, MCP servers, multi-agent orchestration

## Repository Structure

```
summaries/              Topic-by-topic research summaries with references
  01_bbn_bridging.md
  02_sterile_neutrinos.md
  03_modified_gravity_dark_energy.md
  04_dark_matter_cross_scale.md
  05_neutrino_mass_cosmology.md
  06_ai_agents_multiscale_physics.md
tools/                  Inventory of existing codes and their capabilities
  tool_inventory.md
SCOPE_ASSESSMENT.md     Analysis of what can be built as MCP servers
LICENSE                 MIT
```

## Companion MCP Servers

The research in this knowledge base has led to working MCP server implementations:

| Server | Repo | Status |
|--------|------|--------|
| BBN (PRyMordial) | [nesar/bbn-mcp-server](https://github.com/nesar/bbn-mcp-server) | ✅ Working |
| Sterile ν + BBN bridge | [nesar-ai-assistant/sterile-nu-bbn-server](https://github.com/nesar-ai-assistant/sterile-nu-bbn-server) | ✅ Working + CI |
| Hydro emulators (CosmoHydro) | [nesar-ai-assistant/hydroemu-mcp-server](https://github.com/nesar-ai-assistant/hydroemu-mcp-server) | ✅ Working + CI |
| Spectra (CLASS) | [HEP-KE/spectra-mcp-server](https://github.com/HEP-KE/spectra-mcp-server) | ✅ Working |
| Cosmic emulators | [HEP-KE/cosmic_emulator_server](https://github.com/HEP-KE/cosmic_emulator_server) | ✅ Working |
| Lattice QCD | [nesar/lattice-mcp-server](https://github.com/nesar/lattice-mcp-server) | ✅ Working |

## Related Work

- [ArgoLOOM](https://github.com/ML4HEP-Theory/ArgoLOOM) (arXiv:2510.02426) — Multi-agent AI for cosmology
- [cosmohydro_emu](https://github.com/nesar/cosmohydro_emu) — Python package for CosmoHydro GP emulators
- [HEP-KE org](https://github.com/HEP-KE) — HEP Knowledge Extraction

## License

MIT
