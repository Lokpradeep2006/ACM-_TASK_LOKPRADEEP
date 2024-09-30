# ZIP Password Cracker

Here’s the Python script used for the task:

```python
import os
import subprocess

def extract_zip_hash(zip_filename, hash_output_filename):
    """Extracts hash from the given ZIP file."""
    if not os.path.isfile(zip_filename):
        print(f"Error: The ZIP file '{zip_filename}' does not exist.")
        return
    
    with open(hash_output_filename, 'w') as hash_file:
        subprocess.run(['zip2john', zip_filename], stdout=hash_file)
    print(f"Hash extracted to '{hash_output_filename}'.")

def crack_zip_password(hash_filename, wordlist_filename):
    """Cracks the ZIP password using John the Ripper."""
    if not os.path.isfile(hash_filename) or not os.path.isfile(wordlist_filename):
        print("Error: Hash file or wordlist file does not exist.")
        return

    subprocess.run(['john', '--wordlist=' + wordlist_filename, hash_filename])
    print("Password cracking initiated...")
    
    result = subprocess.run(['john', '--show', hash_filename], capture_output=True, text=True)
    print(f"Cracked password:\n{result.stdout.strip()}")

def main():
    zip_filename = "------"
    hash_output_filename = "--------"
    wordlist_filename = "rockyou.txt"  # Ensure this file exists

    extract_zip_hash(zip_filename, hash_output_filename)
    crack_zip_password(hash_output_filename, wordlist_filename)


How It Works
Extracting the Hash
The script first checks if the specified ZIP file exists. It uses the zip2john utility to extract the password hash and saves it to a file.

Cracking the Password
Using John the Ripper, the script attempts to crack the password by running it against a wordlist (like rockyou.txt). After the cracking process, it displays the cracked password.

Cracked Passwords
Upon executing the script, the password for the ZIP file "Trybreakingme.zip" was successfully cracked:

Cracked Password: softball3

The following base64-encoded text was found inside the ZIP file:

Rm9yZW5zaWNzIGlzIGZ1bg==

When decoded, it reads: "Forensics is fun".


