# Enhance — picoCTF Forensics Write-up

## Challenge Information

- **Category:** Forensics
- **Difficulty:** Easy
- **File type:** SVG image
- **Tools:** `file`, `cat`, `strings`, text editor

## Objective

A downloadable image is provided. The goal is to inspect the image file and recover the hidden flag.

## Step 1: Check the File Type

```bash
file drawing.flag.svg
```

Although the file looks like an ordinary image, it is actually an **SVG file**.

SVG files are XML-based, so they may contain readable text inside their source code.

## Step 2: Read the SVG Source

```bash
cat drawing.flag.svg
```

You can also open it using a text editor:

```bash
nano drawing.flag.svg
```

## Step 3: Search for Readable Strings

```bash
strings drawing.flag.svg
```

Search specifically for the picoCTF flag:

```bash
strings drawing.flag.svg | grep -i "pico"
```

The flag characters may be separated inside different SVG tags. Combine them in the correct order.

## Flag

```text
picoCTF{3nh4nc3d_aab729dd}
```

## Key Learning

SVG images should always be inspected as text because they are XML-based and may contain hidden readable information.

## Disclaimer

This write-up is intended for educational purposes and legal CTF environments only.
