see wiki: https://github.com/jackson5-sec/ShimDB/wiki/Creating-FixIT-SDBs

# Shim Database In-Memory Patch Persistence
A persistence technique used by nations and organized crime actors

Utilizes sdb files to patch memory addresses at runtime using an undocumented Microsoft feature outside of the Application Compatibility Toolkit

There are two ways to install SDB files.

1. Using Microsoft's sdbinst (sdbinst.exe -p `<path to file.sdb>` with admin privs!) **This is not Opsec safe** as it leaves behind an Uninstaller in Control Panel

2. Using sdb-explorer (sdb-explorer.exe -r `<path to file.sdb>` -a `<application you are shimming like spoolsv.exe>` **This is safer** does not leave behind uninstaller and doesn't copy the sdb to a default location in C:\Windows

# App Compat Toolkit Tricks

**x64hideRegistry**: Will hide registry entries and redirect them to HKLM\Software\Microsoft\Windows NT\CurrentVersion\EFS (this is usually empty) for reg.exe and regedit.exe

1. HKLM\Software\Microsoft\Windows NT\CurrentVersion\Custom

2. HKLM\Software\Microsoft\Windows NT\CurrentVersion\InstalledSDB

3. HKLM\Software\Microsoft\Windows\CurrentVersion\Run

4. Attempts to use deprecated fix to hide C:\temp\hidden and redirect it to C:\temp for x64 cmd.exe, powershell.exe and explorer.exe (This will only work for certain windows versions like 8.1)

**x86hideRegistry**: Will hide registry entries and redirect them to HKLM\Software\Microsoft\Windows NT\CurrentVersion\EFS (this is usually empty) for reg.exe and regedit.exe

1. HKLM\Software\Microsoft\Windows NT\CurrentVersion\Custom

2. HKLM\Software\Microsoft\Windows NT\CurrentVersion\InstalledSDB

3. HKLM\Software\Microsoft\Windows\CurrentVersion\Run

4. Attempts to use deprecated fix to hide C:\temp\hidden and redirect it to C:\temp for x86 cmd.exe, powershell.exe and explorer.exe (This should work on everything pre Win10/2016)

## References

This technique is a modified version of: https://www.fireeye.com/blog/threat-research/2017/05/fin7-shim-databases-persistence.html

For more information checkout the original tool and creator: https://github.com/evil-e/sdb-explorer


## Jackson5
