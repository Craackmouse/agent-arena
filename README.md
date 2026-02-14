# Agent Arena

## Project Idea

A comprehensive benchmarking platform where minimal coding agents compete head-to-head on real-world tasks. Focus on evaluating **Pi agent** (from OpenClaw) against other lightweight, CLI-based coding agents using standardized benchmarks and metrics.

**Tagline**: *Where minimal coding agents compete on real-world benchmarks*

## The Contenders

### Primary Agents Under Test

1. **Pi Agent** (OpenClaw/badlogic)
   - Minimal terminal coding agent in TypeScript
   - 4 core tools: read, write, edit, bash
   - Multiple modes: interactive, JSON, RPC, SDK
   - Extensible via TypeScript, Skills, Prompt Templates
   - **GitHub**: https://github.com/badlogic/pi-mono

2. **Aider**
   - Git-native, CLI-based coding assistant
   - Structured refactoring across multiple files
   - Terminal-first workflow
   - **Philosophy**: Similar minimalism to Pi
   - **GitHub**: https://github.com/paul-gauthier/aider

3. **Mini-SWE-Agent**
   - Ultra-minimal: 100 lines of Python
   - Achieves 65% on SWE-bench Verified
   - Proof that minimal can be powerful
   - **GitHub**: https://github.com/SWE-agent/SWE-agent

### Optional Extended Comparisons
- **Cline** (VS Code-based, open-source)
- **OpenHands** (production-ready, high benchmark scores)
- **GitHub Copilot** (industry baseline)

## Benchmark Suite

### Core Benchmarks

#### 1. SWE-bench Verified ⭐ PRIMARY
- **Description**: 500 human-annotated real GitHub issues
- **Task**: Generate patches that resolve described problems
- **Verification**: Execution-based testing
- **Why**: Gold standard for real-world coding ability
- **Current SOTA**: Claude Opus 4.5 at 80.9%
- **Link**: https://www.swebench.com/

#### 2. Terminal-Bench 2.0
- **Description**: 89 curated command-line tasks
- **Tasks**: Compiling code, training models, server setup
- **Why**: Perfect for CLI-focused agents like Pi and Aider
- **Current Performance**: Best agents ~60% overall, 16% on hard tasks
- **Link**: https://www.tbench.ai/
- **GitHub**: https://github.com/laude-institute/terminal-bench

#### 3. HumanEval
- **Description**: 164 handwritten Python function problems
- **Task**: Write functions that pass test cases
- **Why**: Standard baseline for basic coding capabilities
- **Focus**: Functional correctness in single-file contexts
- **Link**: https://github.com/openai/human-eval

### Optional Advanced Benchmarks
- **MBPP**: 974 entry-level programming tasks
- **RepoQA**: Repository-level code understanding
- **SWE-bench Lite**: Faster subset for iteration
- **MultiPL-E**: Multi-language capability (18+ languages)

## Evaluation Metrics

### Performance Dimensions

1. **Accuracy** 🎯
   - Task completion rate
   - Pass@1, Pass@5, Pass@10
   - Correctness of generated code

2. **Efficiency** ⚡
   - Time per task (seconds/minutes)
   - Tokens consumed per task
   - API calls made

3. **Cost** 💰
   - Total API cost per benchmark
   - Cost per successful completion
   - Token efficiency (cost/accuracy ratio)

4. **Robustness** 🛡️
   - Performance on "hard" subset
   - Error handling and recovery
   - Edge case handling

5. **Usability** 🎨
   - Setup complexity (time to first run)
   - Configuration difficulty
   - Learning curve
   - Documentation quality

6. **Scalability** 📈
   - Performance on large codebases
   - Multi-file task handling
   - Repository-level operations

## Architecture

```
agent-arena/
├── benchmarks/
│   ├── swe-bench/
│   │   ├── runner.py
│   │   ├── evaluator.py
│   │   └── results/
│   ├── terminal-bench/
│   │   ├── runner.py
│   │   ├── evaluator.py
│   │   └── results/
│   └── humaneval/
│       ├── runner.py
│       ├── evaluator.py
│       └── results/
├── agents/
│   ├── pi/
│   │   ├── setup.sh
│   │   └── wrapper.py
│   ├── aider/
│   │   ├── setup.sh
│   │   └── wrapper.py
│   └── mini-swe/
│       ├── setup.sh
│       └── wrapper.py
├── evaluation/
│   ├── metrics.py
│   ├── analyzer.py
│   └── visualizer.py
├── results/
│   ├── raw/
│   ├── processed/
│   └── reports/
└── dashboard/
    ├── index.html
    └── charts.js
```

