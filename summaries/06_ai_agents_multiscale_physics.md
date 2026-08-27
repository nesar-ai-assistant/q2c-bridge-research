# AI Agents for Multi-Scale Physics: ArgoLOOM, MCP Servers, and the Quarks2Cosmos Pipeline

**Last updated:** 2026-08-27

## 1. The Vision

The fundamental physics landscape spans scales from femtometers (nuclear/particle physics) to gigaparsecs (cosmology). Computational tools at each scale are mature but siloed. **The opportunity**: AI agents can orchestrate cross-scale calculations, routing particle physics inputs through cosmological codes and back, enabling systematic exploration of BSM parameter spaces that would otherwise require expert knowledge of multiple code ecosystems.

## 2. Existing Multi-Scale AI Systems

### 2.1 ArgoLOOM (arXiv:2510.02426)

**Architecture**: Orchestrator + domain-specific toolkits + knowledge base (FAISS/RAG)
- **Cosmology**: CLASS (Boltzmann solver → CMB, P(k), LSS)
- **Collider Physics**: MadGraph5_aMC@NLO (Monte Carlo event generation)
- **Nuclear/QCD**: DIS kinematics mapping, detector smearing, PDFs
- **Knowledge Base**: arXiv papers indexed via sentence-transformers + FAISS

**Strengths**: 
- Cross-frontier calculations in a single dialogue
- Sterile neutrino as demonstrator BSM case study
- Reproducibility via runcards, seeds, citations

**Limitations**:
- Runs on local workstations only
- OpenAI API dependency (GPT backbone)
- No MCP protocol — custom tool-calling scheme
- Limited to CLASS + MG5 (no BBN, no emulators, no N-body)

### 2.2 HEP-KE MCP Server Ecosystem

| Server | Port | Domain | Tools |
|---|---|---|---|
| **spectra-mcp-server** | 8000 | Spectroscopy / stellar | HEP-KE |
| **gaia-mcp-server** | 8001 | Astrometry / Gaia data | HEP-KE |
| **lattice-mcp-server** | 8002 | Lattice QCD | HEP-KE |
| **bbn-mcp-server** | 8003 | Big Bang Nucleosynthesis | nesar |
| **multiagent-client-demo** | — | Multi-agent client | HEP-KE |

**Design pattern** (from spectra-mcp-server):
- Every tool returns `{status, files, message, metadata}` (ArtifactResult)
- Arrays move between tools as **file paths**, never through agent context
- Streamable HTTP transport (`--transport streamable-http`)

### 2.3 Multi-Agent System for Cosmological Parameter Analysis (arXiv:2412.00431)
- Automated MCMC pipeline with AI agents
- Agents decide which datasets to use, configure Cobaya runs, interpret results
- Proof of concept for AI-assisted cosmological inference

### 2.4 The AI Cosmologist (arXiv:2504.03424)
- Agentic system for automated data analysis in cosmology
- Focus on CMB data processing and parameter extraction

### 2.5 ParticlePhysics-MCP-Server
- PDG data access via MCP (github.com/uzerone)
- Particle properties, decay modes, natural-language queries
- Useful building block for cross-scale calculations

## 3. Proposed Q2C MCP Architecture

```
┌─────────────────────────────────────────────────────────┐
│                  Q2C ORCHESTRATOR                       │
│  (AI Agent with access to all servers below)            │
│  Input: "What BBN constraints exist on f(R) gravity?"   │
│  → Routes to BBN + MG servers, synthesizes results      │
└───┬──────┬──────┬──────┬──────┬──────┬──────────────────┘
    │      │      │      │      │      │
    ▼      ▼      ▼      ▼      ▼      ▼
┌──────┐┌──────┐┌──────┐┌──────┐┌──────┐┌──────┐
│ BBN  ││Sterile││  MG  ││  DM  ││ CMB  ││Collid│
│:8003 ││ ν    ││:8004 ││:8005 ││:8006 ││er    │
│      ││:8007 ││      ││      ││      ││:8008 │
└──────┘└──────┘└──────┘└──────┘└──────┘└──────┘
  PRyM    CLASS   hi_class  micrO   CLASS   MG5
  ordial  +custom +MGCAMB   MEGAs   /CAMB   /pylhe
```

### Design Principles
1. **Each server is self-contained**: Works standalone, no inter-server dependencies
2. **ArtifactResult convention**: All tools return `{status, files, message, metadata}`
3. **File-based data transfer**: Large arrays as CSV/HDF5, referenced by path
4. **Cross-server queries via orchestrator**: Agent chains tool calls across servers
5. **Human-readable outputs**: Every computation produces a plot + narrative summary
6. **Tests + CI/CD**: pytest, GitHub Actions, reproducibility checks

## 4. Implementation Priority

Based on scientific impact, tool maturity, and publication potential:

| Priority | Topic | MCP Server | Why |
|---|---|---|---|
| **1** | BBN (existing) | bbn-mcp-server | Already built, extend with BSM scenarios |
| **2** | Sterile ν bridge | sterile-nu-mcp-server | Natural extension of BBN, connects to N_eff, CLASS, ArgoLOOM |
| **3** | Modified gravity | mg-mcp-server | DESI interest, hi_class/MGCAMB mature |
| **4** | Neutrino mass | Extend CMB/LSS server | GokuEmu / COMET integration |
| **5** | Dark matter | dm-mcp-server | micrOMEGAs integration, broadest scope |

## 5. Key References

- Bakshi et al., "ArgoLOOM", arXiv:2510.02426
- Laverick et al., "Multi-Agent System for Cosmological Parameter Analysis", arXiv:2412.00431
- Moss, "The AI Cosmologist I", arXiv:2504.03424
- Tam, Grosset, Banesh, Ramachandra et al., "InferA: smart assistant for cosmological ensemble data", SC Workshops '25
- Coburn, Wells, Ramachandra, "A Multi-Agent System for Automated Cosmological Data Analysis", in prep (2025)
- Model Context Protocol specification: https://modelcontextprotocol.io
