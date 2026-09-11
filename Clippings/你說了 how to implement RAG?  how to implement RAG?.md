---
title: "how does inode work?"
source: "https://gemini.google.com/app/3a3b38927f7ff81f"
tags:
  - "clippings"
---
To understand how an inode links to a file's data, it helps to realize one fundamental truth: **the inode IS the file**.

What we casually call "a file" is actually split into three distinct pieces on your disk that are connected by numbers—like a chain of pointers.

### The 3 Pieces of a File

Think of a file as three separate layers:

```
┌─────────────────────────┐      ┌─────────────────────────┐      ┌─────────────────────────┐
│     1. DIRECTORY        │      │       2. INODE          │      │     3. DATA BLOCKS      │
│   (Human-friendly Name) │      │       (Metadata)        │      │      (Raw Payload)      │
├─────────────────────────┤      ├─────────────────────────┤      ├─────────────────────────┤
│                         │      │ Inode Number: 1422119   │      │                         │
│  "report.pdf" ──────────┼─────►│ File Size: 2.4 MB       │      │ [Block #88102] "PDF..." │
│                         │      │ Owner: User             │─────►│ [Block #88103] "data.." │
│                         │      │ Block List:             │      │ [Block #88104] "end..." │
│                         │      │  -> 88102, 88103, 88104 │      │                         │
└─────────────────────────┘      └─────────────────────────┘      └─────────────────────────┘
```

- **The Directory Entry (The Label):** Maps the human-readable file name (`report.pdf`) to an **Inode Number** (`1422119`).

- **The Inode (The Identity):** Stores the metadata and an explicit list of **Data Block Numbers** (`88102`, `88103`, `88104`).

- **The Data Blocks (The Content):** The actual bytes (text, images, PDFs) written across 4 KB storage blocks on the physical disk.

### How They "Know" Each Other

They don't need to "know" each other through magic—they find each other using **array indices (numbers)**.

#### Step 1: Name 
$$
→
$$
 Inode Number

A directory is just a special file that contains a simple lookup table. When you type `cat report.pdf`, the operating system opens the current directory and reads its table:

| Name | Inode Number |
| --- | --- |
| `notes.txt` | 50211 |
| **`report.pdf`** | **1422119** |
| `script.py` | 89104 |

The OS finds that `report.pdf` corresponds to **Inode #1422119**.

#### Step 2: Inode Number 
$$
→
$$
 Inode Metadata

The disk has an area called the **Inode Table**, which is a massive array of inodes indexed by number: `[Inode #0, Inode #1, Inode #2 ... Inode #1422119]`.

The operating system jumps directly to slot **1422119** in the array. Inside that inode, it finds:

- Permissions: `rw-r--r--`

- Size: `2,450,112 bytes`

- **Block Pointers:** `[88102, 88103, 88104]`

#### Step 3: Inode Pointers 
$$
→
$$
 Physical Disk Data

The inode explicitly lists the exact sector numbers on your SSD or Hard Drive where the data is stored.

The OS tells the storage controller: *"Read physical blocks 88102, 88103, and 88104."* The drive reads those sectors and returns the raw file content to your application.

### Real-World Analogy: The Coat Check

Imagine going to a museum coat check:

- **File Name (`report.pdf`):** Your paper receipt with your name on it.

- **Inode Number (`1422119`):** The coat check ticket number (**#42**) printed on that receipt.

- **Inode:** Slot **#42** on the coat rack framework. It doesn't hold your coat directly; it holds a tag that says *"Your jacket is hanging in Locker 88 and Locker 89"*.

- **Data Blocks:** Lockers **88** and **89**, where your actual physical jacket (the data) is sitting.

If you throw away the paper receipt (delete the file name), coat check ticket **#42** and the jacket in Locker **88** still exist. But without the receipt pointing to ticket **#42**, you no longer have a way to ask for it.