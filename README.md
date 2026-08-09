# CTF-writeup-11

CTF Writeup: Python Wrangling
This one hands you a Python script and basically dares you to actually read it before running it — the whole challenge lives inside understanding what the script's command-line options do.

How I Approached It
Got three files to work with: a script called ende.py, a plaintext password file pw.txt, and an encrypted flag file flag.txt.en. Instead of immediately running the script blind and hoping for the best, my first move was opening ende.py in an editor and skimming through it to see what it actually expected as input.

What Was Actually Going On
Reading through the script, it was clearly doing symmetric encryption/decryption work using base64 encoding layered with Fernet (which is a standard, authenticated symmetric encryption scheme built on top of AES). It accepted command-line flags to switch between encode and decode mode, and it prompted for a password at runtime to derive the actual encryption key. So this wasn't a "find the vulnerability" challenge at all — the script itself was working exactly as designed. The entire task was just correctly invoking it: knowing which flag meant "decode" and which file to point it at.

How I Solved It
I ran the script in decode mode against the encrypted flag file using its -d flag, which looked like python3 ende.py -d flag.txt.en in the terminal. When it prompted me for a password, I opened pw.txt, copied the password sitting inside, and pasted it in at the prompt. The script processed the file and printed the decoded flag straight to the terminal — no errors, no digging required, just correct usage.

What I Took Away From It
A good chunk of this challenge is just basic comfort running Python scripts from the command line and reading their expected arguments instead of guessing or panicking at unfamiliar code. It also reinforced a habit worth keeping generally: open and skim any script before you execute it, especially one you didn't write yourself — not just for security's sake here, but because it's usually the fastest way to actually understand what you're supposed to do with it.
