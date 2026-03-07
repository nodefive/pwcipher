# pwcipher

**pwcipher** is a refined, lightweight, and secure command-line password manager. It utilizes **SQLCipher** to provide transparent 256-bit AES encryption for your SQLite database, ensuring your credentials remain safe even if the database file is compromised.

## Key Features

- 🔐 **Strong Encryption**: Powered by [SQLCipher](https://github.com/sqlcipher/sqlcipher), providing industry-standard security.
- 🎨 **Colorized CLI**: A clean, readable interface with high-contrast color coding for different fields.
- 📝 **Multi-line Support**: The `INFO` field supports multiple lines of text—perfect for 2FA backup codes, security questions, or notes.
- 📂 **No Hardcoded Paths**: Configuration is stored in `~/.pwcipherconf`, allowing you to place your database anywhere.
- 🔍 **Fast Search**: Quickly find accounts by name or ID.
- 🛠️ **Full CRUD**: Add, Edit, Delete, and List operations with built-in safety confirmations.

## Security: Why SQLCipher?

Unlike standard SQLite, which stores data in plaintext, **pwcipher** uses SQLCipher to encrypt every page of the database file. 

- **Algorithm**: 256-bit AES encryption.
- **Key Derivation**: Uses PBKDF2 with a high iteration count.
- **Page-level Encryption**: Ensures that no metadata or structure is visible without the master key.

Learn more at the official [SQLCipher GitHub Page](https://github.com/sqlcipher/sqlcipher).

---

## Screen Examples

### Searching for an Entry
When searching for an account, `pwcipher` displays results in a structured, easy-to-read format:

```text
 ACCOUNT: GOOGLE ADMIN              ID: 52
 ------------------------------------------------
  LOGIN    : admin@google.com
  PASS     : somenicepass
  URL      : https://account.google.com
  INFO     : Example of an account entry
             This field is reserved to additional information
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

- **macOS**: `brew install sqlcipher`
- **Ubuntu/Debian/WSL**: `sudo apt update && sudo apt install sqlcipher`
- **Fedora**: `sudo dnf install sqlcipher`
- **Arch Linux**: `sudo pacman -S sqlcipher`

### 2. Setup
Download the script and make it executable:

```bash
chmod +x pwcipher
./pwcipher
```
On the first run, the script will guide you through the initial setup, asking for your preferred database path and encryption password.

---

## Usage

| Command | Description |
| :--- | :--- |
| `pwcipher --help` | Display detailed help and instructions. |
| `pwcipher [TERM]` | Search for an account name or a specific ID. |
| `pwcipher -a` | **Add** a new account entry. |
| `pwcipher -e [ID]` | **Edit** an existing account by ID (press Enter to skip fields). |
| `pwcipher -d [ID]` | **Delete** an account entry (requires confirmation). |
| `pwcipher -f` | **List** all entries in the database. |
| `pwcipher -w` | **Wipe** all contents from the database (Dangerous!). |

### Handling the INFO Field
When adding or editing the **INFO** field:
1. Type your text.
2. Press **Enter** for new lines.
3. Press **Ctrl+D** on a new line to save and finish.

---

## License
Distributed under the MIT License. See `LICENSE` for more information.
