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

1. Docker 이미지로 Debian Buster (OS) 환경 세팅 
3. Nginx (웹 서버) 설치 -> localhost에서 접속(docker port 설정)
   -  apt install nginx : Nginx 설치
   - service nginx start : Nginx 실행)
4. Nginxdp php 설치, 실행 (Nginx conf 설정)
5. mySQL 설치, 실행 (데이터 베이스 만들어보기)
6. phpmyadmin 설치, 접속(conf 설정)
7. Wordpress 설치, 접속 (conf 설정)
7. Wordpress에 DB 적용해보기
8. 지금까지의 과정을 Dockerfile로 자동화
9. SSL, autoindex 설정



TIP)

seolim님

1. Docker이미지로 debian 환경 만들고 접속해보기

2. nginx 설치하고 로컬호스트에서 접속해보기(docker port 설정)

   

3. Nginx에 php실행시켜 띄워보기(php설치 및 nginx conf 설정)

4. mysql실행해보기(db를 하나 만들어보기)

5. phpmyadmin 접속할수 있게 설정해보기(설치 및 conf 설정)

6. wordpress 접속할수 있게 설정해보기(설치 및 conf 설정)

7. wordpress에 db적용시켜보기

8. 지금까지 해온걸 dockerfile로 자동화 시키기



hjeon님

1. 이미지 빌드할 때랑 컨테이너 실행할 때 태그, 이름 설정 안 하면 <none>으로 실행시킬때마다 생성돼서 컴퓨터 터짐. 
2. DB, php, nginx 이런 것들 설치하는게 오래 걸리기 때문에 따로 이미지로 만들어서 베이스 이미지로 삼으면 설치 과정이 생략돼서 시간 매우 단축됨.





### 도커 실행 명령어

```txt
docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]
```

| 옵션  | 설명                                                   |
| :---: | :----------------------------------------------------- |
|  -d   | detached mode 흔히 말하는 백그라운드 모드              |
|  -p   | 호스트와 컨테이너의 포트를 연결 (포워딩)               |
|  -v   | 호스트와 컨테이너의 디렉토리를 연결 (마운트)           |
|  -e   | 컨테이너 내에서 사용할 환경변수 설정                   |
| –name | 컨테이너 이름 설정                                     |
|  –rm  | 프로세스 종료시 컨테이너 자동 제거                     |
|  -it  | -i와 -t를 동시에 사용한 것으로 터미널 입력을 위한 옵션 |
| –link | 컨테이너 연결 [컨테이너명:별칭]                        |



운영체제를 통채로 받아오는 것이 아닌 패키지 매니저와 공유 자원들을 받아 오는 것.



apt update : 현재 컨테이너 안에 있는 패키지 List를 update (apt : Advanced Packaging Tool)

(dpkg -l : 패키지 List 확인)

apt install : 패키지가 이미 있을 때

apt-get install : 패키지가 없을 때

service [패키지명] [동작] : 패키지 실행 명령





nginx 서버를 다운받은 후 php 7.2-fpm 을 연동하기 위해 환경변수를 설정해줘야 함 

​	1) nginx 와 php를 연동하기 위한 파일 수정

​		/etc/nginx/sites-available/default



​		- root 위치 설정 (index root directory)

​		- index에 index.php 추가(명시된 index 파일들 자동적으로 먼저 실행해줌)

​		- 

​	2) php 환경설정 파일 수정 

​		/etc/php/7.2/fpm/php.ini

​		/etcphp/7.2/cli/php.ini



​		1) short open tag off -> on

​		2) cgi.fix_pathinfo 0 -> 1 



service nginx reload. (default 파일 수정 후 재실행을 해줘야 적용이 됨)

service php7.2-fpm start(-> Sock 파일 생성 됨, Sock 파일이 있어야 php 실행 가능)



 service nginx restart.

service php7.2-fpm restart

 



mysql -u root -p







https://stitchcoding.tistory.com/2

https://subicura.com/2017/02/10/docker-guide-for-beginners-create-image-and-deploy.html

https://www.slideshare.net/pyrasis/docker-fordummies-44424016

https://www.manualfactory.net/10903

https://pyrasis.com/docker.html

https://www.youtube.com/watch?v=FZLpsjNbMg8