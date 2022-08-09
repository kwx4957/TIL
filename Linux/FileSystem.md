# [Linux] FileSystem


## EXT
- Linux의 가장 대표적인 파일 시스템
- data modification timestamp와 inode 수정을 지원하지 않는ㄴ다 
- 연결리스트(linked list)를 통해 free block과 inode를 추적하기 떄문에 성능이 저하된다
- Max filename size(255 bytes)
- Max file size(2GB)

## EXT2 

### 단점
- 디스크를 쓰는 동안 시스템 충돌이나 전원이 끊어지면 심각한 손상을 야기한다. 이때 재부팅이 일어나며 e2fsck라는 검사 프로그램을 전체 파일시스템을 대상으로 실행해야하며 검사 중에는 파일시스템을 사용할수 없다.
## EXT3 
1. HTree 
2. 저널링 기능 지원
### 단점 
- 파일 시스템과 피일의 최대 크기가 작다
- 연속적인 데이터 블록에 대해 비효율적인 인덱스 방식 사용 
## EXT4 
1. 대용량 파일 시스템과 파일 크기 지원
- 
2. Pre-allocation(사전 할당)
3. Delayed allocation(지연 할당)
4. Extent 
## XFS 
- 64bit 파일시스템으로 대용량 파일시스템에 효율적이다.
- EXT4보다 큰 최대 16 EiB 파일시스템과 최대 8EiB 파일을 지원할 수 있습니다.

- B+tree를 사용하여 우수한 I/O 확장성을 제공하고 모든 사용자 데이터 및 메타데이터를 인덱싱합니다.

- 파일시스템이 마운트 되어 활성화되어 있는 동안 확장이 가능합니다.

- 파일시스템의 크기는 줄일 수는 없습니다.

- extent 기반 할당을 사용하며 지연할당 및 사전 할당과 같은 여러 할당 체계를 가지고 있습니다.

- extent 기반 할당은 메타데이터의 양을 감소시키고 단편화를 줄임으로써 대용량 파일의 성능을 향상시킵니다.

- 지연할당을 통해 파일이 연속적인 블록 그룹에 저장될 가능성을 높이기 때문에 단편화를 줄이고 성능을 향상시킵니다.

- 사전 할당을 통해 애플리케이션이 사전에 저장할 데이터의 양을 알고 있는 경우 조각화를 방지하는 데 사용될 수 있습니다.

출처:  
https://medium.com/naver-cloud-platform/posix-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0-1-linux-%EB%A6%AC%EB%88%85%EC%8A%A4-%ED%8C%8C%EC%9D%BC-%EC%8B%9C%EC%8A%A4%ED%85%9C%EC%9D%98-%EC%A2%85%EB%A5%98%EC%99%80-%ED%8A%B9%EC%A7%95-96a2e93e33b3
https://opensource.com/article/18/4/ext4-filesystem