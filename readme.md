## Ansible Roles
ansible-galaxy install -p /home/bob/playbooks/roles geerlingguy.nodejs

### Create a role
ansible-galaxy init /home/bob/playbooks/roles/package



### Install a role
ansible-galaxy install -p /home/bob/playbooks/roles geerlingguy.nodejs

### Install a collection
ansible-galaxy collection install community.general


## 🔧 Ansible Error: `rc=137`

### ❓ What Does It Mean?

The exit code `rc=137` in Ansible means the task was **killed by the operating system**, usually due to **out-of-memory (OOM)** conditions.

- Exit code `137` = `128 + 9`
  - `128`: base for signal errors
  - `9`: signal number for **SIGKILL**

➡️ The process was **forcefully terminated**, most likely by the **Linux OOM Killer**.

---

### 🧠 Common Causes

- The task consumed **too much memory**
- The system has **insufficient RAM**
- Memory limits in **Docker containers**
- Multiple tasks running in **parallel**, overwhelming memory

---

### 🛠️ How to Fix It

#### 1. 🧹 Optimize Your Task
- Refactor to use less memory
- Split large tasks into smaller chunks
- Avoid memory-heavy operations in a single task

#### 2. 🔧 Reduce Ansible Forks
In `ansible.cfg`, reduce concurrency:
```ini
[defaults]
forks = 3  # Default is 5; lower it for memory-constrained systems

