# [Linux] LVM 구성하기

## LVM이란?

CentOS 7기준

## LVM 구성하기 

1. 파티션 생성    
추가한 디스크에 대하여 파티션을 만들어 준다. 
> fdisk /dev/sdb  리눅스 파티션 테이블 조작도구  
    - p 파티션 상태확인  
    - n -> p, 기본값, 기본값, 기본값   
    - t -> 8e(Linux LVM) 
    - w
2. PV 생성  
생성한 파티션에 대한 PV를 만든다.
> pvecreate /dev/sdb1 /dev/sdc1  
  pvs 물리봄륨 정보 조회

3. VG 생성
> vgcreate 볼륨그룹명 파티션들  
vgcreate VG_
4. LVM 생성 

5. 포맷후 마운트해주기
> mkfs.xfs 
> mount 

6. fstab 편집
> vi /etc/fstab 


참조:  
https://yunjipark0623.tistory.com/entry/CentOS7-%EB%A6%AC%EB%88%85%EC%8A%A4-LVMLogical-Volume-Manager-%EC%A0%95%EC%9D%98-%EA%B5%AC%EC%84%B1%ED%95%98%EA%B8%B0
https://tech.cloud.nongshim.co.kr/2018/11/28/lvmlogical-volume-manager-linux-%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4%EC%97%90%EC%84%9C-%ED%99%9C%EC%9A%A9%ED%95%98%EA%B8%B01-2/