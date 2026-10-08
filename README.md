# Bài 3 - Thiết lập Database và Systemd cho Spring Boot

## Môi trường
- OS: Ubuntu 22.04 | MySQL 8.0 | Java (OpenJDK)
- App chạy tại /opt/spring-app/app.jar, cổng 8082
- Chạy dưới user hệ thống spring-runner (non-root, nologin)

## 1. Trạng thái dịch vụ — active (running)
Lệnh: `sudo systemctl status spring-app.service`

\`\`\`
● spring-app.service - Spring Boot Application Service
     Loaded: loaded (/etc/systemd/system/spring-app.service; enabled; vendor preset: enabled)
     Active: active (running) since Fri 2026-10-09 02:44:32 +07
   Main PID: 164667 (java)
             └─164667 /usr/bin/java -jar /opt/spring-app/app.jar
Oct 09 02:44:32 ... java[164667]: App started on port 8082
\`\`\`

## 2. Cổng 8082 đang lắng nghe
Lệnh: `ss -tlnp | grep 8082`

\`\`\`
LISTEN 0  50  *:8082  *:*  users:(("java",pid=164667,fd=5))
\`\`\`
