# Lookey Here — picoCTF Forensics Write-up

## Challenge Information

- **Category:** Forensics
- **Difficulty:** Easy
- **File type:** Text file
- **Tools:** `cat`, `grep`, `strings`

## Objective

A large text file named `anthem.flag.txt` is provided. The goal is to find the hidden flag inside the file.

## Step 1: Check the File

```bash
file anthem.flag.txt
```

## Step 2: Display the Contents

```bash
cat anthem.flag.txt
```

The file contains a large amount of text, so manually reading every line is inefficient.

## Step 3: Search for the Flag

Because picoCTF flags begin with `picoCTF`, use `grep`:

```bash
grep "picoCTF" anthem.flag.txt
```

You can also perform a case-insensitive search:

```bash
grep -i "pico" anthem.flag.txt
```

To display only the flag pattern:

```bash
grep -o 'picoCTF{[^}]*}' anthem.flag.txt
```

## Flag

```text
picoCTF{gr3p_15_@w3s0m3_4c479940}
```

## Key Learning

The `grep` command is useful for quickly finding specific words or patterns inside large text files.

## Disclaimer

This write-up is intended for educational purposes and legal CTF environments only.
