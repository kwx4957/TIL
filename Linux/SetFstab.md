# [Linux] Fstab

### 이유 
윈도우 경우에는 포맷과 마운트가 자동으로 이루어진다. 하지만 리눅스의 경우에는 사용자가 일일이 포맷과 마운트를 시켜줘야한다. 마운트를 시킨후 /etc/fatab 파일에 마운트한 정보를 저장하지 않을 경우 재부팅 시 마운트가 한 정보가 사라지기에 마운트 정보를 저장해줘야한다.

> vi /etc/fstab
```
파티션이름  마운트할디렉토리          파일시스템의종류   파일시스템의고유옵션 dump  파일점검옵션
/dev/sdb1  /home/user1/nameISking   ext4              defaults           0    0 

```
파일시스템의 고유옵션
- defaults(rw, nouser, auto, exec, suid): 일반적인 파일 시스템에서 사용
- auto: 부팅시 자동 마운트
- noauto: 자동 마운트 X
- exec : 실행파일이 실행되는 것을 허용
- noexec : 실행파일이 실행되지 허용 X 
- suid : SetUID와 SetGID의 사용을 허용
- nosuid : SetUID와 SetGID의 사용을 허용 X
- ro : 읽기전용 마운트
- rw : 읽기, 쓰기 가능하도록 마운트
- user : 일반 계정사용자들도 마운트 가능
- nouser : root 계정만 마운트 가능
- usrquota : 개별 계정사용자들의 quota 설정이 가능하도록 한다.
- grpquota : 그룹별 quota 설정이 가능하도록 한다.

dump(백업) 관련 설정(0,1)  
- 0: 덤프가 불가능하게 설정
- 1: 덤프가 가능하게 설정

파일 점검옵션: 무결성 체크(0,1,2)
fsck에 의한 무결성 검사 우선순위 지정
- 0: 무결성 검사 X 
- 1: 우선순위 1순위, 루트부분에 설정
- 2: 우선순위 2순위, 1순위 검사후 2순위 검사 

참조:  
https://hanaldo.tistory.com/32  
https://movenpick.tistory.com/34  
https://hanaldo.tistory.com/32