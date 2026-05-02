# NinjaTrader 8 Auto Login

Tired of typing your password every time you open NinjaTrader? This tool does it for you automatically.

---

## Is it safe?

Yes. Your password is saved by the Windows operating system in the **Credential Manager** — the same system Chrome uses to remember your website passwords. **Your data never leaves your PC**, no internet connection, no external servers.

The clipboard is always cleared immediately after use — **even if an error or crash occurs** — so your password is never left exposed.

The code is readable by anyone — unlike a regular program (.exe), you can open the files with any text editor (e.g. Notepad) and see exactly what they do. If you want to verify, copy the content and paste it into ChatGPT, Claude or any other AI — it will tell you in seconds if there is anything suspicious.

---

## Installation

1. Download both files (`Setup.bat` and `Login.bat`) and place them in the same folder, for example on your Desktop
2. Double-click **Setup.bat** — a small window will open where you enter your NinjaTrader email and password. You can also paste your password with Ctrl+V. Click Save and close
3. From now on, use **Login.bat** every time you want to open NinjaTrader — it will launch it and enter your password automatically

> **That's it.** No installation, no admin rights required, no additional software.

---

## Notes

- **Non-standard installation path:** you don't need to do anything special — the tool searches automatically in several locations on your PC. Only in very rare cases will it show a message with instructions to set the path manually by creating a `NT_Path.txt` file in the same folder as `Login.bat`, containing the full path to NinjaTrader.exe (e.g. `D:\Trading\NinjaTrader 8\bin\NinjaTrader.exe`)
- **Password change:** just run `Setup.bat` again
- **After a reboot:** credentials are permanently stored, just use `Login.bat` as usual

---

## Requirements

- Windows 10 or 11
- NinjaTrader 8
- PowerShell 5 (already included in Windows 10/11)

---

## Tested on

NinjaTrader 8 installed in the standard path (`C:\Program Files\NinjaTrader 8`). For non-standard installations the automatic search should work, but it has not been tested on every possible configuration. If you have issues or want to share your experience, open an issue or leave a comment — your feedback helps improve the tool for everyone.

---

## How it works (for the curious)

`Setup.bat` opens a small graphical window to collect your credentials and saves them to the Windows Credential Manager using `cmdkey`.

`Login.bat` retrieves the encrypted password from the Credential Manager, launches NinjaTrader, waits for the login window to appear, and injects the password using **UI Automation** — the native Windows API designed for this purpose. The clipboard is always cleared immediately after use via a `finally` block — this guarantees it happens even in case of an error or crash, so your password is never left in the clipboard.

---

☕ If you find this tool useful, buy me a coffee! → [ko-fi.com/ilasorf](https://ko-fi.com/ilasorf)

