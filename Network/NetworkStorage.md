# [Network] DAS, NAS, SAN

## DAS(Direct-attached storage)
- 컴퓨터와 저장장치 간에 전용 케이블로 직접 접속된 전통적 연결 구조/방식
     - 개별 호스트가 직접연결 등을 통해 각각 저장장치를 소유한다.


### DAS 특징
1. 공유 사용 불가능  
다른 컴퓨터와의 동시에 디스크 정보를 공유할 수 없고, 1대의 컴퓨터에만 연결이 가능하다.
2. 컴퓨터 본체와는 내장 디스크처럼 속도가 빠른 케이블(SATA,SAS,SCSI)로 연결되어 있다.  
3. Block level 단위의 데이터 접근 처리
    - 전통적 병렬형 SCSI 방식의 연결 

## NAS(Network-attached storage)
- 비교적 소규모의 네트워크 스토리지 
    - 기존의 LAN을 기반으로하는 이기종 클라이언트 환경에서 CIFS 나 NFS 등을 이용하여 화일 단위(화일-지향형)의 전송 서비스 제공

- 네트워크를 통해 파일 단위로 공유케하는 시스템
    - 오로지 파일 서비스만 제공 가능

### NAS 특징
- 네트워크에 접속하여 파일 단위로 액세스할 수 있도록 특화된 일종의 전용 파일 서버
    - 고성능 파일 공유 스토리지 디바이스
    - 오로지 파일 서비스만 제공하는 시스템
    - 여러 파일서버를 하나로 통합하는 개념
    - 파일 I/O(파일 저장,추출,엑세스)에 최적화된 서버

- 통신 프로토콜
    - Ethernet 이나 TCP/IP와 같은 전형적인 프로토콜을 사용

- 주요 파일 공유 프로토콜
    - NFS (Network File System)
    - CIFS (Common Internet File System)

- 한편, 대규모 기업에 사용되는 스토리지 네트워크 시스템은 SAN 등을 사용

## SAN(Storage Area Network)
- 스토리지 전용 네트워크
    - 스토리지 트래픽만을 단독으로 처리할 수 있는 고유의 별도 연결망을 갖음. 높은 신뢰성 및 빠른 속도를 제공하는 저장장치 전용의 망

### SAN 구성,운용 형태 특징
- 스토리지의 분산 이용 및 중앙화된 관리 가능
    - 스토리지를 한 곳으로 모아서 관리하고, 지리적으로 분산된 여러 서버가 이를 공유케 함

- 서버들은 분산시키고, 데이터의 공유,백업,관리는 SAN을 통해 일원적으로 처리


## NAS 및 SAN 비교
- NAS
    - 화일 단위의 I/O 인터페이스를 갖음.

- SAN
    - 블록 단위의 I/O 인터페이스를 갖음  
    기존의 망 이외에 서버와 스토리지를 연결하는 별도의 Fiber Channel(FC) 등을 이용하여 블록 단위의 전송 서비스 제공 가능

## FC-SAN 및 IP-SAN 
- FC-SAN : 최대 10 km 거리지원이 일반적
    - FC(파이버 채널) 기술에 기반한 SAN

- IP-SAN : 거리 제한 없음
    - IP(인터넷 프로토콜) 기술에 기반한 SAN  
    FCIP(Fibre Channel over IP) : 분산된 FC-SAN들을 기존의 IP 네트워크를 통해 상호 연결시켜주는 터널링 프로토콜


## 추세
- 초기에는, 주로 파이버 채널(FC)이라는 전용 네트워크인 FC-SAN이 주도적이었으나,
- 최근에는, IP 기반으로하는 TCP/IP 체계의 iSCSI 프로토콜을 이용한 IP-SAN이 각광을 받음   

출처:  
http://www.ktword.co.kr/word/abbr_view.php?m_temp1=3671  
http://www.ktword.co.kr/word/abbr_view.php?nav=2&id=498&m_temp1=2539    
http://www.ktword.co.kr/word/abbr_view.php?m_temp1=2537  