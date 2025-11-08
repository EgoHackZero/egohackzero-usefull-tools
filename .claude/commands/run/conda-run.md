# Run Python with Conda Environment

When this command is invoked, follow these steps to run Python code with a conda environment:

## Step 1: Check for environment specification
- Look for an environment name in the user's message or command arguments
- The environment name may be specified as: `/conda-run [env_name]` or mentioned in the user's request

## Step 2: Handle environment
If environment name is provided:
1. Source conda: `source ~/miniconda3/etc/profile.d/conda.sh`
2. Check if the environment exists: `conda env list | grep -w [env_name]`
3. If it exists, activate it: `conda activate [env_name]`
4. If it doesn't exist:
   - Use AskUserQuestion to ask:
     - Confirm the environment name (or let them change it)
     - Python version to use (options: 3.11, 3.12, 3.10, or custom)
   - If Python version is not specified or user selects default, use Python 3.11 (stable)
   - Create environment: `conda create -n [env_name] python=[version] -y`
   - Activate it after creation

If NO environment name is provided:
1. Source conda: `source ~/miniconda3/etc/profile.d/conda.sh`
2. List all available environments: `conda env list`
3. Use AskUserQuestion tool to ask which environment to use (include "Create new environment" as an option)
4. If user selects "Create new environment":
   - Ask for environment name
   - Ask for Python version (default to 3.11 if not specified)
   - Create and activate the environment
5. Otherwise, activate the selected environment

## Step 3: Run the Python code
- After activating the environment, run the Python command/script requested by the user
- Use the format: `source ~/miniconda3/etc/profile.d/conda.sh && conda activate [env_name] && python [script_or_code]`

## Notes
- Always source conda initialization before running conda commands
- Default Python version is 3.11 (stable) when not specified
- Keep the environment activated for the entire bash session if running multiple commands
- If user requests to install packages, use: `conda activate [env_name] && pip install [package]` or `conda install [package]`
