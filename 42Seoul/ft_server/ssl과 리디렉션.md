### 1. Oppen SSL 키 생성



```
openssl req -newkey rsa:4096 -days 365 -nodes -x509 -subj "/C=KR/ST=Seoul/L=Seoul/O=42Seoul/OU=Lee/CN=localhost" -keyout localhost.dev.key -out localhost.dev.crt
```

1. req
2. -newkey
3. rsa : Nbytes
4. -days 365
5. -nodes
6. -x509
7. -subj
8. -keyout
9. -out





### 2. 리디렉션 301

- 사용자와 검색엔진을 정확한 페이지로 이동시키기 위한 방법으로 원래 접속한 URL주소를 새로운 다른 주소로 자동으로 연결해준다.

- 301 상태 코드는 페이지가 새 위치로 이전했다는 의미

- 다음과 같은 경우에 주로 사용.

  - **사이트 수정중 또는 공사중과 같은 테스트시에 관련 페이지로 자동 연결이 필요할 때**
  - 서버와 도메인 주소를 한번에 **이전하였는데 도메인 주소를 일시적으로 남겨둘 때**
  - 서버외에 **사이트가 다른 외부 서비스로 연결을 해야할 때**
  - **http 주소를 https 주소로 변환**할 때

  

https://42kchoi.tistory.com/28

https://www.hanumoka.net/2020/05/19/security-20200519-make-ssl-crt-for-test-https/