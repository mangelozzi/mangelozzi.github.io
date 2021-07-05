# Windows Tips

## FIX FILE CORRUPTION

1. Open `cmd.exe` as **Administrator**
2. `DISM.exe /Online /Cleanup-image /Restorehealth`
    - Wait until `The operation completed successfully.`
3. `sfc /scannow`
    - May get something like `Windows Resource Protection found corrupt files and successfully repaired them.`
