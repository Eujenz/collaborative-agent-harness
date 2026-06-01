# Windows PowerShell UTF-8

## Rule

When PowerShell commands may handle non-ASCII text, set UTF-8 explicitly before running the command.

Use this preflight in the same command invocation:

```powershell
[Console]::OutputEncoding = [System.Text.UTF8Encoding]::new($false)
[Console]::InputEncoding = [System.Text.UTF8Encoding]::new($false)
$OutputEncoding = [System.Text.UTF8Encoding]::new($false)
chcp 65001 | Out-Null
```

## Reading Files

Prefer explicit encodings:

```powershell
Get-Content -LiteralPath $path -Encoding UTF8
```

If output is garbled, inspect whether the file is actually UTF-8, UTF-8 with BOM, UTF-16 LE, Big5, or CP950.

## Writing Files

Prefer explicit UTF-8:

```powershell
Set-Content -LiteralPath $path -Value $text -Encoding UTF8
```

Do not normalize file encoding unless the user asked or the task requires it.

## Diagnostics

Useful checks:

```powershell
$PSVersionTable.PSVersion
[Console]::OutputEncoding
[Console]::InputEncoding
chcp
```

## Notes

- PowerShell 7 defaults are usually safer than Windows PowerShell 5.1.
- Windows PowerShell 5.1 `-Encoding UTF8` may write UTF-8 with BOM.
- External tools such as Git, Python, Node, and legacy CLI programs may still emit a different encoding.
