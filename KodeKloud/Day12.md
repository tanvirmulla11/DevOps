# Fix Apache Service Reachability on Port 8085
## Task Description

### Our monitoring tool reported an issue in the Stratos Datacenter.
### One of the application servers (stapp01) had its Apache service unreachable on port 8085.

### Possible causes included:

### Apache service being down

### Firewall blocking the port

### Another service already using the port

### The objective was to identify and fix the issue using tools like telnet, netstat, etc., and ensure Apache is reachable from the jump host without compromising
### security.

### Once fixed, we verified the solution using:
### Troubleshooting & Fix Steps
### 1. Verify reachability from Jump Host
```bash
1. Verify reachability from Jump Host
```
### 2. Log in to stapp01 and check Apache status
```bash
ssh tony@stapp01
sudo systemctl status httpd
```
### 3. Identify which process was using port 8085
```bash
sudo netstat -lntp | grep 8085
```
### 4. Stop the conflicting process
```bash
sudo kill <PID>
```
### 5. Restart Apache service
```bash
sudo systemctl restart httpd
sudo systemctl status httpd
```

### Result: Apache running successfully, listening on port 8085.

### 6. Open firewall for port 8085
```bash
sudo iptables -I INPUT 1 -p tcp --dport 8085 -j ACCEPT
sudo service iptables save
sudo systemctl enable iptables
```
### 7. Confirm Apache is listening
```bash
sudo netstat -tulnp | grep 8085
```

### Result: Apache (httpd) listening on 0.0.0.0:8085.

### 8. Verify from jump host
```bash
curl http://stapp01:8085
```

### Result: Apache page successfully reachable.

## Final Status

### Apache is running and listening on port 8085.

### Firewall rules updated and saved persistently.

### Apache is reachable from the jump host as expected.
# images
<img width="1919" height="967" alt="Screenshot 2025-08-29 105452" src="https://github.com/user-attachments/assets/5444551d-39bb-401b-bc81-6cb95819424a" />
<img width="1919" height="966" alt="Screenshot 2025-08-29 105514" src="https://github.com/user-attachments/assets/5b4610af-bfcc-4353-8eb3-7019924b0579" />



### ✅ Issue resolved.


