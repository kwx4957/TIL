# [Git] 잘못된 계정으로 push한 경우

## 문제
vsc를 통해 .md파일을 작성하는데 다른 계정으로 push가 되었다. 이를 수정하고자 한다. 

## 과정
> git rebase -i -p "커밋내역"  

출처 블로그를 따라 해당 명령어를 따라 하였으나 다음과 같은 에러가 발생하였다.

~~~
fatal: --preserve-merges was replaced by --rebase-merges
Note: Your `pull.rebase` configuration may also be set to 'preserve',
which is no longer supported; use 'merges' instead
~~~
해당 명령어의 -p 옵션을 지원하지 않는다고 한다. 그래서 다음과 같이 명령어를 입력하였다.
> git rebase -i --rebase-merges "직전 커밋"

하지만 기존에 수정한 파일중 커밋하지 않은 파일들이 존재하여 다음과 같은 에러가 발생하였다.
~~~
error: cannot rebase: You have unstaged changes.
~~~

그렇기에 먼저 git stash를 해준다. 
1. git stash
2. git rebase -i --rebase-merges "직전 커밋"  
pick으로 되어있는 것을 edit으로 바꾸어준다.
![](../Img/FixAuthor/1.PNG)
![](../Img/FixAuthor/2.PNG)
edit를 eidt이라 하여 다음과 같은 에러가 발생하였다. 아래 명령어를 통해 다시 수정한다.
3. git rebase --edit-todo
4. git commit --amend --author="qwer <qwerqwre@naver.com>"  
작성자 이름과 이메일을 수정한다. 
5. git rebase --continue  
더이상 수정하고자 하는 파일이 없다면 rebase 작업을 종료한다.
6. git push origin -f master
변경된 로컬 내역들을 푸쉬해준다.
7. git stash pop 


해결 완료! 
![](../Img/FixAuthor/3.PNG)


출처:  
https://github.com/madplay/madplay.github.io/issues/92  
https://sustainable-dev.tistory.com/122