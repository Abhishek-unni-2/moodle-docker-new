# moodle-docker-new
# 🚀 Setup Moodle LMS 5.0.5 Using Docker on Linux Host

This project sets up a Moodle 5.0.5 environment using:

- 🐘 **PHP 8.3** with Apache (in a Docker container)
- 🐬 **MySQL** (running on the host machine)
- 📦 **Moodle source code** cloned from the official Moodle Git repository
- ⚙️ **Custom configuration** for performance and compatibility

---

## 🛠️ Setup Instructions

### 1. Clone This Repository

```bash
git clone <your-repo-url>
cd moodle-docker
##2. Database Setup (Run on Host)##
sql

CREATE DATABASE moodle CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'moodle12'@'%' IDENTIFIED BY 'Root@0884';
GRANT ALL PRIVILEGES ON moodle.* TO 'moodle12'@'%';
FLUSH PRIVILEGES;
3. Project Directory Setup

mkdir docker-compose.yml
sudo nano docker-compose.yml
sudo nano Dockerfile
mkdir moodle.conf



4. Configure Nginx
nano /etc/nginx/sites-available/moodle.conf
sudo ln -s /etc/nginx/sites-available/moodle.conf /etc/nginx/sites-enabled/
systemctl restart nginx


5. Start Docker Containers
docker-compose down
docker-compose up -d --build

6. Get Moodle Container IP Address
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' moodle-app

7. Access MySQL (on Host)
mysql -u moodle12 -p
# Password: Root@0884
8. Open Moodle in Browser

http://localhost
✅ Note:
Make sure MySQL is running before starting the Docker containers.

📂 Directory Structure (Example)

markdown
Copy
Edit
moodle-docker/
├── docker-compose.yml
├── Dockerfile
└── nginx/
    └── moodle.conf
