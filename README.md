<table>
  <tr>
    <td align="center">
      <img src="https://github.com/user-attachments/assets/4f7fb827-e68f-421a-bb55-48af7b2e4e95" width="600"/><br>
      <strong>Test</strong>
    </td>
    <td style="width: 100px;"></td> <!-- Acts as spacer -->
    <td align="center">
      <img src="https://github.com/user-attachments/assets/36e61c05-91a0-489f-add1-299784006ea9" width="600"/><br>
      <strong>Test5</strong>
    </td>
  </tr>
</table>




🚀 Jenkins CI Setup with Spring PetClinic
This repository documents the step-by-step process for installing Jenkins on a Linux environment 🐧 and configuring it for a basic CI pipeline using the 🌸 Spring PetClinic project.

🔧 Method 1: Jenkins Native Installation (Linux)

🛠 Step 1: System Update

`bash`
```sudo apt update && sudo apt upgrade -y```

☕ Step 2: Install Java (JDK 17 or 21 Recommended)

`bash`
```sudo apt install openjdk-17-jdk-headless```

🔐 Step 3: Add Jenkins Repository and Key
Option 1 (curl):

`bash`
```curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null```

Option 2 (get):

`bash`
```sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key```

Add Jenkins repo source:

`bash`
```echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null```


📦 Step 4: Install Jenkins

`bash`
```sudo apt update
sudo apt install jenkins -y ```

🚦 Step 5: Start Jenkins and Get Initial Password

`bash`
```sudo systemctl start jenkins
sudo systemctl enable jenkins
sudo systemctl status jenkins
sudo cat /var/lib/jenkins/secrets/initialAdminPassword```

*🌐 Access Jenkins at: http://localhost:8080*

--=== 🔁 Continuous Integration Setup ===--

📚 Step 6: Install Maven & Git
`bash`
```sudo apt install maven git -y```

📂 Step 7: Create Freestyle Project in Jenkins
*🔗 Use Repo: https://github.com/spring-projects/spring-petclinic*

🧪 Build Step: mvn clean install
📁 Output file: target/spring-petclinic-*.jar

▶️ Step 8: Run Spring Application
`bash`
```java -jar target/spring-petclinic-*.jar --server.port=8080```

-------------===========------------------

☕ Method 2: WAR File Installation (Portable Jenkins)
⬇️ Step 1: Download WAR
🔗 https://updates.jenkins-ci.org/download/war/

🚀 Step 2: Run Jenkins WAR
bash
```java -jar jenkins.war --httpPort=8082```


🐳 Method 3: Docker-based Jenkins (coming soon)
Containerize your Jenkins setup for portability and ease of deployment 🐋


------------===============----------------

🧰 Troubleshooting
❌ Port Already in Use
bash
```sudo apt install lsof
sudo lsof -i :8080
sudo kill -9 <PID>```


🔒 GitHub Clone Issues
✅ Confirm Git is installed

🔐 Use credentials for private repos or SSH

🚫 Avoid GitHub rate-limits for public repos by caching auth or using a token

📌 Important Abrevation
Flags used in commands:
-f: Fail silently on errors
-s: Silent mode
-L: Follow redirects
> /dev/null: Clean output

✅ Build output directory: /var/lib/jenkins/workspace/<job-name>/target/

🧑‍💻 Manual App Run:

bash
java -jar filename.jar --server.port=8084
✅ License
This project setup is open-source and reusable ✨. Customize it for your own CI/CD experiments and happy building! 🏗️

Let me know if you'd like a badge section, .gitignore, or Docker setup next 🐳💡



