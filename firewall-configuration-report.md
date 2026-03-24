# Linux Firewall Configuration & Security Rules
## Firewall Setup (UFW)

### Install UFW
sudo apt update
sudo apt install ufw -y

### Enable Firewall at Startup
sudo ufw enable
**Explanation:**  
This activates the firewall and ensures it starts automatically when the system boots.
##  Allow Required Services

### Allow OpenSSH (port 22)
sudo ufw allow ssh
**Why:**  
Allows secure remote access to the server.
### Allow HTTP (port 80)
sudo ufw allow http
**Why:**  
Allows web traffic for websites.
### Allow HTTPS (port 443)
sudo ufw allow https
**Why:**  
Allows secure web traffic (encrypted connections).
##  Logging Configuration

### Enable Logging
sudo ufw logging on
### Set Logging Level
sudo ufw logging medium

**Explanation:**  
- Logs blocked connections  
- Logs allowed services  
- Helps monitor suspicious activity  

## Default Policies
sudo ufw default deny incoming
sudo ufw default allow outgoing
**Explanation:**  
- Blocks all incoming connections unless explicitly allowed  
- Allows outgoing connections  



##  Protection Against SYN Flood Attacks

Edit sysctl configuration:
sudo nano /etc/sysctl.conf

Add the following lines:
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_max_syn_backlog = 2048
net.ipv4.tcp_synack_retries = 2
net.ipv4.tcp_syn_retries = 5

Apply changes:

sudo sysctl -p


**Explanation:**  
These settings help protect against SYN flood attacks by managing how TCP connections are handled.
## Additional Security Rule (Rate Limiting SSH)
sudo ufw limit ssh

**Why:**  
Prevents brute-force attacks by limiting repeated login attempts.

## Other Common Attacks & Prevention

### 1. Brute-force attacks
- Prevented using `ufw limit ssh`

### 2. Port scanning
- Mitigated by default deny policy

### 3. SYN flood attacks
- Prevented using TCP syncookies and sysctl tuning

### 4. Unauthorized access
- Prevented by allowing only required ports
## Check Firewall Status
sudo ufw status verbose

The firewall ensures that the system is secure and only accessible through defined services.
