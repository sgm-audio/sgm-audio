# Scott Mills — Audio Engineer & Software Engineer, Saskatchewan, Canada

## The thesis in one line

> Generative audio models do not produce a mix of instruments. They produce one sample from a
> joint probability distribution over a summed signal. No per-instrument representation exists
> at any point in generation — so per-instrument extraction, tablature transcription, and
> per-component attribution are **ill-posed**, not merely hard.

Three repositories below exist to test that claim. That is what they are for.

---

## Core work

### [stem-midi-pro](https://github.com/sgm-audio/stem-midi-pro) — source separation & audio→MIDI
Mamba-SSM guitar/bass source separation with phase-coherence preservation, plus polyphonic
audio-to-MIDI with expression detection. Reports **SI-SDR and phase coherence as first-class
outputs**, with a three-tier confidence gate (studio / draft / complex) that routes hard material
to human review rather than guessing.
`278 files · 176 Python · 18 custom CUDA kernels · Mamba-SSM · FP8 · TensorRT export path`
Production path is v1 at repo root; the Mamba-3 experimental branch is quarantined to
[`research/`](https://github.com/sgm-audio/stem-midi-pro/tree/main/research) with its rationale
documented. **Status:** architecture complete, training not yet run.

### [tab-agent-pro](https://github.com/sgm-audio/tab-agent-pro) — audio → playable tablature
Multi-engine pipeline: `SunoDetector` → Demucs → mid-side lead/rhythm split → Basic Pitch ONNX
→ dynamic-programming (Viterbi) string/fret assignment → technique heuristics → MIDI / ASCII tab
/ JSON. Eight preset profiles including a Suno-optimized path. REAPER/ReaPack integration.
`MIT · Docker · GitHub Actions CI · pre-commit (ruff, mypy) · v1.0.0`
**Status:** released and deployed for testing. On AI-generated input the target object does not exist — see
the field report.

### [hit-prompt-engine](https://github.com/sgm-audio/hit-prompt-engine) — chart history → prompt packs
Data pipeline over 50 years of Billboard Hot-100 (1976–2026): ingestion → dedup (ISRC → MBID →
fuzzy) → MusicBrainz + Spotify enrichment → librosa + PANNs "Track DNA" analysis → six-variation
prompt compiler. FastAPI + Dagster. Pydantic v2 schemas, policy separated into `config/`.
[**Docs →**](https://sgm-audio.github.io/hit-prompt-engine)
`MIT · 46 commits · 36 modules · Ruff · docs site`

### [apc-mcp](https://github.com/sgm-audio/apc-mcp) — MCP server for plugin development
Wraps CMake, ctest, clang-format, pluginval, and clap-validator into a Model Context Protocol
tool interface for JUCE / CLAP / VST3 / ARA plugin projects. Includes project scaffolding.
`MIT · published to npm · GitHub Actions release workflow`
```bash
npx -y github:sgm-audio/apc-mcp
```

### [sgm-suno-workflow](https://github.com/SGM-Studios/sgm-suno-workflow) — REAPER pipeline for Suno exports
Six-script Lua suite: ZIP import → metadata/region organizer → RMS-onset tempo mapper →
transient dynamic splitter → −14 LUFS / −1.0 dBTP loudness master → stem aligner. ReaPack
packaged.
`~100KB Lua · CHANGELOG · TEST_CASES.md · ReaPack index.xml`
**Note:** the stem aligner handles *whatever stem set actually arrives* — the built tool is the
record that promised export counts and delivered ones differ.

### [30-agents](https://github.com/sgm-audio/30-agents) — self-hosted agent orchestration
LangGraph + FastAPI + Ollama. 40 specialist agents across 6 tiers, squad pipelines, MCP bridge,
Redis sessions, ChromaDB vector memory, per-run cost reporting and audit trail.
Documented capability graph: **1,197 nodes / 2,486 edges.**
`Apache-2.0 · 35 commits · local inference = $0 marginal cost`

## Working with me

I am available for consulting and collaboration in audio ML, source separation, audio-to-MIDI,
DAW tooling, and AI-music detection and provenance. I can also provide research access to a
moderated practitioner community of ~50,000 members.

**[scott@sgmstudios.ca](mailto:scott@sgmstudios.ca)** · [sgmstudios.ca](https://sgmstudios.ca)
