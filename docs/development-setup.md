# Development Setup Guide

This guide provides comprehensive instructions for setting up the mriQA development environment, including troubleshooting common Git authentication issues.

## Prerequisites

- **Python 3.8+** - Check with `python --version`
- **Git** - Check with `git --version`
- **GitHub Account** with repository access

## Environment Setup

### 1. Clone the Repository

```bash
git clone https://github.com/LeoMcBills/mriQA.git
cd mriQA
```

### 2. Python Environment Setup

Create and activate a virtual environment:

```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
source venv/bin/activate  # Linux/macOS
# or
venv\Scripts\activate     # Windows
```

### 3. Install Dependencies

```bash
# Install package in development mode
pip install -e .

# Install development dependencies
pip install -r requirements.txt

# Install additional development tools
pip install pytest black flake8 jupyter
```

### 4. Verify Installation

```bash
# Run tests
pytest tests/

# Check package installation
python -c "import mriQA; print('mriQA installed successfully')"
```

## Git Configuration & Authentication

### Initial Git Setup

Configure your Git identity:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Fixing Common Authentication Issues

#### Problem: 403 Permission Denied

If you encounter this error:
```
remote: Permission to LeoMcBills/mriQA.git denied to LeoMcBills.
fatal: unable to access 'https://github.com/LeoMcBills/mriQA.git/': The requested URL returned error: 403
```

#### Solution 1: Fix Remote URL (Recommended)

Remove embedded tokens from the remote URL:

```bash
# Check current remote URL
git remote -v

# If you see embedded tokens, reset to standard HTTPS
git remote set-url origin https://github.com/LeoMcBills/mriQA.git

# Configure credential helper
git config --global credential.helper store
```

#### Solution 2: Generate New Personal Access Token

1. Go to GitHub → Settings → Developer settings → Personal access tokens
2. Generate new token with `repo` permissions
3. Use token as password when prompted

#### Solution 3: Use SSH (Alternative)

```bash
# Generate SSH key
ssh-keygen -t ed25519 -C "your.email@example.com"

# Add SSH key to ssh-agent
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Add public key to GitHub (copy output and paste in GitHub SSH settings)
cat ~/.ssh/id_ed25519.pub

# Change remote to SSH
git remote set-url origin git@github.com:LeoMcBills/mriQA.git
```

## Development Workflow

### 1. Create Feature Branch

```bash
git checkout -b feature/your-feature-name
```

### 2. Make Changes

Edit code, add tests, update documentation as needed.

### 3. Run Quality Checks

```bash
# Run tests
pytest tests/

# Format code
black src/ tests/

# Check code style
flake8 src/ tests/
```

### 4. Commit and Push

```bash
git add .
git commit -m "feat: add your feature description"
git push origin feature/your-feature-name
```

### 5. Create Pull Request

Go to GitHub and create a pull request from your feature branch to main.

## Project Structure

```
mriQA/
├── src/
│   └── mriQA/              # Main package
│       ├── __init__.py
│       ├── agents/         # AI agent modules
│       ├── data/           # Data processing
│       └── utils/          # Utility functions
├── tests/                  # Test suite
│   ├── __init__.py
│   └── test_*.py
├── notebooks/              # Jupyter notebooks
│   └── 00_agent_prototype.ipynb
├── experiments/            # Experimental code
├── docs/                   # Documentation
├── requirements.txt        # Python dependencies
├── pyproject.toml         # Project configuration
├── setup.cfg              # Setup configuration
└── Makefile               # Build automation
```

## Running Jupyter Notebooks

```bash
# Start Jupyter server
jupyter notebook

# Or use JupyterLab
jupyter lab

# Navigate to notebooks/ directory in the browser
```

## Testing

### Run All Tests

```bash
pytest
```

### Run Specific Test File

```bash
pytest tests/test_agent.py
```

### Run with Coverage

```bash
pytest --cov=mriQA tests/
```

## Building and Packaging

### Local Development Build

```bash
pip install -e .
```

### Production Build

```bash
python -m build
```

## Troubleshooting

### Common Issues

1. **Python import errors**: Ensure virtual environment is activated
2. **Git authentication**: Follow the authentication fixes above
3. **Package not found**: Install in development mode with `pip install -e .`
4. **Test failures**: Check dependencies are installed correctly

### Getting Help

- Check existing [GitHub Issues](https://github.com/LeoMcBills/mriQA/issues)
- Create new issue with detailed error description
- Include Python version, OS, and error traceback

## Contributing

1. Fork the repository
2. Create feature branch
3. Make changes with tests
4. Ensure all checks pass
5. Submit pull request

For detailed contribution guidelines, see the main README.md file.