# mriQA

Medical Resonance Imaging Study Q&A AI Agent toolkit.

## Quick Start

### Prerequisites
- Python 3.8+
- Git

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/LeoMcBills/mriQA.git
   cd mriQA
   ```

2. **Set up Python environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/macOS
   pip install -r requirements.txt
   pip install -e .
   ```

3. **Run tests:**
   ```bash
   pytest tests/
   ```

## Documentation

- **[Development Setup Guide](docs/development-setup.md)** - Complete setup instructions including Git authentication troubleshooting
- **[Notebooks](notebooks/)** - Jupyter notebooks with examples and prototypes

## Project Structure

```
mriQA/
├── src/mriQA/          # Main package source code
├── tests/              # Test suite
├── notebooks/          # Jupyter notebooks
├── experiments/        # Experimental code and results
├── docs/              # Documentation
├── requirements.txt    # Python dependencies
└── pyproject.toml     # Project configuration
```

## Development

For detailed development setup, Git configuration, and troubleshooting, see the [Development Setup Guide](docs/development-setup.md).

### Common Issues

If you encounter Git authentication errors (403 Permission Denied), check the [Git Authentication Setup](docs/development-setup.md#git-authentication-setup) section in the development guide.

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the terms specified in the [LICENSE](LICENSE) file.
