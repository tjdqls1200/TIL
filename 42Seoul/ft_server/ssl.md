#### penssl로 self-signed ssl 인증서 만들기

1. `apt-get -y install openssl vim`

 

2.

```
openssl req -newkey rsa:4096 -days 365 -nodes -x509 -subj "/C=KR/ST=Seoul/L=Seoul/O=42Seoul/OU=Lee/CN=localhost" -keyout localhost.dev.key -out localhost.dev.crt
```

