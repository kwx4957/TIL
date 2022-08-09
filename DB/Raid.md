# [Linux] Raid


RAID란 여러 개의 디스크를
## RAID
장점
- 성능 
  - 디스크 여러 개를 병렬적으로 사용하여 I/O시간이 크게 개선된다.
- 용량
- 신뢰성 

### RAID이란? 
- RAID 0 Striping (사용X)
    - 서로 다른 디스크에 동시에 값을 병렬로 저장한다 그러므로 속도가 빨라진다. 하지만 디스크 1이 깨질 경우 전체를 사용하지 못한다.
    - 100 + 100 = 200 디스크의 성능
    - 어느 디스크라도 고장이 발생하면 전체 데이터가 손실된다. 
- RAID 0+1 MIrrors Sets of Striped Drivers
    - RAID 0을 RAID 1로 묶은것
- RAID 1 Mirroring
    - 똑같은 데이터를 다른 디스크에 복사한다.
    - 동일한 데이터를 n개의 디스크에 저장한다.
- RAID 1+0
    - RAID 1를 RAID 0으로 묶은것
    - RAID 1 내가 날라갈겨우 전부 죽어
- RAID 2 Hamming Code ECC (사용X)
    - Striping 방식으로 구성 에러 체크 및 수정을 위해 Hamming
- RAID 3 Parity (사용X)
- RAID 4 Desinged Parity
    - Stiriping 방식 + Parity 방식
    - A B C P(패리디 디스크)
    - 병목 현상 및 한개의 디스크가 아닌 여러개의 디스크가 꺠질 경우 복구 X
    - 최소 3개의 디스크
- RAID 5
    - Stiriping 방식 + Distrubuted Parity 방식
    - Parity 비트를 각 디스크 별로 나눠진다.
    - 최소 3개의 디스크
- RAID 6 Distribute Dual Parity
    - A B P P 패리티 비트가 2배로
    - 최소 4개의 디스크

<br>
실무에서는 RAID 5 또는 RAID 6를 일반적으로 사용하는 것으로 알고 있다. 

- 하드웨어 RAID
- 소프트웨어 RAID


참조:  
[https://harryp.tistory.com/806](https://harryp.tistory.com/806)  
https://github.com/remzi-arpacidusseau/ostep-translations/blob/master/korean/README.md