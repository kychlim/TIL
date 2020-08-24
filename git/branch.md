# branch

## 기본 명령어





첫글자	+tap키 (만들어 놓은 hellobranch라는 이름 자동완성됨)

브렌치 병합시 Fast-forward된다는 의미는 master branch 가 병합되는 브렌치로 전진하여 병합된다는 의미

HEAD는 내가 있는 위치를 말해줌

```bash
$ git log --oneline --graph
```





```bash
$ git branch # 브렌치 보기
$ git branch (브렌치 이름) #브렌치 생성

#브렌치 이동
$ git chechout (브렌치이름)
$ git checkout -b (브렌치이름) #브렌치 생성 및 이동


#브렌치 병합
$ git merge (브렌치 이름) #(브렌치이름)을 (master)로 병합

#브렌치 삭제
$ git branch -d (브렌치 이름)
## 병합했다고 자동으로 병합 된 branch가 삭제되는 것이 아님.(충돌 방지를 위해 삭제해 줄 것)
```



**세 가지 병합 상황 가정**

상황1 (충돌x)

- A  feature branch - 변경
- B master branch - 불변



상황2(충돌x) -- 자동 conflict 해결됨

- A  feature branch - c 수정
- B master branch - d 수정



상황3(충돌o) --직접 수정 후 merge commit 을 해줘야 함. 

- A  feature branch - c 수정
- B master branch - c 수정





### 상황 1. fast-foward

> fast-foward는 feature 브랜치 생성된 이후 master 브랜치에 변경 사항이 없는 상황

1. feature/test branch 생성 및 이동

   

2. 작업 완료 후 commit

   


3. master 이동

   


4. master에 병합

   


5. 결과 -> fast-foward (단순히 HEAD를 이동)

   

6. branch 삭제

   

---

### 상황 2. merge commit

> 서로 다른 이력(commit)을 병합(merge)하는 과정에서 다른 파일이 수정되어 있는 상황
>
> git이 auto merging을 진행하고, commit이 발생된다.

1. feature/signout branch 생성 및 이동

   

2. 작업 완료 후 commit

   

3. master 이동

   

4. *master에 추가 commit 이 발생시키기!!*

   * **다른 파일을 수정 혹은 생성하세요!**

   

5. master에 병합

   

6. 결과 -> 자동으로 *merge commit 발생*

   * vim 편집기 화면이 나타납니다.

   * 자동으로 작성된 커밋 메시지를 확인하고, `esc`를 누른 후 `:wq`를 입력후 `Enter`입력하여 저장 및 종료를 합니다.

      * `w` : write
      * `q` : quit

   * 커밋이  확인 해봅시다.

      

7. 그래프 확인하기

   

8. branch 삭제

   

---

### 상황 3. merge commit 충돌

> 서로 다른 이력(commit)을 병합(merge)하는 과정에서 동일 파일이 수정되어 있는 상황
>
> git이 auto merging을 하지 못하고, 해당 파일의 위치에 라벨링을 해준다.
>
> 원하는 형태의 코드로 직접 수정을 하고 merge commit을 발생 시켜야 한다.

1. feature/board branch 생성 및 이동

   

2. 작업 완료 후 commit

   


3. master 이동

   


4. *master에 추가 commit 이 발생시키기!!*

   * **동일 파일을 수정 혹은 생성하세요!**
   
햣
   
5. master에 병합

   


6. 결과 -> *merge conflict발생*

   


7. 충돌 확인 및 해결

   


8. merge commit 진행***********

    ```bash
    $ git commit
    ```

   * vim 편집기 화면이 나타납니다.
   
   * 자동으로 작성된 커밋 메시지를 확인하고, `esc`를 누른 후 `:wq`를 입력하여 저장 및 종료를 합니다.
      * `w` : write
      * `q` : quit
      
   * 커밋이  확인 해봅시다.
   
9. 그래프 확인하기

     


10. branch 삭제

    
