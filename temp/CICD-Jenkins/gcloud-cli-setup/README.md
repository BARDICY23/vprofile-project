## ☁️ Infrastructure Automation (GCP)

This directory includes scripts to **automate infrastructure setup** on Google Cloud:

### 🔒 Firewall Rules
Located in `firewall-rules/`:
- `allow-http-jenkins` → Allow HTTP traffic to Jenkins
- `allow-http-priv` → Private HTTP access to SonarQube
- `allow-jenkins-ui-public` → Public access to Jenkins UI
- `allow-nexus-ui-jenkins` → Nexus access for Jenkins
- `allow-nexus-ui-priv` → Private Nexus UI access
- `allow-ssh-myip` → Restrict SSH access to your IP

👉 `ip-update` script automatically updates all `priv` rules with your current public IP.

### 💻 Instance Provisioning
Located in `instances-cli/`:
- `jenkins-instance` → Creates Jenkins VM (`Debian 12`, 20GB disk)
- `nexus-instance` → Creates Nexus VM (`CentOS 9`, SSD, 50GB disk)
- `sonar-instance` → Creates SonarQube VM (`Debian 12`, 30GB disk)

Each instance uses a **startup script** for automatic installation & configuration.

