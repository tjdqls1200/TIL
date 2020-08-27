**1. Introduction**



- 시스템 관리 학습. 

- 작업을 자동화하기 위해 스크립트를 사용하는 것의 중요성 인지

- **docker를 사용하여 완전한 웹 서버**를 설치

- 이 서버는 **Wordpress, phpMyAdmin 그리고 SQL 데이터베이스 서비스** 실행.

  

**2. General instructions**



- **서버 구성에 필요한 모든 파일을 srcs 폴더**에 저장

- **Dockerfile 파일은 리포지토리의 루트에 있어야하고 이것은 컨테이너를 빌드할 것**이다. (docker-compose 사용 X)

- **WordPress 웹 사이트에 필요한 모든 파일은 srcs 폴더**에 있어야한다

  

**3. Mandatory part**



- **하나의 Docker 컨테이너에서 Nginx로 웹 서버를 설정**해야한다. (**컨테이너 OS는 debian buster**)
- 웹 서버는 **여러 서비스를 동시에 실행**할 수 있어야한다. 
- 서비스는 **WordPress 웹 사이트, phpMyAdmin 그리고 MySQL**이고 SQL 데이터베이스가 WordPress 와 phpMyAdmin에서 작동하도록 만들어야한다.
- **서버는 SSL 프로토콜을 사용**할 수 있어야한다.
- **URL에 따라 서버가 올바른 웹사이트로 리디렉션되어야 한다.**
- **서버가 반드시 연결이 되지 않아도 autoindex로 돌아갈 수 있어야 한다?**
- 언제든 해제할 수 있는 autoindex가 적용 되어야 한다?





순서

1. Debian Buster (OS)
   - Debian Buster 이미지 Build
   - Debian Buster 기반의 컨테이너 생성
2. 이미지를 이용하여 컨테이너 생성
3. Nginx (웹 서버) 
   -  apt install nginx : Nginx 설치
   - service nginx start : Nginx 실행)
4. php 설치
5. mySQL 설치 (데이터 베이스)
6. phpmyadmin 설치
7. Wordpress 설치 (웹 사이트)
8. SSL, autoindex 설정