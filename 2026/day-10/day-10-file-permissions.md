# Day 10 – File Permissions & File Operations Challenge

## Task
Master file permissions and basic file operations in Linux.

- Create and read files using `touch`, `cat`, `vim`
- Understand and modify permissions using `chmod`

---

## Challenge Tasks

### Task 1: Create Files 

1. Create empty file `devops.txt` using `touch`
2. Create `notes.txt` with some content using `cat` or `echo`
3. Create `script.sh` using `vim` with content: `echo "Hello DevOps"`
<img width="1354" height="178" alt="image" src="https://github.com/user-attachments/assets/026fcf01-f564-4b72-ae97-7e955b7fc2a7" />

**Verify:** `ls -l` to see permissions
<img width="733" height="139" alt="image" src="https://github.com/user-attachments/assets/4cde4167-cf09-42b7-8247-3fd2421721a5" />

---

### Task 2: Read Files 

1. Read `notes.txt` using `cat`
2. View `script.sh` in vim read-only mode
3. Display first 5 lines of `/etc/passwd` using `head`
4. Display last 5 lines of `/etc/passwd` using `tail`

<img width="868" height="74" alt="image" src="https://github.com/user-attachments/assets/6d0cc383-a15f-4ec2-8c6d-6fec018e7773" />
<img width="1374" height="725" alt="image" src="https://github.com/user-attachments/assets/a97ec5a0-6c2f-4626-a67b-c9dfbf15f8b3" />
<img width="947" height="247" alt="image" src="https://github.com/user-attachments/assets/bb893ea3-8d8e-4970-9f69-3a751670022f" />

---

### Task 3: Understand Permissions 

Format: `rwxrwxrwx` (owner-group-others)
- `r` = read (4), `w` = write (2), `x` = execute (1)

Check your files: `ls -l devops.txt notes.txt script.sh`

Answer: What are current permissions? Who can read/write/execute?
```bash
-rw-rw-r--
```
- Owner: Read, Write
- Group: Read, Write
- Others: Read
---

### Task 4: Modify Permissions 

1. Make `script.sh` executable → run it with `./script.sh`
2. Set `devops.txt` to read-only (remove write for all)
3. Set `notes.txt` to `640` (owner: rw, group: r, others: none)
4. Create directory `project/` with permissions `755`

<img width="930" height="275" alt="image" src="https://github.com/user-attachments/assets/e797be9e-4624-4bcf-b01c-b3a7e67806bf" />
<img width="688" height="258" alt="image" src="https://github.com/user-attachments/assets/242ba44f-5c1e-43a6-9835-52c6e6be8050" />
<img width="837" height="260" alt="image" src="https://github.com/user-attachments/assets/83788490-bb49-4bbe-a9c4-53fb5b14b0b1" />
<img width="949" height="331" alt="image" src="https://github.com/user-attachments/assets/261bfe74-f1cc-4a25-a7e8-995c122a55e2" />

#### Updated Permissions
| File/Directory| Permission    | Description                   |
|-------------  |-----------    |-------------------------------|
| script.sh     | `-rwxrwxr-x`  | Script made executeable       |
| devops.txt    | `-r--r--r--`  | Read-only for all users       |
| notes.txt     | `-rw-r-----`  | Owner `rw`, Group `r`         |
| project/      | `drwxr-xr-x`  | Standard directory permissions|

**Verify:** `ls -l` after each change

---

### Task 5: Test Permissions 

1. Try writing to a read-only file - what happens?

<img width="604" height="71" alt="image" src="https://github.com/user-attachments/assets/6c52e8d3-6be0-44bd-8e5d-b132c6afaf0f" />

For vim command :-
<img width="1365" height="62" alt="image" src="https://github.com/user-attachments/assets/49e7f5e4-5478-493c-bd66-9a52063293ce" />

2. Try executing a file without execute permission
<img width="820" height="214" alt="image" src="https://github.com/user-attachments/assets/88b00d8b-6868-498d-a4ff-056ee2895cd0" />

3. Document the error messages : documented above 

---

## Learning Outcomes✅ 

<img width="540" height="334" alt="image" src="https://github.com/user-attachments/assets/a91b6b10-2c07-45fd-8184-6aec3803f15e" />

-Linux file permissions are critical for access control and system security.

-Execute permission and the shebang line are both required to run shell scripts.

-Numeric permission notation (755, 640) is concise and widely used in production systems.

-Permission-related errors help reinforce understanding of Linux security behavior.

---
