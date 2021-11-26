**Bytes Conversion Chart:**

| Bytes          | To change  |
| -------------- | ---------- |
| 0 or 1         | 1 Bit      |
| 8 Bits         | 1 Byte     |
| 1024 Bytes     | 1 Kilobyte |
| 1024 Kilobytes | 1 Megabyte |
| 1024 Megabytes | 1 Gigabyte |

**Shell Script:-**

 A shell script is a text file that **contains a sequence of commands for a UNIX-based operating system.** It is called a shell script because it combines a sequence of commands, that would otherwise have to be typed into the keyboard one at a time, into a single script.

---
mkdir a b c d

---

mkdir a/aa b/bb c/cc d/dd

---

touch a/aa/a.txt

---

one file copying into multiple folder =>
xargs -n 1 cp -v a/aa/a.txt <<<"b/bb c/cc d/dd"

---
