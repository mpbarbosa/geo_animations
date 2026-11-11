# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Package manager

This project uses `uv`. Always use `uv` instead of `pip` or `python` directly.

```bash
uv sync                  # install / sync dependencies
uv add <package>         # add a dependency
uv run python main.py    # run a script
```

## Rendering animations

Scenes are Manim `Scene` subclasses. Render a scene with:

```bash
uv run manim main.py SceneName           # render at default quality
uv run manim -ql main.py SceneName       # low quality (fast preview)
uv run manim -qh main.py SceneName       # high quality (1080p60)
uv run manim -p main.py SceneName        # render and open in player
uv run manim -qh -p main.py SceneName    # high quality + auto-open
```

Output lands in `media/videos/<quality>/`. TeX cache goes in `media/Tex/`.

## Architecture

All animation code lives in Python files as Manim `Scene` subclasses. Each class defines a `construct(self)` method that contains the animation sequence. Manim handles rendering; there is no separate build step.

The `media/` directory is fully generated — do not edit files there.
