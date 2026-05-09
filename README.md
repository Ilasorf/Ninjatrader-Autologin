# NinjaTrader 8 Auto Login

Tired of typing your password every time you open NinjaTrader? This tool does it for you automatically.

---

## Files included

- **Setup.bat** — run once to save your credentials
- **Login.bat** — use every day to launch NinjaTrader automatically

---

## Is it safe?

Yes. Your password is saved by the Windows operating system in the **Credential Manager** — the same system Chrome uses to remember your website passwords. **Your data never leaves your PC**, no internet connection, no external servers.

The clipboard is always cleared immediately after use — **even if an error or crash occurs** — so your password is never left exposed.

The `.bat` files contain PowerShell code encoded in base64. To verify what they do, just paste the content of either file into ChatGPT, Claude or any other AI and ask *"what does this script do?"* — it will decode and explain everything in plain language in seconds.

---

## Installation

1. Download both files (`Setup.bat` and `Login.bat`) and place them in the same folder, for example on your Desktop
2. Double-click **Setup.bat** — a small window will open where you enter your NinjaTrader email and password. You can also paste your password with Ctrl+V. Click Save and close
3. From now on, double-click **Login.bat** every time you want to open NinjaTrader — it will launch it and enter your password automatically

> **After double-clicking Login.bat, do not touch the mouse or keyboard for a few seconds** — the script needs to find the login window and enter your password. Once NinjaTrader is fully loaded you can use it normally.

> **That's it.** No installation, no admin rights required, no additional software.

---

## Notes

- **Non-standard installation path:** the tool searches for NinjaTrader automatically in several locations on your PC. If it cannot find it, it will show an error message — in that case, create a plain text file called `NT_Path.txt` in the same folder as `Login.bat`, open it with Notepad, and type or paste the full path to your NinjaTrader.exe on a single line, for example:
  ```
  D:\Trading\NinjaTrader 8\bin\NinjaTrader.exe
  ```
  Save the file and run `Login.bat` again.

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
