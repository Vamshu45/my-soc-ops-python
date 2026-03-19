---
description: Development workflow, code organization, and best practices for the Soc Ops project.
applyTo: "app/**, tests/**"
---

# Development Instructions

## ⚠️ Mandatory Pre-Commit Checklist

**Before every commit, run these commands:**
```bash
uv run ruff check . --fix && uv run ruff format .  # Lint & format
uv run pytest                                       # Test (all must pass)
uv run uvicorn app.main:app --reload              # Build & manual test
```
- ❌ Commit blocked if lint/format fails
- ❌ Commit blocked if any test fails
- ❌ Commit blocked if app won't run

## Quick Start

```bash
uv sync                                    # Install dependencies
uv run uvicorn app.main:app --reload      # Dev server (http://localhost:8000)
uv run pytest                              # Run tests
```

## Project Structure

```
app/
├── main.py              # FastAPI routes & middleware
├── models.py            # Pydantic data structures
├── game_logic.py        # Pure game rules & validation
├── game_service.py      # Session & state management
├── data.py              # Quiz data
├── static/css/app.css   # Utility classes
└── templates/           # Jinja2 templates + HTMX
tests/
└── test_api.py, test_game_logic.py
```

## Code Organization

### Backend (app/*.py)

| File | Purpose |
|------|---------|
| `models.py` | Pydantic models only (no logic) |
| `game_logic.py` | Pure functions: game rules, validation |
| `game_service.py` | Session management & state wrapping |
| `main.py` | Thin route handlers: request → service → template |

### Frontend (templates/)

- **base.html** — Master layout
- **Page templates** — Use `{% extends "base.html" %}`
- **components/** — Reusable HTMX-driven fragments

## HTMX + Jinja2 Patterns

Routes return partial HTML (not full pages):

```python
@app.post("/api/mark-cell", response_class=HTMLResponse)
async def mark_cell(request: Request) -> str:
    session = _get_game_session(request)
    session.mark_cell(cell_id)
    return templates.get_template("components/bingo_board.html").render(
        board=session.game.board
    )
```

Template with HTMX:
```html
<button hx-post="/api/mark-cell" 
        hx-target="#board"
        hx-swap="innerHTML">
  Mark Cell
</button>
```

## Code Quality Rules

- **Type hints** required on all functions
- **Function names** use `snake_case`, **Classes** use `PascalCase`
- **Naming**: Follow PEP 8; ruff enforces `E`, `F`, `I`, `N`, `W` rules
- **No unused imports, debug code**, or undefined variables
- **CSS**: Use utilities from `app/static/css/app.css`

## Testing

```bash
uv run pytest                    # All tests
uv run pytest tests/test_game_logic.py -v  # Specific file + verbose
```

**Pattern**: Arrange-Act-Assert
```python
def test_marking_cell_sets_marked_true():
    board = GameBoard()          # Arrange
    board.mark_cell("cell-1")    # Act
    assert board.get_cell("cell-1").marked  # Assert
```

## Adding Features

**New endpoint:**
1. Define model in `models.py` (if needed)
2. Implement logic in `game_logic.py`
3. Wrap in service (`game_service.py`)
4. Create route in `main.py` → return template response
5. Add tests in `tests/test_api.py`

**New component:**
1. Create `app/templates/components/my_component.html`
2. Use utility classes for styling
3. Include in parent: `{% include "components/my_component.html" %}`

## Debugging

- **Browser DevTools**: F12 for HTMX requests/responses
- **Server Logs**: Check uvicorn terminal for request logs
- **Print Debugging**: Use `print()` (remove before commit)
- **Breakpoints**: `breakpoint()` in code

## Stack

- **Backend**: FastAPI (Python 3.13+)
- **Frontend**: Jinja2 + HTMX (no build step)
- **Styling**: Custom CSS utilities
- **Testing**: pytest + httpx
- **Quality**: ruff (lint & format)
