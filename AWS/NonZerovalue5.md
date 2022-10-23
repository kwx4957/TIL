# [AWS] Process finished with non-zero exit value 5

- 문제: build.gradle에서 ELB에 환경설정을 코드들이 정상적으로 빌드가 되지 않고 다음과 같은 에러가 발생하였다. 

```groovy
Caching disabled for task ':release' because:
  Build cache is disabled
Task ':release' is not up-to-date because:
  Task has not declared any outputs despite executing actions.
Starting process 'command 'eb''. Working directory: Command: eb setenv SPRING_PROFILES_ACTIVE=prod
Successfully started process 'command 'eb''
:release (Thread[Execution worker for ':',5,main]) completed. Took 0.269 secs.

FAILURE: Build failed with an exception.
```

- 원인: 원인은 단순하다. 내가 eb를 설정한 디렉토리는 /Users/main이다. 하지만 빌드를 하는 디렉토리는 springboot 디렉토리였다. 즉 aws설정 정보에 대한 파일이 있어야 배포가 가능한데 springboot/ 에는 해당 aws 설정 정보에 대한 파일이 없기에 발생한 문제이다

- 해결
> eb use "ELB 환경이름"   
> $ ./gradlew release