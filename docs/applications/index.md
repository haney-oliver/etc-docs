---
title: Applications
icon: material/application-brackets
---

## Setup

Install the application repositories:

- [api-storytime](./storytime/index.md)

### Create application virtual environments

```bash
brew install pyenv
brew install pyenv-virtualenv
```

Add the following lines to your ~/.zshrc

```bash
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
export PIPENV_PYTHON="$PYENV_ROOT/shims/python"
export PYENV_VIRTUALENV_DISABLE_PROMPT=1
plugin=(
  pyenv
)
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

Then activate your virtual environment and bind it to your working directory:

```bash
source ~/.zshrc

pyenv install -v 3.10.5
pyenv virtualenv 3.10.5 <APP_NAME>

# Automatically select the correct venv when you're in this directory:
cd <APP_NAME>
pyenv local <APP_NAME>

# Verify that your env is setup correctly
pyenv versions
python --version

# If the <APP_NAME> venv is not selected, run the following
pyenv activate <APP_NAME>

# Install dev dependencies if you intend to edit this script
pip install flake8 black

# Install project dependencies
pip install -r requirements.txt
```

??? question "How to configure VS Code to use your new virtualenv"
    Press `⌘` + `Shift` + `p`

    Select `Python: Select Interpreter`

    Select `Enter interpreter path...`

    Then enter `~/.pyenv/versions/3.10.5/envs/<APP_NAME>/bin/python`
    
    All of your dependencies should be supported by python interpreter.

```bash
# Run in virtualenv
uvicorn app:app --reload

# Run in Docker container
docker build -t <APP_NAME> .
docker run -it <APP_NAME> -p 8080:8080

# Push to registry
docker tag <APP_NAME>:latest registry.everythingisacomputer.io/<APP_NAME>:latest
docker push registry.everythingisacomputer.io/<APP_NAME>:latest
```
