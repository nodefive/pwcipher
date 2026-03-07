# pwcipher

**pwcipher** is a professional, lightweight, and secure command-line password manager. It utilizes **SQLCipher** to provide transparent 256-bit AES encryption for your SQLite database, ensuring your credentials remain safe even if the database file is compromised.

## Key Features

- 🔐 **Pro Encryption**: Powered by [SQLCipher](https://github.com/sqlcipher/sqlcipher) with 256-bit AES encryption.
- 🎨 **Elegant CLI**: A high-end, colorized interface with perfect alignment and intuitive flow.
- 📝 **Native Multi-line Support**: The `INFO` field supports real multi-line text—ideal for 2FA backup codes, security questions, or private notes.
- 📂 **Flexible Configuration**: No hardcoded paths; your settings are stored in `~/.pwcipherconf`.
- 🔍 **Smart Search**: Quickly find accounts by name or specific ID.
- 🛠️ **Advanced Rekeying**: Seamlessly change your master password, encrypt a plaintext database, or decrypt to standard SQLite.
- 🛡️ **Full CRUD**: Add, Edit, Delete, and List operations with professional safety confirmations.

## Security: Why SQLCipher?

Unlike standard SQLite, which stores data in plaintext, **pwcipher** uses SQLCipher to encrypt every page of the database file. 

- **Algorithm**: 256-bit AES encryption.
- **Key Derivation**: Uses PBKDF2 with a high iteration count.
- **Page-level Encryption**: Ensures that no metadata or structure is visible without the master key.

Learn more at the official [SQLCipher GitHub Page](https://github.com/sqlcipher/sqlcipher).

---

## Screen Examples

### Searching for an Entry
`pwcipher` displays results in a structured, perfectly aligned "Pro" format:

```text
 [ACCOUNT] GOOGLE ADMIN              (ID: 52)
 ------------------------------------------------
  LOGIN           : admin@google.com
  PASS            : somenicepass
  URL             : https://account.google.com
  INFO            : Example of an account entry
                    This field is reserved for additional information
                    The 2FA example codes are:
                    4829 3012
                    9012 3456
                    1122 3344
                    5566 7788
```

---

## Installation

### 1. Prerequisites
You must have the `sqlcipher` command-line tool installed.

- **macOS (Homebrew)**: `brew install sqlcipher`
- **Ubuntu/Debian/WSL**: `sudo apt update && sudo apt install sqlcipher`
- **Fedora**: `sudo dnf install sqlcipher`
- **Arch Linux**: `sudo pacman -S sqlcipher`

### 2. Setup
Download the script and make it executable:

```bash
chmod +x pwcipher
./pwcipher
```
On the first run, the **Initial Setup** wizard will guide you through creating your database and setting your master password.

---

## Usage

| Command | Description |
| :--- | :--- |
| `./pwcipher --help` | Display detailed help and instructions. |
| `./pwcipher [TERM]` | Search for an account name or a specific ID. |
| `./pwcipher -a` | **Add** a new account entry. |
| `./pwcipher -e [ID]` | **Edit** an existing account (leave fields blank to skip). |
| `./pwcipher -d [ID]` | **Delete** an account entry (requires confirmation). |
| `./pwcipher -f` | **List** the entire database contents. |
| `./pwcipher -r` | **Rekey, Encrypt, or Decrypt** the database. |
| `./pwcipher -w` | **Wipe** all database entries (Dangerous!). |

### Advanced: Handling the INFO Field
When adding or editing the **INFO** field:
1. Type your text.
2. Press **Enter** for as many new lines as you need.
3. Press **Ctrl+D** on a new line to **Save and Finish**.

### Advanced: Rekeying and Decryption
Use the `-r` option to enter the Encryption Settings menu:
- **Change Password**: Enter and confirm your new password.
- **Encrypt**: If your DB is currently plaintext, use this to set a password.
- **Decrypt**: Leave the new password field **blank** and type `DECRYPT` to remove all encryption.

---

## License
Distributed under the MIT License. See `LICENSE` for more information.
