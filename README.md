# Hacienda Utilities

Command-line utilities for the Hacienda project.

## tree-dump

Interactive directory tree dumper with smart filtering and colored output.

### Installation

1. Ensure `tree` is installed:
   ```bash
   # macOS
   brew install tree

   # Linux
   apt-get install tree  # Debian/Ubuntu
   yum install tree      # RHEL/CentOS
   ```

2. Add to your PATH (optional):
   ```bash
   # Add to ~/.zshrc or ~/.bashrc
   export PATH="$PATH:/Users/jordan/workspace/github.com/hacienda/bin"
   ```

   Or use directly:
   ```bash
   /path/to/hacienda/bin/tree-dump
   ```

### Usage

```bash
# Interactive mode with current directory
tree-dump

# Specify a directory
tree-dump /path/to/directory

# Or use relative paths
tree-dump ./packages/my-package
```

### Features

#### Interactive Prompts
- **Directory description**: Add context about what the directory contains
- **Depth level**: Control how deep the tree should traverse (default: 3)
- **Filter presets**: Quick filters for common scenarios
  - `code`: Source code files (`.ts`, `.js`, `.py`, `.go`, etc.)
  - `docs`: Documentation (`.md`, `.txt`, `.pdf`, etc.)
  - `config`: Configuration files (`.json`, `.yaml`, `.toml`, etc.)
  - `web`: Web assets (`.html`, `.css`, `.vue`, etc.)
- **Custom patterns**: Specify your own file extensions (e.g., `*.ts,*.tsx,*.md`)

#### Smart Exclusions
- **Common excludes**: Automatically skip `node_modules/`, `.git/`, `dist/`, `build/`, etc.
- **Custom excludes**: Add your own exclusion patterns

#### Git Integration
- **Git-tracked only**: Show only files tracked by git (when in a git repository)

#### Display Options
- **File sizes**: Show human-readable file sizes
- **Hidden files**: Include dotfiles and hidden directories
- **Directories only**: Show just the directory structure
- **Colored output**: Full ANSI color support for better readability

#### Output Options
1. **Terminal display**: View the tree in your terminal
2. **Save to file**: Export to a timestamped file
3. **Both**: Display and save simultaneously

#### Metadata Header
Every output includes:
- Generation timestamp
- Directory path and description
- Depth level
- Applied filters and exclusions
- Full command used

#### Statistics
- Total file count
- Directory count
- Top 10 file extensions with counts

### Examples

#### Quick code-only dump
```bash
tree-dump ./packages/my-lib
# Select preset: 1 (code)
# Use common exclusions: y
# Output: Display in terminal
```

#### Deep documentation export
```bash
tree-dump ./docs
# Depth: 5
# Preset: 2 (docs)
# Output: Save to file
```

#### Git-tracked files only
```bash
tree-dump .
# Git tracked only: y
# Useful for seeing only committed files
```

#### Custom pattern with sizes
```bash
tree-dump ./src
# Pattern: *.test.ts,*.spec.ts
# Show sizes: y
# Find all test files with sizes
```

### Sample Output

```
# Directory Tree Dump
# Generated: 2025-11-29 15:30:45
# Directory: /Users/jordan/workspace/github.com/hacienda/packages/core
# Description: Core library package with TypeScript utilities
# Depth: 3
# Pattern: *.ts,*.json
# Common exclusions: enabled
# Command: tree -L 3 -P *.ts,*.json -I node_modules -I .git --dirsfirst -F -C /Users/jordan/workspace/github.com/hacienda/packages/core

packages/core/
├── src/
│   ├── utils/
│   │   ├── logger.ts
│   │   └── config.ts
│   ├── index.ts
│   └── types.ts
├── package.json
└── tsconfig.json

╔════════════════════════════════════════════╗
║   Statistics                               ║
╚════════════════════════════════════════════╝
Files found: 6
Directories (max depth 3): 3

Top file extensions:
  ts: 4
  json: 2
```

### Tips

1. **Start shallow**: Use depth 2-3 for large directories, increase as needed
2. **Use presets**: Faster than typing custom patterns
3. **Common exclusions**: Almost always want this enabled
4. **Save important dumps**: Use "Both" output to review and keep a record
5. **Add descriptions**: Future-you will thank you for context

### Color Scheme

- 🟦 **Directories**: Blue with bold
- 🟩 **Executables**: Green
- 🟪 **Archives**: Magenta
- 🟨 **Images**: Yellow
- ⬜ **Regular files**: Default color

Colors are automatically enabled and follow your terminal's color scheme.
