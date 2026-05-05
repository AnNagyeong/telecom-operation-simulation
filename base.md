[ 1. 서버 만들기 in Rocky Linux9 ]
------------------------------------
sudo dnf update -y
sudo dnf install epel-release -y
------------------------------------
웹서버 설치(nginx)
sudo dnf install nginx -y
sudo systemctl enable --now nginx
------------------------------------

systemctl status nginx 
이후 Active - running : 성공

[ 웹 서버 접속하기 ]
http://localhost 접속 OR ip a

만약 방화벽이 막혀있을 경우,
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --reload

<img width="779" height="284" alt="image" src="https://github.com/user-attachments/assets/5385261f-0972-42f1-9345-2c150cc05857" />

[ 웹 서버 접속하기(2) ]
cd /usr/share/nginx/html
sudo nano index.html

<img width="638" height="460" alt="image" src="https://github.com/user-attachments/assets/b881f46e-bc06-4a6c-a5a0-3fe7d225dda3" />


nano에서 index.html을 수정하고 Ctrl + O 를 입력해 저장 후 엔터, Ctrl + X를 눌러 nano를 빠져나간다.

<img width="419" height="148" alt="image" src="https://github.com/user-attachments/assets/8559827e-abc3-4738-87d9-b5712ea661bf" />

[ 2. 로그인 기능 구현 ]
백엔드 준비
sudo dnf install php php-fpm php-mysqlnd -y
sudo systemctl enable --now php-fpm

[ 2.2 백엔드 + nginx 연결 ]
sudo nano /etc/nginx/conf.d/default.conf

<img width="599" height="400" alt="image" src="https://github.com/user-attachments/assets/ba1d3341-8fb8-4cb7-bae7-4260f9a0be41" />

저장하고 나와서
sudo systemctl restart nginx

[ 2.3 PHP 작동 확인 ]
cd /usr/share/nginx/html
sudo nano info.php

<img width="637" height="473" alt="image" src="https://github.com/user-attachments/assets/073a7c6d-7a5a-4124-b877-5911fd2f48af" />

이후 http://localhost/info.php 접속

<img width="949" height="862" alt="image" src="https://github.com/user-attachments/assets/d7434e46-1148-446a-8187-eb0ce430b5ac" />
