# RHEL Automated Installation with Kickstart

This repository provides **example files** to automate the installation of **Red Hat Enterprise Linux (RHEL)** using **Kickstart** and custom **boot parameters**.  
All sensitive information has been anonymized. Use them as a reference to build your own setup.

---

## Repository Structure

- [`rhel94bond`](prm/rhel94bond.prm) → Example boot parameters (kernel line).  
- [`rhelvirtksbond`](kickstart/rhelvirtksbond) → Example Kickstart configuration file.

---

## How to Use

### 1. Prepare the Installation Server
- Configure an HTTP or NFS server to host your RHEL installation tree.  
- Place the Kickstart file in a known location, e.g.:
- http://example.repo.local/rh94/images/rhelvirtks
- ### 2. Set Boot Parameters
Use the content of [`rhel94bond`](prm/rhel94bond.prm) as an example.  
These parameters configure:
- Network interfaces
- Repository URL
- Location of the Kickstart file (`inst.ks`)

### 3. Customize the Kickstart File (`ks.cfg`)
The Kickstart file defines:
- Authentication and user accounts
- Disk partitioning
- Networking (bonding example included)
- Package groups to be installed
- Post-installation scripts

Edit it to match your environment:
- Replace `192.168.0.x` with your IPs
- Update `server.example.com` with your hostname
- Adjust partitioning and package groups as needed

### 4. Start the Installation
- Boot the system with the customized boot parameters.  
- The installer will automatically fetch the Kickstart file and perform the installation.  

### 5. Verify Post-Installation
After installation and reboot:
- Logs are available at `/root/anaconda-ks.cfg` and `/root/post.log`.

---

## Customization Tips
- **Root password**: generate a hash with  
```bash
openssl passwd -6
```

📖 References
- [Red Hat Kickstart Documentation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html/performing_an_advanced_rhel_installation/assembly_automating-the-installation-with-kickstart_installing-rhel)
- [Kickstart Syntax Reference](https://pykickstart.readthedocs.io/en/latest/)
