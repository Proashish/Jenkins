Got it ✅
You want me to prepare a **clear and professional README.md file** that documents the full process of **Jenkins setup on Ubuntu EC2**, including pipeline creation and GitHub integration — so you can directly push it to GitHub.

Here’s a clean **README.md** version for you 👇

---

````markdown
# Jenkins Server Setup on Ubuntu EC2

This guide explains how to set up **Jenkins** on an **Ubuntu EC2 instance**, configure it, and run a sample pipeline project integrated with GitHub + Maven.

---

## 🚀 Step 1: Launch EC2 Instance
- **Name:** `vm_ubuntu_jenkins_server`  
- **AMI:** Ubuntu (latest LTS recommended)  
- **Instance Type:** `t2.medium` (sufficient for Jenkins)  
- **Key Pair:** Select or create a new key  
- **Security Group:** Allow `22 (SSH)` and `8080 (Custom TCP)` from `0.0.0.0/0`

---

## 🖥 Step 2: Connect to EC2
Use Git Bash (Windows) or terminal (Linux/Mac):

```bash
ssh -i "your-key.pem" ubuntu@<EC2-Public-IP>
````

---

## ☕ Step 3: Install Java

Jenkins requires Java. Install **OpenJDK 17**:

```bash
sudo apt update
sudo apt install -y fontconfig openjdk-17-jre
java -version
```

---

## 🔧 Step 4: Install Jenkins

Run the following commands:

```bash
# Add Jenkins key
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

# Add Jenkins repo
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

# Update and install
sudo apt-get update
sudo apt-get install -y jenkins
```

---

## ▶ Step 5: Start Jenkins Service

Enable and start Jenkins:

```bash
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins   # Verify
```

---

## 🌐 Step 6: Access Jenkins UI

1. Open browser → `http://<EC2-Public-IP>:8080/login`
2. Get initial password from server:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

3. Paste it into the **Administrator Password** field.
4. Select **Install Suggested Plugins**.
5. Create first admin user:

   * **Username:** `Ashish`
   * **Password:** `ashish12345`
6. Jenkins URL will look like:

   ```
   http://<EC2-Public-IP>:8080/
   ```

---

## 🛠 Step 7: Create a Pipeline Job

1. Go to **Dashboard → New Item**
2. Enter name: `test-pipeline`
3. Select **Pipeline** → click **OK**
4. Scroll down → add pipeline script.
5. Example **Hello World pipeline**:

```groovy
pipeline {
    agent any
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
}
```

6. Click **Apply → Save**.
7. Run build → `Build Now`.
8. Go to **Console Output** → you should see `"Hello World"`.

---

## ⏱ Step 8: Build Triggers

### Option 1: Build Periodically

Runs job at fixed intervals using CRON syntax:

```
* * * * *
```

➡ Runs every minute (**not recommended**).

### Option 2: Poll SCM (Recommended)

Runs only when there are **changes in GitHub repository**:

```
* * * * *
```

---

## ✅ Final Verification

* Access Jenkins at: `http://<EC2-Public-IP>:8080/`
* Test pipeline job builds successfully.
* GitHub integration triggers build on code changes.

---

## 📌 Notes

* Use `t2.medium` or higher instance type for better performance.
* Always open **port 8080** in Security Group to access Jenkins.
* Prefer **Poll SCM** over **Build Periodically** to save resources.
* You can extend pipelines with Maven, Gradle, Docker, etc.

---

```

---

👉 This README is now GitHub-ready.  

Do you also want me to **add a Jenkins + Maven sample pipeline** (that builds a Java project from GitHub) so your README shows both **Hello World** and a **real Java build example**?
```
# Jenkins
