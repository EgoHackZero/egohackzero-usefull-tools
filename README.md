# EgoHackZero's Useful Tools for Claude Code

A collection of useful commands and tools for Claude Code that enhance developer productivity.

## Features

### Conda Environment Runner (`/conda-run`)

Seamlessly manage and run Python code with conda environments directly from Claude Code.

**Key capabilities:**
- Automatically detect or create conda environments
- Smart environment selection with interactive prompts
- Support for multiple Python versions (3.10, 3.11, 3.12)
- Integrated package installation
- Persistent environment activation across commands

**Usage:**

```bash
# Run with a specific environment
/conda-run myenv

# Let Claude help you select or create an environment
/conda-run

# Examples of what Claude can do after activation:
# - Run Python scripts
# - Install packages with pip or conda
# - Execute Python code snippets
# - Manage environment dependencies
```

## Installation

### Method 1: Manual Installation

1. Clone or download this repository
2. Copy the `.claude` directory to your project root:
   ```bash
   cp -r egohackzero_usefull_tools/.claude /path/to/your/project/
   ```

### Method 2: Symlink (Recommended for development)

Create a symlink to use the extension across multiple projects:

```bash
# Linux/Mac
ln -s /path/to/egohackzero_usefull_tools/.claude /path/to/your/project/.claude

# Windows (requires admin privileges)
mklink /D "C:\path\to\your\project\.claude" "C:\path\to\egohackzero_usefull_tools\.claude"
```

### Method 3: Git Submodule

Add as a git submodule to your project:

```bash
git submodule add https://github.com/egohackzero/usefull-tools.git .claude-extensions/egohackzero_usefull_tools
ln -s .claude-extensions/egohackzero_usefull_tools/.claude .claude
```

## Requirements

- Claude Code CLI
- Conda/Miniconda installed on your system
- Conda initialization script at `~/miniconda3/etc/profile.d/conda.sh` (or update the path in the command)

## Commands Reference

### `/conda-run [env_name]`

**Description:** Run Python code with conda environment management

**Arguments:**
- `env_name` (optional): Name of the conda environment to use

**Behavior:**
- If environment exists: Activates it
- If environment doesn't exist: Prompts to create it with selected Python version
- If no environment specified: Shows list of available environments or option to create new

**Examples:**

```bash
# Use existing environment
/conda-run ml-project

# Interactive selection
/conda-run

# After activation, run Python code
# Claude will execute: source conda && conda activate env_name && python script.py
```

## Contributing

Feel free to contribute additional useful commands and tools!

1. Fork the repository
2. Create a new command in `.claude/commands/`
3. Update `package.json` with command metadata
4. Submit a pull request

## License

MIT License - See LICENSE file for details

## Author

**egohackzero**

## Changelog

### v1.0.0 (Initial Release)
- Added `/conda-run` command for conda environment management
- Support for automatic environment creation
- Interactive environment selection
- Multi-version Python support
