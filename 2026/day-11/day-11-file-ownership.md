# Day 11 – File Ownership Challenge (chown & chgrp)

## Challenge Tasks

### Task 1: Understanding Ownership 

1. Run `ls -l` in your home directory
2. Identify the **owner** and **group** columns
3. Check who owns your files

<img width="1111" height="225" alt="image" src="https://github.com/user-attachments/assets/1afa5d4a-190d-4e45-ac2f-7ba107040ca0" />

**Format:** `-rw-r--r-- 1 owner group size date filename`

Document: What's the difference between owner and group?

Owner is one user who owns the file. Group is a set of users who can access the file. Linux uses owner, group, and others to control permissions

---

### Task 2: Basic chown Operations 

1. Create file `devops-file.txt`
2. Check current owner: `ls -l devops-file.txt`
3. Change owner to `tokyo` (create user if needed)
4. Change owner to `berlin`
5. Verify the changes
   
**Try:**
```bash
sudo chown tokyo devops-file.txt
```
<img width="1258" height="628" alt="image" src="https://github.com/user-attachments/assets/d8a3f3f0-c394-494d-b028-ab66255a5a61" />

---

### Task 3: Basic chgrp Operations

1. Create file `team-notes.txt`
2. Check current group: `ls -l team-notes.txt`
3. Create group: `sudo groupadd heist-team`
4. Change file group to `heist-team`
5. Verify the change

<img width="979" height="208" alt="image" src="https://github.com/user-attachments/assets/7694866d-95bd-4b17-aeb5-0dc8a1ce1904" />

---

### Task 4: Combined Owner & Group Change 

Using `chown` you can change both owner and group together:

1. Create file `project-config.yaml`
2. Change owner to `professor` AND group to `heist-team` (one command)
3. Create directory `app-logs/`
4. Change its owner to `berlin` and group to `heist-team`

**Syntax:** `sudo chown owner:group filename`

<img width="893" height="440" alt="image" src="https://github.com/user-attachments/assets/18829b42-4abb-46df-9f2f-e7efdfd66945" />
<img width="1069" height="462" alt="image" src="https://github.com/user-attachments/assets/46da1e34-2ce8-4f27-86d7-f3d2c29677eb" />

---

### Task 5: Recursive Ownership 

1. Create directory structure:
   ```
   mkdir -p heist-project/vault
   mkdir -p heist-project/plans
   touch heist-project/vault/gold.txt
   touch heist-project/plans/strategy.conf
   ```
<img width="1371" height="517" alt="image" src="https://github.com/user-attachments/assets/b0e12fa3-89b8-4a85-b5e8-f37075982d0d" />
<img width="776" height="218" alt="image" src="https://github.com/user-attachments/assets/1e7571ef-fd3e-49c7-8ec2-448ea942ed02" />

2. Create group `planners`: `sudo groupadd planners`

3. Change ownership of entire `heist-project/` directory:
   - Owner: `professor`
   - Group: `planners`
   - Use recursive flag (`-R`)

4. Verify all files and subdirectories changed: `ls -lR heist-project/`

<img width="1188" height="378" alt="image" src="https://github.com/user-attachments/assets/89133fc3-0ddb-4232-9828-d49054bbc074" />
<img width="798" height="260" alt="image" src="https://github.com/user-attachments/assets/2a130bbe-affb-434f-8abc-a179654c1209" />

---

### Task 6: Practice Challenge 

1. Create users: `tokyo`, `berlin`, `nairobi` (if not already created)
2. Create groups: `vault-team`, `tech-team`
3. Create directory: `bank-heist/`
4. Create 3 files inside:
   ```
   touch bank-heist/access-codes.txt
   touch bank-heist/blueprints.pdf
   touch bank-heist/escape-plan.txt
   ```
<img width="1326" height="482" alt="image" src="https://github.com/user-attachments/assets/34696482-cb80-4168-8946-f261041b259f" />


5. Set different ownership:
   - `access-codes.txt` → owner: `tokyo`, group: `vault-team`
   - `blueprints.pdf` → owner: `berlin`, group: `tech-team`
   - `escape-plan.txt` → owner: `nairobi`, group: `vault-team`

**Verify:** `ls -l bank-heist/`

<img width="1239" height="284" alt="image" src="https://github.com/user-attachments/assets/ac87130a-3c2d-4ed6-8f13-d15a5eb3053f" />

---

## Key Commands Reference

```bash
# View ownership
ls -l filename

# Change owner only
sudo chown newowner filename

# Change group only
sudo chgrp newgroup filename

# Change both owner and group
sudo chown owner:group filename

# Recursive change (directories)
sudo chown -R owner:group directory/

# Change only group with chown
sudo chown :groupname filename
```
---

## Hints

- Most `chown`/`chgrp` operations need `sudo`
- Use `-R` flag for recursive directory changes
- Always verify with `ls -l` after changes
- User must exist before using in `chown`
- Group must exist before using in `chgrp`/`chown`

---


## Troubleshooting

**Permission denied?**
- Use `sudo` for chown/chgrp operations

**Group doesn't exist?**
- Create it first: `sudo groupadd groupname`

**User doesn't exist?**
- Create it first: `sudo useradd username`

---

## Why This Matters for DevOps

In real DevOps scenarios, you need proper file ownership for:

- Application deployments
- Shared team directories
- Container file permissions
- CI/CD pipeline artifacts
- Log file management

---
