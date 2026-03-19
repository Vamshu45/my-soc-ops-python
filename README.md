# 🎮 Soc Ops — Social Bingo for Modern Teams

A dynamic, real-time social bingo game built to energize in-person mixers and team events. Players mingle, find colleagues matching various criteria, and race to get 5 in a row. Fast-paced, social, and genuinely fun.

> **Perfect for**: Icebreakers, networking events, team building, corporate mixers, conferences

---

## ✨ What Makes It Special

- **Real-Time Gameplay** — Instant updates via HTMX. Mark cells and see results instantly across browsers.
- **No-Build Frontend** — Pure Jinja2 templates + HTMX. Simplicity meets interactivity.
- **Type-Safe Backend** — FastAPI with strict type hints and modern Python (3.13+).
- **Developer-Friendly** — Comprehensive development instructions, strict linting, and 100% test coverage.
- **Learn-by-Doing** — Educational workshop included. Understand how modern AI agents handle complex codebases.

---

## 🚀 Quick Start

```bash
# Clone and setup
git clone https://github.com/Vamshu45/my-soc-ops-python
cd my-soc-ops-python
uv sync

# Run the game
uv run uvicorn app.main:app --reload

# Then visit: http://localhost:8000
```

That's it. Takes ~2 minutes.

---

## 🏗️ Tech Stack

| Layer | Tech |
|-------|------|
| **Backend** | FastAPI (Python 3.13+) with type safety |
| **Frontend** | Jinja2 templates + HTMX (zero build step) |
| **Styling** | Custom CSS utilities (lightweight & fast) |
| **Testing** | pytest + 100% coverage |
| **Quality** | ruff (strict linting + type hints) |

---

## 📚 Learn How It's Built

This project is a **complete teaching example** for modern development practices:

### Workshop Modules
| # | Topic | Learn |
|---|-------|-------|
| **00** | [Overview & Checklist](workshop/00-overview.md) | Project structure and goals |
| **01** | [Setup & Context](workshop/01-setup.md) | Environment setup, dependencies |
| **02** | [Design-First Frontend](workshop/02-design.md) | Building UI components the right way |
| **03** | [Custom Quiz Master](workshop/03-quiz-master.md) | Adding new features with AI agents |
| **04** | [Multi-Agent Dev](workshop/04-multi-agent.md) | Advanced workflows with specialized agents |
| **05** | [Complete Example](workshop/05-complete.md) | Full walkthrough of a complex feature |

👉 **Start here**: [Read the complete guide](workshop/GUIDE.md)

---

## 🎯 How to Play

1. **Enter the Game** — Get a unique session, grab a bingo card
2. **Circulate** — Move around the room, talk to people
3. **Mark Matches** — Find someone matching a cell's criteria? Mark it!
4. **Win** — First to 5 in a row (horizontal, vertical, diagonal) wins
5. **Share** — Celebrate and play again with different cards

---

## 🛠️ For Developers

### Development Workflow
```bash
# Lint & format
uv run ruff check . --fix && uv run ruff format .

# Run tests (mandatory before commits)
uv run pytest

# Start dev server with hot reload
uv run uvicorn app.main:app --reload
```

### Key Files
- **[app/main.py](app/main.py)** — FastAPI server & routes
- **[app/game_logic.py](app/game_logic.py)** — Pure game rules
- **[app/game_service.py](app/game_service.py)** — Session management
- **[app/templates/](app/templates/)** — Frontend components
- **[tests/](tests/)** — Test suite (25 tests, all passing)

### Code Standards
- ✅ Type hints on all functions (enforced)
- ✅ No unused variables (caught by linting)
- ✅ Modern Python syntax (pyupgrade)
- ✅ All tests passing before commit
- ✅ See [Development Guide](/.github/instructions/development.instructions.md) for details

---

## 🌐 Deployment

This repo **auto-deploys to GitHub Pages** on every push to `main`.

```bash
git push origin main
# → Automatically builds and deploys
```

---

## 📋 Prerequisites

- **Python 3.13+** — [Download here](https://www.python.org/downloads/)
- **uv** — Fast Python package manager ([Install here](https://docs.astral.sh/uv/))

### Using Devcontainer?
- **VS Code**: Opens automatically when you first clone
- **Codespaces**: Click **Code** → **Codespaces** → **Create codespace on main**

---

## 📖 Documentation

| Doc | Purpose |
|-----|---------|
| [Development Guide](/.github/instructions/development.instructions.md) | Workflow, architecture, adding features |
| [CSS Utilities](/.github/instructions/css-utilities.instructions.md) | Styling system & available classes |
| [Frontend Design](/.github/instructions/frontend-design.instructions.md) | Design patterns and best practices |
| [Workshop Guide](workshop/GUIDE.md) | Complete learning path |

---

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Code of Conduct**: This project adopts the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). See [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 🎓 Credits

Built as an educational project to demonstrate modern development practices, AI-assisted coding workflows, and interactive web applications.

---

**Ready to play? Get started:** `uv sync && uv run uvicorn app.main:app --reload`

Then visit **http://localhost:8000** 🎮
