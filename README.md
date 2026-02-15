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

### Expected Strengths by Agent

| Agent | SWE-bench 💻 | WebArena 🌐 | AgentBench 🎯 | Notes |
|-------|--------------|-------------|---------------|-------|
| **Pi** | ⭐⭐⭐ | ⭐ | ⭐⭐⭐ | Strong at coding + OS tasks, may lack browser |
| **Aider** | ⭐⭐⭐ | ⭐ | ⭐⭐ | Git-native coder, CLI-focused |
| **Mini-SWE** | ⭐⭐ | ❌ | ⭐ | Minimalist, SWE-bench specialist |
| **Cline** | ⭐⭐⭐ | ⭐⭐ | ⭐⭐ | VS Code integration, broader tools |
| **OpenHands** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | Production agent, browser support |

*Ratings based on agent design, not benchmark results (TBD)*

## Benchmark Suite

Our benchmark suite tests three critical dimensions of agent capability:

### Core Benchmarks (The Essential 3)

#### 1. 💻 SWE-bench Verified - CODING BENCHMARK
**What it tests:** Real-world software engineering ability

- **Description**: 500 human-verified GitHub issues from actual open-source projects
- **Task**: Agent reads issue → generates code fix → must pass existing tests
- **Environments**: Python repositories (Django, Flask, scikit-learn, etc.)
- **Why**: Best predictor of real coding ability - not toy problems, actual bugs
- **Current SOTA**: Claude Opus 4.5 at 80.9% | IBM CUGA at 61.7%
- **Human baseline**: ~78%
- **Links**: [Leaderboard](https://www.swebench.com/) | [GitHub](https://github.com/princeton-nlp/SWE-bench)

**What it covers:**
- ✅ Multi-file changes across large codebases
- ✅ Understanding existing code architecture
- ✅ Bug fixing with test-driven verification
- ✅ Working with real-world dependencies

**What it misses:**
- ❌ New feature development (only bug fixes)
- ❌ Non-Python languages
- ❌ UI/frontend work

---

#### 2. 🌐 WebArena - BROWSER MODE BENCHMARK
**What it tests:** Web navigation and task completion ability

- **Description**: 812 realistic web tasks across 4 simulated domains
- **Domains**:
  - 🛒 E-commerce (shopping site)
  - 💬 Social forum (Reddit-like)
  - 💻 Code collaboration (GitLab-like)
  - 📝 Content management (WordPress-like)
- **Task Examples**:
  - "Find cheapest laptop with 16GB RAM and add to cart"
  - "Reply to the top post in tech forum"
  - "Create issue for bug #123 and assign to user X"
- **Why**: Tests if agents can navigate real web interfaces like humans do
- **Current SOTA**: IBM CUGA at 61.7% (Feb 2025)
- **Human baseline**: ~78% (17% gap remaining)
- **Links**: [Website](https://webarena.dev/) | [GitHub](https://github.com/web-arena-x/webarena) | [Paper](https://arxiv.org/abs/2307.13854)

**What it covers:**
- ✅ Web UI understanding (buttons, forms, links)
- ✅ Multi-step workflows (search → filter → action)
- ✅ Goal-oriented task completion
- ✅ Realistic website interactions

**What it misses:**
- ❌ Non-web tasks
- ❌ Mobile interfaces
- ❌ Complex JavaScript-heavy SPAs

---

#### 3. 🎯 AgentBench - REAL-WORLD MULTI-DOMAIN BENCHMARK
**What it tests:** General agent capability across diverse environments

- **Description**: 8 different environments testing adaptability and reasoning
- **Environments**:
  1. 💻 **Operating System** - File manipulation, bash commands, system tasks
  2. 🗄️ **Database** - SQL queries, data operations
  3. 🕸️ **Knowledge Graph** - Complex relationship queries
  4. 🎮 **Digital Card Game** - Strategic planning and decision-making
  5. 🧩 **Lateral Thinking Puzzles** - Creative problem solving
  6. 🏠 **House-Holding** - Physical world task simulation
  7. 🛒 **Web Shopping** - E-commerce workflows
  8. 🌐 **Web Browsing** - General web navigation
- **Why**: Tests if agents can generalize across domains (not just specialists)
- **Current SOTA**: GPT-4.1 at 62% Action Completion | Gemini 2.5 Flash at 94% Tool Selection
- **Best Open-Source**: Kimi K2 at 53% ($0.039/session)
- **Links**: [GitHub](https://github.com/THUDM/AgentBench) | [Paper](https://arxiv.org/abs/2308.03688) | [Leaderboard](https://huggingface.co/spaces/galileo-ai/agent-leaderboard)

**What it covers:**
- ✅ Cross-domain adaptability
- ✅ Planning and multi-step reasoning
- ✅ Tool use and integration
- ✅ OS-level operations (perfect for CLI agents!)

**What it misses:**
- ❌ Deep domain expertise
- ❌ Long-running projects (>30 min)
- ❌ Creative/generative work

---

### Why These 3?

| Benchmark | Tests | Best For | Time/Task |
|-----------|-------|----------|-----------|
| **SWE-bench** | Can it code? | Coding agents (Pi, Aider) | ~10 min |
| **WebArena** | Can it use the web? | Browser-enabled agents | ~5 min |
| **AgentBench** | Can it adapt to anything? | General-purpose agents | ~3 min |

Together they cover: **Code + Web + Real-world tasks = Complete agent evaluation**

---

### 🔍 What Each Benchmark Uniquely Tests

**SWE-bench tests:** "Can you fix real bugs in real codebases?"
- Reading & understanding large existing projects
- Making surgical changes without breaking things
- Working with production-grade test suites

**WebArena tests:** "Can you navigate websites like a human?"
- Visual UI understanding (where's the button?)
- Form filling and navigation flows
- Goal completion across multiple pages

**AgentBench tests:** "Can you adapt to any environment?"
- Terminal/OS operations (bash, file system)
- Strategic planning (games, puzzles)
- Tool use across different domains
- Reasoning without explicit code

**The Gap:** An agent might ace SWE-bench (great at coding) but fail WebArena (can't use a browser) or bomb AgentBench puzzles (can't reason beyond code). Testing all 3 reveals true versatility.

---

### Optional Extended Benchmarks
- **GAIA**: General AI assistant tasks (reasoning + tool use)
- **Terminal-Bench**: CLI-only tasks (89 command-line scenarios)
- **HumanEval**: Basic coding sanity check (164 Python functions)
- **MBPP**: Entry-level programming (974 tasks)
- **SWE-bench Lite**: Faster SWE-bench subset for iteration

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
│   ├── swe-bench/          # Coding benchmark
│   │   ├── runner.py
│   │   ├── evaluator.py
│   │   └── results/
│   ├── webarena/           # Browser mode benchmark
│   │   ├── runner.py
│   │   ├── evaluator.py
│   │   └── results/
│   └── agentbench/         # Real-world multi-domain benchmark
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

- **Overall Score**: Weighted average across the 3 core dimensions
  - 💻 SWE-bench (Coding): **40%**
  - 🌐 WebArena (Browser): **30%**
  - 🎯 AgentBench (Real-world): **30%**

- **Efficiency Score**: (Accuracy / Cost) × Speed_factor
- **Value Score**: Accuracy × Usability / Cost

**Specialty Scores:**
- **Coding Specialist Score**: SWE-bench performance (for pure coding agents)
- **Web Automation Score**: WebArena performance (for browser agents)
- **Generalist Score**: AgentBench average across all 8 environments

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
- [ ] Setup benchmark environments (SWE-bench, WebArena, AgentBench)
- [ ] Agent wrapper implementations (Pi, Aider, Mini-SWE)
- [ ] Docker isolation for each benchmark
- [ ] Basic evaluation metrics (accuracy, time, cost)
- [ ] Result storage system (SQLite + JSON logs)

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
