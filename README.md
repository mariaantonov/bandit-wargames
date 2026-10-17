# OverTheWire: Bandit — Walkthrough & Command Reference 🐧

A structured technical journal documenting Linux command-line techniques, stream processing, binary inspection, and security fundamentals encountered during the [OverTheWire: Bandit](https://overthewire.org/wargames/bandit/) wargame challenges.

---

## 🧭 Repository Structure

- [`docs/levels-00-12.md`](docs/levels-00-12.md): Comprehensive walkthrough and syntax breakdown covering Levels 0 through 12.
- Additional level breakdowns and intermediate exploitation notes added incrementally as progress continues.

---

## 🛠️ Tooling & Core Commands Mastered

| Category | Commands Explored | Core Security & Systems Concepts |
| :--- | :--- | :--- |
| **Remote Access & Shell** | `ssh`, `exit` | Asymmetric key authentication, non-standard port connections (`-p 2220`), secure shell sessions. |
| **Directory & Path Navigation** | `pwd`, `cd`, `ls -la` | Directory tree traversals, parsing UNIX inode permissions, hidden dotfiles (`.*`). |
| **Edge-Case Path Handling** | `./-` (relative paths), `""` / `\` | POSIX dashed option parsing (`--`), whitespace escaping, argument delimiter disambiguation. |
| **File Identification & Inspection** | `cat`, `file`, `head`, `tail` | ASCII human-readable text validation vs. binary formats, magic byte header identification. |
| **Metadata & Filesystem Querying** | `find` | Predicate filters by user (`-user`), group (`-group`), exact byte sizing (`-size`), and non-executable states (`! -executable`). |
| **Pattern Search & Inspection** | `grep`, `strings` | Regular expression filtering, raw binary scanning, extracting printable contiguous ASCII sequences. |
| **Stream Filtering & Frequency** | `sort`, `uniq -u` | UNIX pipeline architecture (`\|`), stream aggregation, isolating singular unique records via adjacent duplicate matching. |
| **Data Representation & Decoding** | `base64 -d` | Radix-64 encoding/decoding, standard ASCII transport formatting vs. cryptographic encryption. |
| **Character Translation Ciphers** | `tr` | Symmetric substitution ciphers (ROT13 Caesar shifts), character class mapping, `stdin` redirection (`<`). |
| **Binary Carving & Archive Reversal** | `xxd -r`, `file`, `tar`, `gzip`, `bzip2` | Hexadecimal stream reconstitution, multi-tier recursive decompression, magic header verification. |

---

## ⚖️ Ethics & Writeup Policy

Per standard wargame etiquette, this repository highlights **methodology, POSIX syntax mechanics, underlying system primitives, and security edge cases** rather than publishing plaintext flag keys or spoilers.