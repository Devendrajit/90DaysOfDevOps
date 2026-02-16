# Day 09 – Linux User & Group Management

## Objective
The objective of Day 09 was to gain hands-on experience with **Linux user and group management**.  
This included creating users and groups, assigning users to multiple groups, and configuring shared directories with proper permissions for collaboration.

## Users & Groups
- Users created:
    - tokyo
    - berlin
    - professor
    - nairobi

- Groups created:
    - developers
    - admins
    - project-team

---

## Group Assignments
| User      | Groups Assigned           |
|-----------|---------------------------|
| tokyo     | developers, project-team  |
| berlin    | developers, admins        |
| professor | admins                    |
| nairobi   | project-team              |

---

## Task 1: User Creation

Create three users with home directories and passwords:
- `tokyo`
- `berlin`
- `professor`

<img width="703" height="363" alt="image" src="https://github.com/user-attachments/assets/c9cf208d-31af-439f-b9d7-cc8bf4252e0a" />

**Verify:** Check `/etc/passwd` and `/home/` directory

<img width="981" height="700" alt="image" src="https://github.com/user-attachments/assets/3a2b1da9-c424-4eb4-9702-76d54135fe03" />

---

### Task 2: Create Groups 

Create two groups:
- `developers`
- `admins`
  
<img width="953" height="702" alt="image" src="https://github.com/user-attachments/assets/12c65020-14d7-4be7-bd19-ed3a5d37a21c" />

**Verify:** Check `/etc/group`

<img width="1070" height="317" alt="image" src="https://github.com/user-attachments/assets/29e09516-7be7-407b-98de-e98567d2e7d7" />

---

### Task 3: Assign to Groups 

Assign users:
- `tokyo` → `developers`
- `berlin` → `developers` + `admins` (both groups)
- `professor` → `admins`

<img width="931" height="85" alt="image" src="https://github.com/user-attachments/assets/9a86b5d7-3db2-4477-92da-8f89e44a481d" />

**Verify:** Use appropriate command to check group membership

<img width="1367" height="84" alt="image" src="https://github.com/user-attachments/assets/69f30c14-5119-413a-8d19-4d1b06c6fc94" />
<img width="1366" height="174" alt="image" src="https://github.com/user-attachments/assets/d03a5d4a-014e-4b02-8ca1-fe7e63687cf9" />

---
### Task 4: Shared Directory 

1. Create directory: `/opt/dev-project`
2. Set group owner to `developers`
<img width="746" height="237" alt="image" src="https://github.com/user-attachments/assets/f0eaf093-e5b1-4da5-96c6-4450494d7db6" />

3. Set permissions to `775` (rwxrwxr-x)
<img width="937" height="296" alt="image" src="https://github.com/user-attachments/assets/df7afce4-98e1-46d1-8a8b-56daa97ef674" />

4. Test by creating files as `tokyo` and `berlin`
created 

**Verify:** Check permissions and test file creation

Users toyko and berlin both belong to developers group therefore both users have read, write and execution access to dev-project directory but user professor belongs to other group therefore can only access to read and execute.
<img width="954" height="221" alt="image" src="https://github.com/user-attachments/assets/654fc751-ab55-408a-97c2-a75838e5782a" />

Now logged in as tokyo user and created file named tokyo_files.sh which has defalut permission i.e read and write permissions for the owner and group, and read-only for others. 

<img width="700" height="154" alt="image" src="https://github.com/user-attachments/assets/1bd223cb-45b5-4a1e-8e24-54fb7846d238" />

Changed permission of this file to read,write and execute for owner, read and execute for group and read-only for other user.

<img width="1029" height="120" alt="image" src="https://github.com/user-attachments/assets/d1677849-4fef-4cb5-a51e-41d38906a837" />

Now logged in as berlin and can check accesses

read access - Yes

<img width="1257" height="272" alt="image" src="https://github.com/user-attachments/assets/06a095b7-e67d-4fac-a289-8d3928d4179c" />

write access - No

<img width="1361" height="718" alt="image" src="https://github.com/user-attachments/assets/2ef2eda6-0662-4cc6-b8f9-39402e0903bd" />

Execution access - No

<img width="576" height="47" alt="image" src="https://github.com/user-attachments/assets/1433c5aa-b50f-4990-a328-073c74726615" />

In order to provide required access to other users, need to change file permission to required aceess and can change group of this file accordingly for required users if required.

---

### Task 5: Team Workspace 

1. Create user `nairobi` with home directory
2. Create group `project-team`
3. Add `nairobi` and `tokyo` to `project-team`
4. Create `/opt/team-workspace` directory
5. Set group to `project-team`, permissions to `775`
6. Test by creating file as `nairobi`

<img width="1365" height="206" alt="image" src="https://github.com/user-attachments/assets/5cf8b0ea-2cbd-4a44-acd4-fbcc20d09aa2" />
<img width="1362" height="74" alt="image" src="https://github.com/user-attachments/assets/809c09ee-1ca1-4f78-a2ef-59dbf3a7c659" />
<img width="1340" height="623" alt="image" src="https://github.com/user-attachments/assets/5d7f45e7-7fa3-4321-9adb-2ed3edab90af" />
<img width="1096" height="196" alt="image" src="https://github.com/user-attachments/assets/25367293-f988-4d41-85c2-1e40e620f17c" />

checking permissions of this file 
<img width="1038" height="89" alt="image" src="https://github.com/user-attachments/assets/765d84f5-ff63-41d6-be28-5f9633d61056" />
<img width="1038" height="89" alt="image" src="https://github.com/user-attachments/assets/d3d5e8fc-c451-4f68-a544-bed9b855999f" />

---

## Commands Used

### User Management
```bash
sudo useradd -m tokyo
sudo useradd -m berlin
sudo useradd -m professor
sudo useradd -m nairobi
sudo passwd <username>
```
---

### Group Management
```bash
sudo groupadd developers
sudo groupadd admins
sudo groupadd project-team
```
---

### Assign Users to Groups
```bash
sudo usermod -aG developers tokyo
sudo usermod -aG developers,admins berlin
sudo usermod -aG admins professor
sudo gpasswd -M nairobi,tokyo project-team
```
---

### Directory & Permissions
```bash
sudo mkdir dev-project
sudo chgrp developers dev-project/
sudo chmod 775 dev-project

sudo mkdir /opt/team-workspace
sudo chown :project-team team-workspace
sudo chmod 775 team-workspace
```
---

### Testing and verification
```bash
sudo -u tokyo touch /opt/dev-project/tokyo-test
sudo -u berlin touch /opt/dev-project/berlin-test
sudo -u nairobi touch /opt/team-workspace/nairobi-test
ls -ld /opt/team-workspace/nairobi_files.txt
```
<img width="1193" height="259" alt="image" src="https://github.com/user-attachments/assets/b0163b21-7b11-4c94-b69f-2396aa64f11e" />

---

## What I Learned
1. Users do not get permissions directly, groups control access
2. The `-aG` flag is critical to avoid removing existing group memberships
3. Correct group ownership and permissions enable secure collaboration
4. `sudo -u` is a safe way to test user access without switching sessions
