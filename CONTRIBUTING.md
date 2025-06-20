# Contributing to ARUX SDK

First off, thank you for considering contributing to the ARUX SDK! Your help is essential for keeping it great.

## How Can I Contribute?

### Reporting Bugs
If you find a bug, please ensure the bug was not already reported by searching on GitHub under Issues. If you're unable to find an open issue addressing the problem, open a new one. Be sure to include a title and clear description, as much relevant information as possible, and a code sample or an executable test case demonstrating the expected behavior that is not occurring.

### Suggesting Enhancements
If you have an idea for an enhancement, please open an issue to discuss it. This allows us to coordinate efforts and ensure that your suggestion aligns with the project's goals.

### Pull Requests
1. Fork the repo and create your branch from `main`.
2. If you've added code that should be tested, add tests.
3. Ensure the test suite passes.
4. Make sure your code lints.
5. Issue that pull request!

## Development Setup

### Prerequisites
- GCC (GNU Compiler Collection)
- CMake (version 3.10 or higher recommended)
- Git

### Cloning the Repository
```bash
git clone https://github.com/your-username/arux-sdk.git
cd arux-sdk
```
(Replace `your-username` with your actual GitHub username or the organization's name if you are a direct collaborator)

### Building the Project
A `CMakeLists.txt` is provided at the root of the `sdk` directory.
```bash
cd sdk
mkdir build
cd build
cmake ..
make
```

## Pull Request Workflow
1. Ensure any install or build dependencies are removed before the end of the layer when doing a build.
2. Update the README.md with details of changes to the interface, this includes new environment variables, exposed ports, useful file locations and container parameters.
3. Increase the version numbers in any examples and the README.md to the new version that this Pull Request would represent. The versioning scheme we use is SemVer.
4. You may merge the Pull Request in once you have the sign-off of two other developers, or if you do not have permission to do that, you may request the second reviewer to merge it for you.

We look forward to your contributions!
