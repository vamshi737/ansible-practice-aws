# **Ansible Practice - Day 2 Summary**

## **1. Understanding Ansible Playbooks**
- An **Ansible Playbook** is a YAML file that contains automation instructions for configuration management and application deployment.
- We wrote an **`apache.yaml`** playbook to install and start the Apache web server on an AWS EC2 instance.
- Used proper **YAML syntax** and **best practices** to structure the playbook.

## **2. Setting Up the AWS EC2 Instance**
- Connected to the **EC2 instance** via **MobaXterm** using the AWS public IP address.
- Ensured the correct **SSH key (`linux-key.pem`)** was used for authentication.
- Verified connectivity before proceeding with the Ansible playbook execution.

## **3. Writing and Running the Ansible Playbook**
### **Playbook: `apache.yaml`**
```yaml
---
- name: Install and Start Apache
  hosts: aws_servers
  become: true
  tasks:
    - name: Install Apache
      ansible.builtin.yum:
        name: httpd
        state: present
    
    - name: Start Apache Service
      ansible.builtin.service:
        name: httpd
        state: started
```
### **Execution Command:**
```bash
ansible-playbook -i inventory --private-key=/home/ec2-user/linux-key.pem apache.yaml
```
- Faced issues related to **missing packages and incorrect host configuration**.
- Fixed YAML syntax errors using **yamllint**.
- Successfully installed and started **Apache**.
- Verified installation by accessing **EC2 public IP** in the browser.

## **4. Pushing Playbook and Inventory File to GitHub**
### **GitHub Repository Setup:**
```bash
git init
git remote add origin git@github.com:vamshi737/ansible-practice-aws.git
git add apache.yaml inventory.ini
git commit -m "Added Ansible Playbook and Inventory"
git push origin main
```
- Encountered **authentication issues** due to missing SSH keys.
- Configured GitHub **SSH authentication** to resolve the issue.
- Successfully pushed **all files to GitHub**.

## **5. Troubleshooting and Fixes**
- Fixed YAML formatting using `yamllint`.
- Addressed **Git push errors** by verifying SSH keys.
- Used **Git Bash** for version control and **MobaXterm** for AWS SSH access.

## **6. Finalizing Documentation and Backup**
- Ensured all files are safely stored in the **GitHub repository**.
- Discussed how to restore everything if the **EC2 instance is deleted**.
- Created this documentation as a **Markdown (`.md`) file** to track the entire process.
- Next, we will push this `.md` file to GitHub for reference.

## **7. Next Steps for Day 3**
- Set up a **new AWS instance** if required.
- Clone the GitHub repository and reconfigure SSH keys.
- Pull the latest changes and execute the playbook again.
- Explore advanced Ansible features like **variables, handlers, and conditions**.
- Improve Git workflow and finalize the **README.md documentation**.

### **Conclusion:**
We successfully wrote, executed, and troubleshooted an Ansible Playbook while managing it via GitHub. The process helped in understanding **AWS EC2 setup, Ansible YAML syntax, and Git version control.** 🚀

