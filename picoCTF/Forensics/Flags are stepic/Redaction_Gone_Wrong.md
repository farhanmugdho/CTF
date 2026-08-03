# Redaction Gone Wrong — picoCTF Forensics Write-up

## Challenge Information

- **Category:** Forensics
- **Difficulty:** Easy
- **File type:** PDF
- **Tools:** `file`, `pdftotext`, `grep`, PDF reader

## Objective

A PDF document contains blacked-out or redacted information. The goal is to recover the text hidden underneath the black boxes.

## Step 1: Check the File Type

```bash
file Financial_Report_for_ABC_Labs.pdf
```

## Step 2: Convert the PDF into Text

Use `pdftotext` to extract the document text:

```bash
pdftotext Financial_Report_for_ABC_Labs.pdf extracted.txt
```

## Step 3: Read the Extracted Text

```bash
cat extracted.txt
```

Search for the flag:

```bash
grep "picoCTF" extracted.txt
```

Another method is to open the PDF in an editable document application. The black boxes may only be shapes placed over the original text, meaning the hidden text may still remain inside the file.

## Flag

```text
picoCTF{C4n_Y0u_S33_m3_fully}
```

## Key Learning

Covering text with a black shape does not securely remove the original information. Proper redaction must permanently delete the hidden content.

## Disclaimer

This write-up is intended for educational purposes and legal CTF environments only.
