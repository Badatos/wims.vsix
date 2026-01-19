# WIMS VS Code Extension - Copilot Instructions

## Project Overview
This is a VS Code syntax highlighting extension for WIMS (Web Interactive Multipurpose Server) module development. It provides syntax highlighting for 18 file types used in the Open Exercise Format (OEF) language.

## Core Architecture

### Single-Purpose Design
- **Extension Type**: Syntax highlighter (no code execution, no runtime dependencies)
- **Main Asset**: [syntaxes/WIMS.tmLanguage](syntaxes/WIMS.tmLanguage) - TextMate grammar definition in XML/plist format
- **Configuration**: [language-configuration.json](language-configuration.json) - Editor behavior for brackets, comments, auto-closing pairs
- **Entry Point**: [package.json](package.json) registers the language and grammar with VS Code

### Supported File Extensions
The extension recognizes 18 file types: `.phtml`, `.var`, `.proc`, `.input`, `.ca`, `.cn`, `.de`, `.en`, `.es`, `.fr`, `.it`, `.nl`, `.si`, `.tw`, `.template`, `.def`, `.local`, `.dat`

## Pattern Recognition in WIMS Language

The grammar highlights these core elements:

1. **Variables**: `$(PARAM1)` or `$VAR_NAME` syntax
2. **Comments**: Lines starting with `#` or `!!`
3. **Reserved Keywords**: `to`, `of`, `within`, `in`, `into`, `by`, `default`, `internal`, `between`, `select`, `where`
4. **Element Types**: `line`, `lines`, `column`, `word`, `words`, `item`, `items`
5. **Initialization States**: `any`, `allow`, `deny`, `init`, `config`, `reply`
6. **Mathematical Functions**: `abs`, `sqrt`, `sin`, `cos`, `max`, `min`, `gcd`, `lcm`, etc. (50+ functions)
7. **WIMS Commands**: Prefixed with `!` (e.g., `!if`, `!for`, `!foreach`, `!changeto`, `!eval`, `!let`, `!record`)
8. **External Tools**: `pari`, `maxima`, `yacas`, `wims`, `draw`, `slib`, `teximg`
9. **Comparison Operators**: Standard (`==`, `!=`, `<`, `<=`, `>`, `>=`) and text-based (`isin`, `notin`, `issamecase`, `and`, `or`)
10. **Numeric Constants**: Auto-highlighted integers

## Development Workflow

### Editing the Grammar
- **File Format**: XML plist (not JSON) - maintain DTD at top
- **Pattern Structure**: Each pattern is a dict with keys: `comment`, `match` (regex), `name` (scope identifier)
- **Scope Naming Convention**: Use hierarchical names like `entity.name.function.wims` or `keyword.operator.compare.wims`
- **Regex Testing**: Use [Debuggex](https://www.debuggex.com/) or VS Code's regex tester to validate pattern matches

### Testing Changes
1. Install locally in `.vscode/extensions/` directory
2. Open a WIMS file with matching extension
3. Use VS Code's "Developer: Inspect Editor Tokens and Scopes" command (Ctrl+Shift+P)
4. Verify syntax highlighting against expected scope names

### Key Conventions
- Comments in WIMS use `#` (start-of-line) or `!!` (start-of-line)
- WIMS commands always start with `!` - this is a critical pattern
- Mathematical functions are domain-specific (hyperbolic, logarithmic, trigonometric)
- Each function scope receives appropriate theme coloring through VS Code's theme system

## File Dependencies

```
package.json (extension manifest)
├─ language-configuration.json (editor settings)
└─ syntaxes/WIMS.tmLanguage (grammar patterns)
```

**Never** modify the installed location in `.vscode/extensions/` - always edit source files.

## Common Tasks

- **Add new WIMS command**: Find the `wimscommand` pattern match in WIMS.tmLanguage, add command name to regex
- **Add mathematical function**: Update the function pattern match (search for `abs|sign|sqrt`)
- **Add file extension**: Update `fileTypes` array in WIMS.tmLanguage AND `extensions` array in package.json
- **Test highlighting**: Use "Developer: Inspect Editor Tokens and Scopes" to debug scope assignment

## Extension Metadata
- **VS Code Minimum**: 1.61.0
- **Language ID**: `wims`
- **Category**: Programming Languages
- **Version**: 0.0.1 (unreleased)
