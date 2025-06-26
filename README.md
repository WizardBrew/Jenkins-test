markdown
# 🚀 Jenkins CI Setup with Spring PetClinic

This repository documents the step-by-step process to install Jenkins on a Linux environment and configure it for a basic CI pipeline using the [Spring PetClinic](https://github.com/spring-projects/spring-petclinic) project.

---

## 🔧 Method 1: Jenkins Native Installation (Linux)

### Step 1: System Update
```bash
sudo apt update && sudo apt upgrade -y
Step 2: Install Java (JDK 17 or 21 Recommended)
bash
sudo apt install openjdk-17-jdk-headless
Step 3: Add Jenkins Repository and Key
bash
# Add key (Method 1)
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null

# If curl fails, use (Method 2)
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

# Add repo source
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
Step 4: Install Jenkins
bash
sudo apt update
sudo apt install jenkins -y
Step 5: Start Jenkins and Retrieve Initial Password
bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
sudo systemctl status jenkins
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
Access Jenkins on: http://<your-server-ip>:8080

🔁 Continuous Integration Setup
Step 6: Install Maven & Git
bash
sudo apt install maven git -y
Step 7: Create Freestyle Project in Jenkins
Use Repo: https://github.com/spring-projects/spring-petclinic

Build Step: mvn clean install

Output File: target/spring-petclinic-*.jar

Step 8: Run JAR Application
bash
java -jar target/spring-petclinic-*.jar --server.port=8084
☕ Method 2: WAR File Installation (Portable Jenkins)
Step 1: Download
Go to https://updates.jenkins-ci.org/download/war/ and download the latest jenkins.war

Step 2: Run Jenkins WAR
bash
java -jar jenkins.war --httpPort=8082
🐳 Method 3: Jenkins via Docker (Coming Soon)
Set up Jenkins using a Dockerfile or docker-compose.yml for easier portability and isolation.

🧰 Troubleshooting
Port Already in Use
bash
sudo apt install lsof
sudo lsof -i :8080
sudo kill -9 <PID>
GitHub Clone Issues in Jenkins
Ensure Git is installed

If repo is private, configure credentials or use SSH

For public repos, rate-limiting may still apply; consider a GitHub token if needed

📌 Notes
-fsSL flags:

-f: Fail silently on HTTP errors

-s: Silent mode (no progress meter)

-S: Show errors (useful with -s)

-L: Follow redirects

tee: Safer way to write to files via pipe

> /dev/null: Suppresses noisy output

After each Jenkins build, your .jar will typically be in:

/var/lib/jenkins/workspace/<job-name>/target/
To start your app manually:

bash
java -jar filename.jar --server.port=8084
✅ License
This setup is shared for educational and practical use. Adapt and improve freely!


All set! You can paste this directly into your repo’s `README.md` file. If you'


Tests 
![image](https://github.com/user-attachments/assets/4f7fb827-e68f-421a-bb55-48af7b2e4e95)


Test5
![image](https://github.com/user-attachments/assets/36e61c05-91a0-489f-add1-299784006ea9)