## Methodology

### Evaluation Protocol

1. **Isolated Environments**: Each agent runs in clean Docker container
2. **Consistent Hardware**: Same compute resources for all agents
3. **Fair API Access**: Same LLM models and API keys where applicable
4. **Reproducibility**: Seed random states, log all interactions
5. **Multiple Runs**: 3-5 runs per task to account for variance
6. **Timeout Limits**: Consistent time limits across all agents

### Scoring System

- **Overall Score**: Weighted average across benchmarks
  - SWE-bench Verified: 50%
  - Terminal-Bench 2.0: 30%
  - HumanEval: 20%

- **Efficiency Score**: (Accuracy / Cost) × Speed_factor
- **Value Score**: Accuracy × Usability / Cost

## Reference Projects & Prior Art

### Benchmark Frameworks
- [AI Agent Benchmark Compendium](https://github.com/philschmid/ai-agent-benchmark-compendium) - 50+ benchmarks
- [AgentBench](https://github.com/THUDM/AgentBench) - Multi-environment LLM-as-Agent benchmark
- [WebArena](https://github.com/ServiceNow/webarena-verified) - Web-based autonomous agent tasks

### Agent Comparison Resources
- [Faros AI: Best AI Coding Agents for 2026](https://www.faros.ai/blog/best-ai-coding-agents-2026)
- [8 Benchmarks Shaping Next-Gen AI Agents](https://tessl.io/blog/8-benchmarks-shaping-the-next-generation-of-ai-agents/)
- [Rethinking Coding Agent Benchmarks](https://medium.com/@steph.jarmak/rethinking-coding-agent-benchmarks-5cde3c696e4a)

### OpenClaw & Pi
- [Pi: The Minimal Agent Within OpenClaw](https://lucumr.pocoo.org/2026/1/31/pi/)
- [Building an Opinionated Minimal Coding Agent](https://mariozechner.at/posts/2025-11-30-pi-coding-agent/)

### Research Papers
- [ACE-Bench: Benchmarking Agentic Coding](https://openreview.net/forum?id=41xrZ3uGuI)
- [SWE-bench: Can Language Models Resolve Real-World GitHub Issues?](https://arxiv.org/abs/2310.06770)

## Tech Stack (Planned)

- **Runner**: Python 3.11+
- **Containerization**: Docker / Docker Compose
- **Data Storage**: SQLite for results, JSON for logs
- **Visualization**: Plotly / D3.js
- **Dashboard**: React / Svelte
- **CI/CD**: GitHub Actions for automated runs

## Features Roadmap

### Phase 1: Foundation
- [ ] Setup benchmark environments (SWE-bench, Terminal-Bench, HumanEval)
- [ ] Agent wrapper implementations (Pi, Aider, Mini-SWE)
- [ ] Basic evaluation metrics
- [ ] Result storage system

### Phase 2: Evaluation
- [ ] Run full benchmark suite
- [ ] Collect performance metrics
- [ ] Cost tracking implementation
- [ ] Statistical analysis

### Phase 3: Reporting
- [ ] Interactive dashboard
- [ ] Automated report generation
- [ ] Comparison visualizations
- [ ] Export to CSV/PDF

### Phase 4: Advanced
- [ ] Custom benchmark creation
- [ ] Real-time monitoring
- [ ] Agent configuration tuning
- [ ] Community submissions

## Integration Opportunities

- **Container Isolation**: Use [claude-container-sandbox](../claude-container-sandbox) for safe agent execution
- **Progress Monitoring**: Send results to [agent-telegram-monitor](../agent-telegram-monitor)
- **Multi-Agent Testing**: Integrate with [multi-agent-orchestrator](../multi-agent-orchestrator) for parallel runs

## Contributing

Want to add a new agent or benchmark? See CONTRIBUTING.md (coming soon)

## Status

🚧 **In Planning** - Repository initialized, designing benchmark suite and evaluation methodology.

## License

MIT
