# QuantumCTF — Multi-Level Capture The Flag
**Date:** July 3, 2024  
**Type:** Group project

**Repository:** [github.com/Aveira-jdk/ctf-challange-acc/blob/main/v8.sh
](https://github.com/Aveira-jdk/ctf-challange-acc/blob/main/v8.sh
)

## Concept
QuantumCTF is a structured CTF designed to simulate realistic attacker workflows.  
Instead of just trivia challenges, it walks you through real techniques:
- Enumeration
- Hidden data extraction
- Decoding and reversing
- Brute forcing
- Privilege escalation

It was deployed in Cywaria as a capstone-style challenge set.

---

## Challenge Design
The CTF is broken into difficulty tiers (Easy / Medium / Hard).  
Each tier chains levels, and each level gives credentials or access to unlock the next.

### Easy Tier (Onboarding / Fundamentals)
Focus: basic analyst tradecraft.  
Examples:
- **CTF Archive**  
  Extract layered archives to reveal the next clue.
- **Find Obfuscated Name**  
  Deobfuscate or decode strings / names hidden in files.
- **Maze**  
  Navigate a generated multi-level directory “maze” to hunt a file placed in only one correct path.
- **Sort / Unique / Decode**  
  Take noisy text, identify the unique meaningful value, base64/ROT decode it.
- **Steganography**  
  Recover a hidden message embedded in an HTML-like file or image using stego tools.
- **Metadata inspection (Exif/headers)**  
  Extract hidden info from file metadata.

### Medium Tier (Applied attacker workflow)
Focus: thinking like an adversary, doing work instead of guessing.
Examples:
- Brute force against a small “locked box” binary that only opens with the correct password.
- Decoding chained encodings (hex → base64 → ROT, etc.).
- Traversing deep directory structures with randomized placement of the true target.
- Rebuilding archives in the reverse order they were nested.

### Hard Tier (Privilege & post-exploitation concepts)
Focus: system-level access and escalation.
Examples:
- Privilege escalation via misconfigured sudoers entries.
- Recovering protected flags behind interactive programs.
- Using wordlists and brute forcing where a password check is hardcoded in a compiled binary.
- Inspecting hidden files in a user’s home directory to recover secrets.
- Working with hashed/encoded secrets, not just plaintext.

---

## My Role
I built and automated the environment:
- Wrote the main provisioning script in Bash.
- Automatically created user accounts (`level1`, `level2`, …, `level7`, etc.) and assigned passwords.
- Created and placed all artifacts for each challenge:
  - Steganography HTML with hidden data.
  - Multi-level nested archives with encoded flags.
  - The compiled C brute-force challenge binary.
  - A fake “web page” with a hidden flag in HTML source.
  - A SHA-512 hash challenge that must be cracked from a provided wordlist.
  - Bytecode/base64 challenges that force decoding to continue.
  - A restricted sudo / privilege escalation scenario where a low-priv user can run a specific editor with elevated rights.
- Set up a final “root-only” flag file for post-escalation validation.

---

## Technologies Used
- Bash scripting for provisioning and environment setup  
- C (compiled with gcc) for the brute-force binary challenge  
- Linux user management and permissions  
- Hashcat and hashing primitives (SHA-512-style cracking flow)  
- Archive manipulation (tar, gzip, zip, bzip2)  
- Basic steganography tooling  
- sudoers misconfiguration to model privilege escalation

---

## Why This Matters
QuantumCTF demonstrates:
- Understanding of basic offensive security techniques and how to teach them.
- Ability to build training infrastructure programmatically, not by hand.
- Practical escalation scenarios instead of purely theoretical security questions.

