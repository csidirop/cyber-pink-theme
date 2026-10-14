# AGENTS.md

## Repository overview

This repository contains the Cyber Pink VS Code color-theme extension. Theme definitions live in `themes/`, and extension metadata and contributed theme registrations live in `package.json`.

## Editing guidelines

- Keep changes scoped to the requested theme variant unless the task explicitly applies to every variant.
- Preserve unrelated user changes in the working tree.
- Use lowercase six- or eight-digit hexadecimal colors consistently with the surrounding file.
- Prefer standard VS Code workbench color IDs and narrow TextMate scopes over broad overrides.
- For language-independent syntax colors, use generic TextMate scopes such as `keyword`, `variable`, and `entity.name.function`.
- Use language-specific scopes only when a token truly needs special treatment. For example, PHP `$this` is `variable.language.this.php`.
- The Cyan Edit variant is defined in `themes/cyber-pink-cyan-edit.json`.
- With VS Code's experimental modern connected tabs, `modernEditorTab.activeBackground` controls the active editor-tab surface.
- `sideBarTitle.background` controls the title row at the top of the Primary Side Bar; `sideBar.background` controls the main Explorer/Side Bar body; `activityBar.background` controls the narrow icon rail.

## Validation

After editing JSON files, validate them before packaging:

```bash
node -e "JSON.parse(require('fs').readFileSync('package.json', 'utf8')); JSON.parse(require('fs').readFileSync('themes/cyber-pink-cyan-edit.json', 'utf8')); console.log('JSON valid')"
```

## Local packaging and installation

Build the extension from the repository root:

```bash
npx @vscode/vsce package
```

Install the generated package locally:

```bash
code --install-extension cyber-pink-theme-0.4.3.vsix --force
```

Run **Developer: Reload Window** in VS Code after installation. The helper commands are also recorded in `compile.sh`.

## Verification

- Confirm the edited theme JSON parses successfully.
- Confirm the expected files are included in the generated VSIX.
- Do not commit the generated `.vsix` unless explicitly requested.
