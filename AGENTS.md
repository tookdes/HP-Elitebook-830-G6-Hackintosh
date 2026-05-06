## Cursor Cloud specific instructions

This repository is a **Hackintosh EFI configuration** for HP Elitebook 830 G6 using the OpenCore bootloader. It is **not a software development project** — it contains only pre-compiled binaries and configuration files:

- `EFI/OC/config.plist` — OpenCore configuration (XML plist, the main editable file)
- `EFI/OC/Kexts/` — 30 pre-compiled macOS kernel extensions
- `EFI/OC/ACPI/` — Compiled ACPI SSDT patches (`.aml`)
- `EFI/OC/Drivers/` — UEFI drivers (`.efi`)
- `EFI/BOOT/BOOTx64.efi` — UEFI boot stub
- `SSDT/` — Original/dumped ACPI tables from the laptop firmware

### No build, lint, or test infrastructure

There are no programming languages, package managers, build systems, CI/CD pipelines, linters, or test suites. The only validation possible is XML well-formedness of `config.plist`:

```bash
xmllint --noout EFI/OC/config.plist
```

### No services to run

There are no runnable services or applications. The EFI directory is meant to be copied to a physical machine's EFI System Partition.
