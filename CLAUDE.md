# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an nbdev-based Python project for learning and experimenting with neural networks from Andrej Karpathy's "Zero to Hero" course. The project uses nbdev's literate programming approach where Jupyter notebooks serve as the source of truth for both code and documentation.

## Architecture

- **nbs/**: Source notebooks containing code and documentation
  - `00_core.ipynb`: Core module notebook  
  - `index.ipynb`: Main documentation/README notebook
- **nn_andrej_zero_to_hero/**: Auto-generated Python package from notebooks
  - `core.py`: Generated from `00_core.ipynb`
- **_docs/**: Generated documentation website
- **_proc/**: Processed files during nbdev workflow

## Development Workflow

### Setup
```bash
# Install in development mode
pip install -e .
```

### Core Development Commands
```bash
# Compile notebooks to Python modules and docs
nbdev_prepare

# Export code from notebooks to Python files
nbdev_export

# Build documentation
nbdev_docs

# Run tests (uses nbdev's test flags in settings.ini)
nbdev_test

# Clean generated files
nbdev_clean
```

### Making Changes
1. Edit code in notebooks under `nbs/` directory
2. Run `nbdev_prepare` to sync changes to Python modules and docs
3. The Python files in `nn_andrej_zero_to_hero/` are auto-generated - never edit directly

## Key Files

- `settings.ini`: Main configuration file containing project metadata and nbdev settings
- `pyproject.toml`: Minimal build configuration
- `nbs/`: All source code lives here as notebooks
- Notebooks use nbdev directives like `#| export` to control code generation

## Testing

Tests are embedded in notebooks and controlled by `tst_flags = notest` in settings.ini. Use `nbdev_test` to run all tests.

## Documentation

Documentation is auto-generated from notebooks. The `index.ipynb` becomes the main README and documentation homepage.

## Important Notes

- Never edit files in `nn_andrej_zero_to_hero/` directly - they are auto-generated
- Always use `nbdev_prepare` after making changes to notebooks
- The project targets Python 3.7+ (see settings.ini)
- Uses Apache 2 license