Here are **clean, structured, and Obsidian-ready notes** extracted from your Nagios PDF.

---

### 🖥️ Nagios Installation Notes  
**Status**: Draft  
**Tags**: #nagios #linux #monitoring #apache #installation  

---

#### 🔧 Overview  
We are installing **Nagios Core from source** on a Linux system.  
This requires:
- Installing dependencies
- Compiling from source
- Configuring Apache to serve the Nagios web UI
- Enabling required Apache modules

---

#### ✅ Step-by-Step Installation

---

##### 1. Install Dependencies  
```bash
sudo apt update
sudo apt install -y build-essential apache2 php openssl perl make php-gd libgd-dev libapache2-mod-php libperl-dev libssl-dev daemon wget apache2-utils unzip
```

---

##### 2. Download Nagios Core  
```bash
cd /tmp
wget https://assets.nagios.com/downloads/nagioscore/releases/nagios-4.5.0.tar.gz
tar -xzf nagios-4.5.0.tar.gz
cd nagios-4.5.0/
```

---

##### 3. Compile and Install  
```bash
sudo ./configure --with-httpd-conf=/etc/apache2/sites-enabled
sudo make all
sudo make install
sudo make install-init
sudo make install-commandmode
sudo make install-config
sudo make install-webconf
```

---

##### 4. Configure Apache  
Enable required modules and restart Apache:
```bash
sudo a2enmod rewrite
sudo a2enmod cgi
sudo systemctl restart apache2
```

---

##### 5. Create Nagios Admin User  
```bash
sudo htpasswd -c /usr/local/nagios/etc/htpasswd.users nagiosadmin
```

---

##### 6. Start Nagios Service  
```bash
sudo systemctl start nagios
sudo systemctl enable nagios
```

---

##### 7. Verify Installation  
Open browser and go to:  
```
http://your-server-ip/nagios
```
Log in with `nagiosadmin` and the password you set.

---

#### 📁 Key Paths  
- **Nagios Config**: `/usr/local/nagios/etc/`
- **Web UI**: `http://your-ip/nagios`
- **Apache Config**: `/etc/apache2/sites-enabled/nagios.conf`

---

#### 🧪 Next Steps  
- Install Nagios Plugins
- Configure hosts/services
- Set up email alerts

---

Let me know if you want a version with **Mermaid diagrams**, **checklist format**, or **plugin installation steps** next.