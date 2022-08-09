# [Linux] Chrony 사용하기

### Chrony이란?
NTP의 구현체이며 ntpd의 대체제이다. 유닉스 운영체제(리눅스와 macOs)에서 돌아간다. 

### 기존 NTP와의 차이점
- Chrony는 SHA256과 SHA512와 같은 최신 보안이 적용이 가능하지만 NTP는 MD1와 SHA1과 같은 옛 버전의 보안 방식을 사용하여 취약하다.

- NTP는 AutoKey 프로토콜을 사용하는데 보안 문제로 사용하지 않는다. 대신 Chrony에서는 대칭 키 인증 방식을 사용한다.

### Chrony 구성하기
- chrony를 설치하기 앞서 NTP를 꺼줘야 한다.
- UDP 123번 포트가 열려있어야 한다. ㄷ
1. yum install -y chrony
2. vi /etc/chrony.conf
    ```
    # 기존 ntp 서버 주석 처리 
    #server 0.centos.pool.ntp.org iburst
    #server 0.centos.pool.ntp.org iburst
    #server 0.centos.pool.ntp.org iburst
    #server 0.centos.pool.ntp.org iburst
    # 동기화 시킬 NTP 서버 추가
    server NTPserverIP iburst 
    ```
    ### Stratum 2의 서버 목록
    - time.bora.net
    - time.nist.gov
    - kr.pool.ntp.org  
<br>
3. systemctl restart chronyd
4. systemctl enable chronyd 
5. 동기화 여부 확인
    1. chronyc sources
        1. NTP 서버와의 시간 차이 Last
        
        | M |  |
        | --- | --- |
        | ^ | 서버 |
        | = | 피어 |
        | # | 로컬 |
        
        | S |  |
        | --- | --- |
        | * | 현재 동기화중 |
        | + | 동기화 가능 |
        | - | 동기화 불가능 |
        | ? | 응답 없음 |
        | x | 서버와 시간차이가 큼 |
        
    2. chronyc tracking 
6. 수동 시간 동기화
    1. chronyc -a makstep 
    2. hwclock -w (현재 설정된 시간으로 하드웨어 시간 설정)


참조:  
https://s-core.co.kr/post_os/%EC%84%9C%EB%B2%84-%EC%8B%9C%EA%B0%84-%EB%8F%99%EA%B8%B0%ED%99%94-%EB%B0%A9%EB%B2%95/  
https://joungkyun.gitbook.io/annyung-3-user-guide/chapter6/chapter6-chrony  
https://access.redhat.com/documentation/en-us/red-hat-enterprise-linux/8/guide/9cf452d2-ae03-4a15-9797-fe7e46a316c4  
https://chrony.tuxfamily.org/comparison.html