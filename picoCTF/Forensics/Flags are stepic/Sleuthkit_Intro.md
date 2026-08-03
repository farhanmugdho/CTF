# Sleuthkit Intro — picoCTF Forensics Write-up

## Challenge Information

- **Category:** Forensics
- **Difficulty:** Easy
- **File type:** Compressed disk image
- **Tools:** `file`, `gunzip`, `mmls`, `nc`

## Objective

A compressed disk image is provided. The challenge asks for the size of the Linux partition inside the image.

## Step 1: Check the Downloaded File

```bash
file disk.img.gz
```

The output should show that the file is compressed using Gzip.

## Step 2: Extract the Disk Image

```bash
gunzip disk.img.gz
```

Check the extracted file:

```bash
ls
file disk.img
```

## Step 3: Examine the Partition Table

Use `mmls`, which is part of The Sleuth Kit:

```bash
mmls disk.img
```

Example output:

```text
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

Slot      Start        End          Length       Description
000:      0000000000   0000000000   0000000001   Primary Table
001:      0000000000   0000002047   0000002048   Unallocated
002:      0000002048   0000204799   0000202752   Linux
```

The Linux partition length is:

```text
202752
```

## Step 4: Connect to the Challenge Server

Use the Netcat command provided by your picoCTF instance:

```bash
nc saturn.picoctf.net <PORT>
```

Replace `<PORT>` with the port number shown in the challenge.

Enter the Linux partition size:

```text
202752
```

The server will verify the answer and return the flag.

## Flag

```text
picoCTF{mm15_f7w!}
```

## Key Learning

The `mmls` command displays the partition layout of a disk image, including the starting sector, ending sector, and length of each partition.

## Disclaimer

This write-up is intended for educational purposes and legal CTF environments only.
