# IPHub Coding Style

## Description

This coding_style repository contains files to ensure a consistent coding style for projects.

### C and C++

- [Clang-format](https://clang.llvm.org/docs/ClangFormat.html) is a tool that automatically formats C and C++ code with the style given in the `.clang-format` file.
- [Clang-tidy](https://clang.llvm.org/extra/clang-tidy/) is a static analysis tool for C and C++ code, to ensure some coding standards and best practices for projects.

### Python

- [Black](https://black.readthedocs.io/en/stable/) is used to format Python code. It can be enabled using

  ```toml
  [tool.black]
  line-length = 100
  ```

- [Isort](https://pycqa.github.io/isort/) is used to group python import statements. It can be enabled using

  ```toml
  [tool.isort]
  line_length = 100
  ```

- [Pylint](https://pypi.org/project/pylint/) is used for static code analysis.
- [Mypy](https://mypy-lang.org/) can be used for optional static type checking.

### Rust

- `cargo fmt` is used to format Rust code.
- `cargo clippy` is used for static code analysis.

### Groovy

- [Groovy Lint](https://github.com/nvuillam/npm-groovy-lint) is used to format and lint Groovy files.

### CMake

- [cmake-format](https://github.com/cheshirekow/cmake_format) is used to format CMake files.

## Usage

It is recommended to use

- [iphub_boilerplate_c](https://gitlab.intra.infineon.com/iphub/boilerplate_c)
- [iphub_boilerplate_rust](https://gitlab.intra.infineon.com/iphub/boilerplate_rust)
- [iphub_boilerplate_python](https://gitlab.intra.infineon.com/iphub/boilerplate_python)

To directly use this repository, it is recommended to also use it as git submodule, see [Integration as Git Submodule](#integration-as-git-submodule).
In the following it is described how to use clang-format and clang-tidy either in VS Code or in WSL.

### C and C++

#### VS Code

- Install the C/C++ extension in VS Code
- Only if the .clang-format and .clang-tidy file is NOT located at top level:
  - [Add Symbolic Link](#add-symbolic-link).
  - Or: adapt settings.json file (File -> Preferences -> Settings -> Workspace). Search for "clang-format". Click "Edit in settings.json". Add the following:

    ```json
    "clang-format.executablePath": "/path/to/.clang-format",
    "clang-tidy.executablePath": "/path/to/.clang-tidy"
    ```

- To use in VS Code: Open the command palette ("Ctrl + Shift + P")
  - for clang-tidy: enter "Run Code Analysis"
  - for clang-format: enter "Format Document with" -> "C/C++"
- Additional option: Format on Save -> Go to Settings -> Enable "Editor: Format on Save"

#### WSL or Debian like Linux

Alternatively to VS Code Windows Subsystem for Linux (WSL) can be used.
Therefore install the clang tools in WSL:

```bash
sudo apt install clang-tidy
sudo apt install clang-format
```

To use clang-format and clang-tidy in a bash to format a file, and the clang files are located at top level of you repository, call:

```bash
clang-format -style=file [file]
clang-tidy -style=file [file]
```

If the clang files are not located at top level, see [Add Symbolic Link](#add-symbolic-link).

#### Windows

LLVM including clang-format and clang-tidy can be downloaded here: [https://releases.llvm.org/download.html](https://releases.llvm.org/download.html)

#### Integration as Git Submodule

In your project (parent_repository) call the `git submodule add` command, to include the coding_style in the `lib/coding_style` directory of your project:

```bash
cd /path/to/parent_repository
git submodule add https://gitlab.intra.infineon.com/ifxsource/hostlib/coding_style lib/coding_style
```

To update your repository to include the latest changes from the coding_style repository, use:

```bash
git submodule update --init --recursive
```

##### Add Symbolic Link

To use the clang files in your repository without specifying the full path to the clang files in this submodule, you can create a symbolic link:

```bash
cd /path/to/parent_repository
ln -s lib/coding_style/.clang-format .clang-format
ln -s lib/coding_style/.clang-tidy .clang-tidy
```

### Python Code

Tools can be installed executing:

```bash
pip install black isort pylint mypy
```

Usage is specified in `./pyproject.toml`:

```toml
[tool.black]
line-length = 100

[tool.isort]
line_length = 100

[tool.mypy]

[tool.pylint]
```

#### VS Code

Install [Python Extension Pack](https://marketplace.visualstudio.com/items?itemName=donjayamanne.python-extension-pack) extension.

### Groovy Code

Install using:

```bash
npm install -g npm-groovy-lint
```

#### VS Code

Install [Groovy Lint, Format and Fix](https://marketplace.visualstudio.com/items?itemName=NicolasVuillamy.vscode-groovy-lint) extension

### CMake

cmake-format can be installed executing:

```bash
pip install cmakelang
```

#### VS Code

Install [cmake-format](https://marketplace.visualstudio.com/items?itemName=cheshirekow.cmake-format) extension.
