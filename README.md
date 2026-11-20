# 🔐 Week 3: Password Cracking with John the Ripper & Networkwalks Tools

## 📌 Project Overview
This repository documents my Week 3 Cybersecurity & Ethical Hacking project tasks at **Networkwalks**. The objective of this lab was to understand how password-protected PDF documents store cryptographic hashes and perform authorized dictionary-based password recovery using both **John the Ripper (JtR)** on Kali Linux and **Networkwalks** web utilities.

---

## 🛠️ Module 1: Password Cracking with John the Ripper (Kali Linux)

### Steps Performed:
1. Navigated to the Week 3 project directory in Kali Linux.
2. Extracted the `$pdf$` hashes from the three encrypted PDF files using `pdf2john`:
   - `pdf2john 'My Locked PDF1.pdf' > hash1.txt`
   - `pdf2john 'My Locked PDF2.pdf' > hash2.txt`
   - `pdf2john 'My Locked PDF3.pdf' > hash3.txt`
3. Executed dictionary attacks using `john` and verified the recovered credentials with `john --show`:
   - **`My Locked PDF1.pdf`** $\rightarrow$ Password: `good-luck`
   - **`My Locked PDF2.pdf`** $\rightarrow$ Password: `password1`
   - **`My Locked PDF3.pdf`** $\rightarrow$ Password: `1qaz2wsx`
4. Unlocked all three protected PDFs to verify access and capture the lab flags.

### Screenshots:
<img width="682" height="398" alt="jtr-pdf1" src="https://github.com/user-attachments/assets/4feb0f2d-dd38-42ef-8cac-622585e6471a" />

<img width="721" height="398" alt="jtr-pdf2" src="https://github.com/user-attachments/assets/b0b26ac5-a589-4bf2-ba4a-b02b66feb69b" />

<img width="718" height="398" alt="jtr-pdf3" src="https://github.com/user-attachments/assets/fcd2323e-2e49-4c56-806e-831556c4334d" />





---

## 🌐 Module 2: Password Cracking with Networkwalks Web Tools

### Steps Performed:
1. Opened the **Networkwalks Hash Calculator** and uploaded `My Locked PDF1 (for NW Tools Lab WK3-PM2).pdf` to extract its `$pdf$` hash locally in the browser.
2. Pasted the extracted hash into the **Networkwalks Password Cracker** and executed a dictionary attack.
3. Successfully recovered the password (`password1`) and verified access to the document.

### Screenshots:
<img width="712" height="443" alt="nw-hash-calculator" src="https://github.com/user-attachments/assets/fa396a1e-fb28-455b-bf72-e8b95bfd3abe" />

<img width="681" height="440" alt="nw-password-cracker" src="https://github.com/user-attachments/assets/44e1ef64-b343-41c1-a814-5f32ff5b6b56" />



---

## 💡 Troubleshooting & Key Takeaways
- **Issue 1 (`pyhanko` Missing in Kali Linux):** Running `pdf2john` initially failed with a `pyhanko is missing` error, and `apt` could not locate `python3-pyhanko`.
  - **Solution:** Installed the dependency using `pip install --user pyhanko --break-system-packages`, which enabled `pdf2john` to extract all PDF hashes cleanly.
- **Issue 2 (Wordlist Exhausted in Browser Cracker):** Testing a hash with a custom word (`good-luck`) against the built-in 100-word list resulted in `ACCESS DENIED`.
  - **Solution:** Extracted the hash from the dedicated Module 2 PDF (`My Locked PDF1 (for NW Tools Lab WK3-PM2).pdf`), matching the built-in wordlist and recovering the password immediately.
- **Security Lesson:** Common words and keyboard patterns (`password1`, `1qaz2wsx`, `good-luck`) are cracked in seconds. Sensitive files should always be protected with long, complex passphrases (12+ mixed characters).

---
*Disclaimer: All testing was conducted strictly for educational purposes in an authorized Networkwalks lab environment.*
