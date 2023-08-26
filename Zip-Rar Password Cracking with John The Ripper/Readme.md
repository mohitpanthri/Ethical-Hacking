# Zip/Rar password cracking with John the Ripper

Crack the password of attached file using **John the Ripper**:
<br>
a) using automatic password generation 
<br>
b) using word dictionary

## What is John the Ripper?
John the Ripper is a popular password cracking tool that can be used to perform brute-force attacks using different encryption technologies and helpful wordlists. 
It's often what pen-testers and ethical hackers use to find the true passwords behind hashes.

## REQUIREMENTS 
- KALI LINUX
- VMware.
- Encypted Zip/Rar File

### Step 1
Download the Zip/Rar file to your kali linux.

<img src="https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/1da5ed25-d93d-4a2c-a808-a6be9922b32b" alt="image" width="500"/>

<hr>


### Step 2
Now, we will use use ``zip2John`` which is a part of the John the ripper to get the password hashes.
Also, make sure to save the password hashes to a ``txt`` file.

- If you are using Zip file write:
  ```
  zip2john GradedLab1.zip > hash.txt
  ```
- If you are using Rar file write:
  ```
  rar2john GradedLab1.rar > hash.txt
  ```

<img src="https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/77419b1c-b8f6-4aea-b1f1-3cb900687ee7" alt="image" width="700" />

<img src="https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/0d6fb5f1-17e4-4603-85a9-c80b8c439f06" alt="image" width="500"/>

<hr>

### Step 3
Now, we can start with the password cracking process.
<br>
We can do this in two ways:

1. Using Automatic password generation
For this use the below command.
```
john -incremental hash.txt
```
<img src="https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/43abd8b4-fc0e-4a7f-aea0-27ecda21c328" alt="image" width="700"/>

2. Using Word Dictionary

   ```
   john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
   ```

   or you can simply write the below command.
   ```
   john hash.txt
   ```

<img src="https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/58baedc2-5bca-4f46-a149-abb5aac7b6a1" alt="image" width="700"/>

**Note:** It will take some time to complete the process.

<hr>

### Step 4
When the john stops you will be able to see the password of the file (``CSF446`` in my case).

<img src="https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/94196464-f851-446a-ba90-3c38be6975ea" alt="image" width="800"/>

<hr>

### Step 5
Now you can use that password to open the encrypted file.

<img src="https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/9da792f3-5b30-4c00-8f1d-a0e85eff27ae" alt="image" width="500"/>
<br>
<img src="https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/b551a907-d128-47e7-8d43-eb3759bf3faa" alt="image" width="500"/>

<img src="https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/7b115406-2525-40d3-bcf7-b937bc4cd2d2" alt="image" width="500"/>

<img src="https://github.com/mohitpanthri/Ethical-Hacking/assets/99413629/66a93da8-e0a1-420f-b01f-a33068f7a61d" alt="image" width="500"/>

<br>
<br>
<br>
<br>

<div align="center">
  
[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&size=30&pause=1000&color=F7F7F7&width=435&lines=%E2%9D%A4%EF%B8%8F+Happy+Hacking+%E2%9D%A4%EF%B8%8F)](https://git.io/typing-svg)

</div>
