# Bandit Levels 00 to 04 Walkthrough & Core Concepts

---

## Level 0 to Level 1: Remote Access & Encrypted Channels

Objective: Establish an authenticated, encrypted interactive shell session with the remote game server host.

Commands:
ssh bandit0@bandit.labs.overthewire.org -p 2220
ls
cat readme
exit

Core Concepts Learned:
1. Transport Layer Port Addressing (-p 2220): Standard SSH daemons listen on TCP port 22. Labs and servers often remap SSH to alternative ports like 2220 to avoid scanner noise or conflicts. The -p flag forces OpenSSH to target port 2220.
2. Host Authentication & Fingerprint Verification: On initial connection, SSH warns that the authenticity cannot be established and checks the remote public key against ~/.ssh/known_hosts to protect against Man-in-the-Middle (MitM) attacks.
3. Standard File Output (cat): The cat utility reads files sequentially and streams their contents to standard output (stdout).

---

## Level 1 to Level 2: Dashed Filenames & Argument Parsing

Objective: Read the contents of a file named "-" in the home directory.

Commands:
cat ./-
cat -- -

Core Concepts Learned:
1. POSIX Option Parsing: CLI utilities treat tokens starting with "-" as options/flags rather than file arguments.
2. Special Meaning of Single Dash (-): In tools like cat, a lone "-" represents stdin (standard input), causing the shell to wait for keyboard input rather than opening a file.
3. Path Disambiguation (./-): Adding the relative path prefix "./" prevents the parser from reading "-" as a flag because the argument starts with ".".
4. End-of-Options Delimiter (--): The double dash tells the parser that all subsequent arguments are strictly positional operands.

---

## Level 2 to Level 3: Spaces and Special Characters in Filenames

Objective: Read a file titled "spaces in this filename".

Commands:
cat "spaces in this filename"
cat spaces\ in\ this\ filename

Core Concepts Learned:
1. Shell Tokenization & Word Splitting: Bash uses whitespace to separate arguments. Without quotes or backslash escapes, cat attempts to open four separate files instead of one.

---

## Level 3 to Level 4: Hidden Files & Directory Navigation

Objective: Locate and extract the key hidden in the "inhere" directory.

Commands:
cd inhere
ls -la
cat .hidden

Core Concepts Learned:
1. Unix Dotfiles: Files prefixed with "." are treated as hidden by default convention. The -a flag instructs ls to display all directory contents without filtering out dotfiles.

---

## Level 4 to Level 5: Binary vs. Human-Readable Inspection

Objective: Identify the single human-readable ASCII file among multiple binary files.

Commands:
cd inhere
file ./*
cat ./-file07

Core Concepts Learned:
1. Magic Numbers & MIME Detection (file): Linux file extensions are arbitrary labels. The file utility checks file headers, magic numbers, and byte encodings (ASCII, UTF-8, binary) to safely classify contents before displaying them.