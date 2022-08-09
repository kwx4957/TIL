# [Network] Bonding

## Bonding이란

## Bonding 구성 과정
1. VM에 네트워크 1개를 추가한다.
2. ifconfig로 네트워크가 추가되었는지 확인한다.
3. vi   
    1.  vi  /etc/sysconfig/network-scripts/ifcfg-bond0
```
TYPE=Bond
BOOTPROTO=static
DEFROUTE=no
NAME=bond0
DEVICE=bond0
ONBOOT=yes
PREFIX=24
IPADDR=192.168.200.129
GATEWAY=192.168.200.1
BODING_MASTER=yes
BONDING_OPTS=mode 1 miimon=100 fail_over_mac=1
```
    
    2. vi  /etc/sysconfig/network-scripts/ifcfg-ens33    
```
TYPE="Ethernet"
BOOTPROTO=none
NAME=ens33
DEVICE=ens33
ONBOOT=yes
SLAVE=yes
Master=bond0
```
    3. vi  /etc/sysconfig/network-scripts/ifcfg-ens36    
```
TYPE="Ethernet"
BOOTPROTO=none
NAME=ens36
DEVICE=ens36
ONBOOT=yes
SLAVE=yes
Master=bond0
```


4. ip link show 
5. 네트워크를 죽이거나 살림으로서 테스트한다.
    - ip link set dev 네트워크디바이스명 down
    - ip link set dev 네트워크디바이스명 up
    - ifup
    - ifdown


- `fail_over_mac` : bond된 인터페이스와 slave 인터페이스들간에 어떻게 MAC 주소를 가져갈지 정하는 옵션으로 설정된 값에 따라 bond된 인터페이스와 slave 인터페이스들의 MAC을 설정하는 방식이 달라진다.
- bonding mode가 active-backup 방식일때만 사용
- `none` or `0` : (Default) bond된 인터페이스와 모든 slave 인터페이스들의 MAC이 같은 값으로 설정되는 옵션으로 보통 가장 첫번째 slave 인터페이스의 MAC 주소를 모든 bond된 인터페이스와 slave 인터페이스들이 갖는다.

첫 번쨰 slave 인터페이스 MAC 주소로 모든 인터페이스들이 동일한 mac 주소를 가잔다. 

- `active` or `1` : active 상태인 slave 인터페이스의 MAC 주소를 bond된 인터페이스의 MAC으로 설정하는 옵션으로 failover된 상황에서 active 상태인 slave에 따라에 bond된 인터페이스의 MAC 주소가 달라진다.

active된 상태의 mac주소를 따른다 1번이 failover될 경우 2번의 mac주소를 따른다

- `follow` or `2` : bond된 인터페이스의 MAC 주소는 고정이고(보통 첫번째 slave 인터페이스의 MAC 주소를 갖는다.) active 상태가 되는 slave 인터페이스 MAC 주소에 해당 MAC 주소를 부여하는 방식이다. failover가 일어날때 새로 active 상태가 될 인터페이스의 MAC 주소를 이전의 active 상태였던 인터페이스에 부여하고 bond된 인터페이스의 MAC을 받는다.

출처:  
https://atl.kr/dokuwiki/doku.php/linux_network_bonding_-_fail_over_mac