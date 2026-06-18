# University CS Course Skills

Free computer science courses from top universities, converted into [Agent Skills](https://agentskills.io) for AI-assisted learning. Works with Claude Code, OpenCode, Cursor, Copilot, Gemini CLI, and [30+ other agents](https://agentskills.io).

## What's Inside

18 skills covering courses from 6 top universities:

| University | Skills | Topics |
|------------|--------|--------|
| **Harvard** | `cs50x`, `cs50p`, `cs50-ai`, `cs50-web` | Intro CS, Python, AI, Web Dev |
| **Cornell** | `cornell-cs6120`, `cornell-cs4320`, `cornell-cs4820` | Compilers, Databases, Algorithms |
| **Stanford** | `stanford-cs161`, `stanford-cs221`, `stanford-cs229` | Algorithms, AI, Machine Learning |
| **MIT** | `mit-6006`, `mit-6034`, `mit-os` | Algorithms, AI, Operating Systems |
| **Georgia Tech** | `gt-networking`, `gt-os`, `gt-ml` | Networking, OS, ML for Trading |
| **UC Berkeley** | `berkeley-cs61c` | Computer Architecture |
| **Princeton** | `princeton-algos` | Algorithms & Data Structures |

## Quick Start

### Installation

Copy the skills you want to your agent's skills directory:

```bash
# Install all skills
cp -r skills/* ~/.opencode/skills/

# Or install specific ones
cp -r skills/cs50x ~/.opencode/skills/
cp -r skills/stanford-cs229 ~/.opencode/skills/
```

#### Agent-Specific Paths

| Agent | Skills Directory |
|-------|------------------|
| **Claude Code** | `~/.claude/skills/` |
| **OpenCode** | `~/.opencode/skills/` |
| **Cursor** | Project `.cursor/skills/` |
| **Copilot** | Project `.github/copilot/skills/` |
| **Gemini CLI** | `~/.gemini/skills/` |

### Usage

Load any skill in your agent:

```
skill({ name: "cs50x" })
skill({ name: "stanford-cs229" })
skill({ name: "cornell-cs6120" })
```

## Skill Structure

Each skill contains:

```
skill-name/
├── SKILL.md                    # Main entry point
└── references/
    ├── syllabus.md             # Course breakdown
    ├── key-concepts.md         # Cheat sheets
    ├── exercises.md            # Practice problems
    └── resources.md            # Additional materials
```

## Learning Paths

### Beginner → Web Developer
1. `cs50x` → Foundations (C, Python, SQL, web)
2. `cs50p` → Python deep dive
3. `cs50-web` → Full-stack (Django, React)

### Beginner → AI/ML Engineer
1. `cs50x` or `cs50p` → Programming
2. `mit-6006` → Algorithms
3. `cs50-ai` → AI fundamentals
4. `stanford-cs229` → Mathematical ML

### Systems & Compilers
1. `cs50x` → Programming
2. `berkeley-cs61c` → Computer architecture
3. `mit-os` → Operating systems
4. `cornell-cs4320` → Databases
5. `cornell-cs6120` → Compilers

### Theory of Computation
1. `stanford-cs161` → Algorithm design
2. `princeton-algos` → Java implementations
3. `cornell-cs4820` → Algorithm analysis (theory)

## All Skills

| Skill | University | Level | Topics |
|-------|------------|-------|--------|
| `cs50x` | Harvard | Beginner | C, Python, SQL, algorithms |
| `cs50p` | Harvard | Beginner | Python, OOP, testing |
| `cs50-ai` | Harvard | Intermediate | AI, search, ML, neural nets |
| `cs50-web` | Harvard | Intermediate | Django, React, JavaScript |
| `cornell-cs6120` | Cornell | Advanced | Compilers, LLVM, SSA |
| `cornell-cs4320` | Cornell | Intermediate | SQL, databases, transactions |
| `cornell-cs4820` | Cornell | Advanced | Algorithm analysis, NP-completeness |
| `stanford-cs161` | Stanford | Intermediate | Algorithm design, DP, graphs |
| `stanford-cs221` | Stanford | Intermediate | AI principles, search, ML |
| `stanford-cs229` | Stanford | Advanced | Machine learning theory |
| `mit-6006` | MIT | Intermediate | Algorithms, complexity |
| `mit-6034` | MIT | Intermediate | AI, neural nets, planning |
| `mit-os` | MIT | Advanced | OS design, xv6 labs |
| `gt-networking` | Georgia Tech | Intermediate | TCP/IP, routing, DNS |
| `gt-os` | Georgia Tech | Intermediate | Processes, memory, files |
| `gt-ml` | Georgia Tech | Intermediate | ML for trading |
| `berkeley-cs61c` | UC Berkeley | Intermediate | C, RISC-V, caches, parallelism |
| `princeton-algos` | Princeton | Intermediate | Algorithms, Java |

## Contributing

Contributions welcome! To add a new course skill:

1. Fork this repo
2. Create a skill directory under `skills/`
3. Follow the structure: `SKILL.md` + `references/` with 4 files
4. Submit a PR

## License

MIT

## Acknowledgments

Course materials are from the respective universities under their open licenses. This project organizes them as Agent Skills for AI-assisted learning.
