# Development Guide for HintEval

This document provides guidelines for developing and contributing to the HintEval project.

## Setting up the Development Environment

1. **Fork the Repository**
   Fork the [HintEval repository](https://github.com/DataScienceUIBK/HintEval) on GitHub.

2. **Clone your Fork**
   ```
   git clone https://github.com/YOUR_USERNAME/HintEval.git
   cd HintEval
   ```

3. **Set up a Virtual Environment**
   ```
   conda create -n hinteval_env python=3.11.9 --no-default-packages
   conda activate hinteval_env
   ```

4. **Install Dependencies**

   You'll need PyTorch 2.4.0 for HintEval. Refer to the [PyTorch installation page](https://pytorch.org/get-started/previous-versions/) for platform-specific installation commands. If you have access to GPUs, it's recommended to install the CUDA version of PyTorch, as many of the evaluation metrics are optimized for GPU use.
   
   Once PyTorch 2.4.0 is installed, you can install HintEval via pip:
   ```
   pip install -e .
   ```

## Development Workflow

1. **Create a New Branch**
   ```
   git checkout -b feature/your-feature-name
   ```

2. **Make Changes and Commit**
   ```
   git add .
   git commit -m "Your descriptive commit message"
   ```

3. **Push Changes to Your Fork**
   ```
   git push origin feature/your-feature-name
   ```

4. **Create a Pull Request**
   Go to the original HintEval repository and create a new pull request from your feature branch.

## Coding Standards

- Follow PEP 8 guidelines for Python code.
- Use type hints where possible.
- Write docstrings for all functions, classes, and modules.
- Ensure all tests pass before submitting a pull request.

## Documentation

- Update documentation for any new features or changes to existing functionality.
- Use [NumPy style](https://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_numpy.html#example-numpy) for docstrings.

## Submitting Pull Requests

1. Ensure your code adheres to the project's coding standards.
2. Include tests for new functionality.
3. Update documentation as necessary.
4. Provide a clear description of the changes in your pull request.

Thank you for contributing to HintEval!
