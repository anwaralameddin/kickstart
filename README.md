# kickstart

A collection of scripts, code snippets, templates and guides for setting up a new project.

## Installation

1. Clone the repository.

```bash
git clone https://github.com/anwaralameddin/kickstart.git
```

2. Rename [config.example](config.example) to <code>config</code> and ammend it to your needs.

```bash
mv kickstart/config.example kickstart/config
# ammend kickstart/config
```

3. Add the root directory to your <code>PATH</code>:

```bash
export PATH="$PATH:$(pwd)/kickstart"
```

## Usage

Run the <code>kickstart</code> script to see the available options:

```bash
kickstart --help
```

## Supported projects

- [X] LaTeX
- [ ] Bash
- [ ] Rust
- [ ] Python
- [ ] C
- [ ] C++
