# api-mkdocs

## Create a virtual environment for this app

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
pyenv virtualenv 3.10.5 api-mkdocs

# Automatically select the correct venv when you're in this directory:
pyenv local api-mkdocs

# Verify that your env is setup correctly
pyenv versions
python --version

# If the api-mkdocs venv is not selected, run the following
pyenv activate api-mkdocs

# Install dev dependencies if you intend to edit this script
pip install flake8 black

# Install project dependencies
pip install -r requirements.txt
```

## Setup virtualenv in VS Code for development

Press `⌘` + `Shift` + `p`

Select `Python: Select Interpreter`

Select `Enter interpreter path...`

Then enter `~/.pyenv/versions/3.10.5/envs/api-mkdocs/bin/python`

All of your dependencies should be supported by python interpreter.

```bash
# Run in virtualenv
uvicorn app:app --reload

# Run in Docker container
docker build -t api-mkdocs .
docker run -it api-mkdocs -p 8080:8080

# Push to registry
docker tag api-mkdocs:latest registry.everythingisacomputer.io/api-mkdocs:latest
docker push registry.everythingisacomputer.io/api-mkdocs:latest
```
