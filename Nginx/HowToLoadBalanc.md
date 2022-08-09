# [Nginx] HTTP Load Balance 구성하기 


### 로드 밸런싱 기술
- round robin
- least-connected
- ip-hash

### 로드 밸런싱 설정 
> vi /etc/nginx/nginx.conf 
```vim
http {
    upstream myapp1 {
        server srv1.example.com;
        server srv2.example.com;
        server srv3.example.com;
    }

    server {
        listen 80;

        location / {
            proxy_pass http://myapp1;
        }
    }
}
```
특정 로드 밸런싱 기술을 설정해주지 않을 경우에는, 기본값인 round-robin으로 설정되어있다. 모든 요청은 myapp1 서버 그룹으로 전달이 되어 http 로드 밸런싱으로 요청들을 분배한다. 

리버스 프록시는 HTTP, HTTPS, FastCGI, uwsgi, SCGI memacached, gRPC에 로드 밸런싱이 적용된다. 

https 경우에는 http 대신 htttps를 작성해주면 된다. 

참조:  
https://docs.nginx.com/nginx/admin-guide/load-balancer/http-load-balancer/
http://nginx.org/en/docs/http/load_balancing.html