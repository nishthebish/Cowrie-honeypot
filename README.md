# Cowrie-honeypot

Walking through setting up and configuring a Cowrie SSH honeypot on Ubuntu through a virtual machine.

---

## Tools Used

- Ubuntu 24.04 LTS (inside VirtualBox)
- Cowrie (SSH/Telnet Honeypot)
- Python 3.12.3
- Virtual Environment (venv)
- Git & GitHub for version control

---

## Step-by-Step Setup

### 1. System Update

sudo apt update && sudo apt upgrade -y

---

### 2. Install Required Packages

sudo apt install python3 python3-pip python3-venv git net-tools -y

---

### 3. Clone the Cowrie Repository

git clone https://github.com/cowrie/cowrie.git ~/cowrie  
cd ~/cowrie

---

### 4. Set Up Virtual Environment

python3 -m venv cowrie-env  
source cowrie-env/bin/activate

---

### 5. Install Cowrie Dependencies

pip install --upgrade pip  
pip install -r requirements.txt

---

### 6. Create and Configure Cowrie

cp etc/cowrie.cfg.dist cowrie.cfg  
nano cowrie.cfg

Inside cowrie.cfg, find the [output_jsonlog] section and make sure it looks like this:

[output_jsonlog]  
enabled = true  
logfile = log/cowrie.json

---

### 7. Run the Honeypot

bin/cowrie start

---

### 8. Stop the Honeypot

bin/cowrie stop

---

### 9. Simulate an SSH Attack (From Host or PowerShell)

ssh -p 2222 wronguser@127.0.0.1

Use any password after entering the username.

---

### 10. View Logs of SSH Attempts

tail -f log/cowrie.json  
tail -f var/log/cowrie/cowrie.log

---

## Takeaways

- Set up a honeypot to detect unauthorized access
- Worked with a virtual machine
- Worked with SSH
- Configured Cowrie for logging
- Parsed log files to analyze attack attempts
- Learned how attackers interact with a fake system

---

Maintained by Nishanth Butta  
LinkedIn: https://www.linkedin.com/in/nish-butta  
GitHub: https://github.com/nishthebish
