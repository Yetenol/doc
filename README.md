# Documentation 

![last commit](https://img.shields.io/github/last-commit/yetenol/doc?color=white)

This project contains all my documentations of my developer life including code templates, tips and tricks, cheat sheets and glossaries.

# Windows

- **[Components](windows/components.md)** ›
    Certificates | `certmgr.msc`
- **[Settings app pages](windows/settings.md)** ›
    Display | `ms-settings:display`
- **[Dll commands](windows/dll.md)** ›
    Neue Verknüpfung anlegen | `rundll32 appwiz.cpl,NewLinkHere`
- **[Troubleshooters](windows/troubleshooters.md)** ›
    Printer Troubleshooter | `msdt -id PrinterDiagnosticmsdt`
- **[Icon libraries](windows/icons.md)** ›
    Images Library | `shell32.dll`
- **[Context menu](windows/context-menu.md)** ›
    Open in VS Code

## [Known Folders](windows/known-folders/known-folders.md)

- **[User Folders](windows/known-folders/user-folders.md)** ›
    Downloads Folder | `shell:My Pictures`
- **[OS Panels, Folders](windows/known-folders/guids.md)** ›
    Recycle Bin | `shell:::{}`
- **[GUIDs Archive](windows/known-folders/guids-archive.md)** ›
    3D Objects | `shell:::{}`

# [Powershell](Powershell.md)

# LaTeX

- **[Getting Started](latex/latex.md)** ›
    Project Structure | `texdoc PACKAGE_NAME`
- **[Symbols](latex/symbols.md)** ›
    Arrows | `\mathbb{NR}` → ℕℝ
- **[Mathematics](latex/math.md)** ›
    Norm | 
- **[Layout](latex/layout.md)** ›
    Hyphenation | `\!` `\,` `\:` `\;` `\quad` `\qquad`
- **[Useful Packages](latex/packages.md)** ›
    Lipsum Text | `\usepackage[utf8]{inputenc}`
- **[Modify Environments](latex/environments.md)** ›
    Modify Existing Environments | `\usepackage{etoolbox}`

## [Floating Bodies](latex/floats.md)
› Images | `\begin{figure}[htbp]`

- **[Tables](latex/tables.md)** ›
    Auto-Stretching Columns | `S[table-format = -3.0e-1]`

# Languages, Encodings

- **[Regular Expression](languages/regex.md)** ›
    Quantifiers | `(?in)user:(?<name>\S*)\s*key:(?<pwd>\S*)`
- **[Java](languages/java.md)** ›
- **[Git](languages/git.md)** ›
    Delete binary from history | `git clone git@github.com:Yetenol/$repo.git`
- **[Unicode](languages/unicode.md)** ›
    Character Sorting | `!` `+` `Ξ`
- **[Markdown](languages/markdown.md)** ›
    LaTeX Render | `$e^{i\pi}=-1$` → <img src="https://render.githubusercontent.com/render/math?math=e^{i\pi}=-1">
- **C › [GNU Debugger](languages/gdb.md)** ›
    Examinate Variables | `break`
- **[AutoHotkey v1](languages/autohotkey.md)** ›
    Get Program stdout | `Shell := ComObjCreate("WScript.Shell")`
- **Minecraft › [Datapacks](languages/minecraft.md)** ›
    Leash Decorations | `kill 	e[type=item,nbt={Item:{id:"minecraft:wool"}}]`

# Applications

- **[Excel](apps/excel.md)** ›
    Empty Range? | `=IF(SUMPRODUCT(--(A1:C4<>""))<>0,"not empty","empty")`
- **[OneNote](apps/onenote.md)** ›
    Mathematical Typesetting | `\displaystyle\bmatrix(1&2@a&b) `
- **[Obsidian](apps/obsidian.md)** ›
    Convert wikilinks to markdown
- **[Visual Studio Code](apps/vscode.md)** 
	Shell command keybindung

# Discussions

- **[Indentation: Tabs vs Spaces](discussion/indentation.md)**  