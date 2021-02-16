# branch

## 기본 명령어

첫글자 +tap키 (만들어놓은 이름 자동완성됨)



```bash
$ git branch

$ git branch (브랜치 이름) #브랜치 생성

#브랜치 이동
$ git checkout (브랜치 이름)
$ git checkout -b (브랜치 이름) #브랜치 생성 및 이동

# 브랜치 병합
$ git merge (브랜치 이름) #(브랜치 이름)을 (master)로 병합

# 브랜치 삭제
$ git branch -d (브랜치 이름)
```





### 상황 1. fast-foward

> fast-foward는 feature 브랜치 생성된 이후 master 브랜치에 변경 사항이 없는 상황

1. feature/test branch 생성 및 이동

   ```bash
   $ git checkout -b {브랜치 이름}
   $ git checkout -b feature/blog
   Switched to a new branch 'feature/blog'
   (feature/blog) $
   ```

   

2. 작업 완료 후 commit

   ```bash
   $ touch blog.html
   $ git add blog.html
   $ git commit -m 'Complete blog app'
   $ git commit -m 'Complete blog app'
   [feature/blog c3f9b07] Complete blog app
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 blog.html
   ```
   
   


3. master 이동

   ```bash
   $ git checkout master
   Switched to branch 'master'
   (master) $
   $ git log --oneline
   67fba2b (HEAD -> master, hellobranch) Hellobranch
   f99248c Init
   ```
   
   


4. master에 병합

   ```bash
   $ git merge feature/blog
   Updating 67fba2b..c3f9b07
   Fast-forward     <-- 핵심 
    blog.html | 0
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 blog.html
   ```
   
   


5. 결과 -> fast-foward (단순히 HEAD를 이동)

   ```bash
   $ git log --oneline
   c3f9b07 (HEAD -> master, feature/blog) Complete blog app
   67fba2b (hellobranch) Hellobranch
   f99248c Init
   ```

   

6. branch 삭제

   ```bash
   
   $ git branch -d feature/blog
   Deleted branch feature/blog (was c3f9b07).
   
   ```
   
   

---

### 상황 2. merge commit

> 서로 다른 이력(commit)을 병합(merge)하는 과정에서 다른 파일이 수정되어 있는 상황
>
> git이 auto merging을 진행하고, commit이 발생된다.

1. feature/poll branch 생성 및 이동

   ```bash
   $ git checkout -b feature/poll
   Switched to a new branch 'feature/poll'
   ```

   

2. 작업 완료 후 commit

   

3. master 이동

   

4. *master에 추가 commit 이 발생시키기!!*

   * **다른 파일을 수정 혹은 생성하세요!**

   ```bash
   $ touch hotfix.css
   $ git add .
   $ git commit -m 'hofix in master'
   $ git commit -m 'hofix in master'
   [master 2907900] hofix in master
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 hotfix.css
   $ git log --oneline
   2907900 (HEAD -> master) hofix in master
   c3f9b07 Complete blog app
   67fba2b (hellobranch) Hellobranch
   f99248c Init
   
   ```

   

5. master에 병합

   

6. 결과 -> 자동으로 *merge commit 발생*

   * vim 편집기 화면이 나타납니다.
   
   * 자동으로 작성된 커밋 메시지를 확인하고, `esc`를 누른 후 `:wq`를 입력하여 저장 및 종료를 합니다.
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
   

   
5. master에 병합

   


6. 결과 -> *merge conflict발생*

   
   
   
   1. 충돌 확인 및 해결
   
   


8. merge commit 진행

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

    
