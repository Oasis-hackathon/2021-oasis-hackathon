# git/github를 이용해 효과적으로 협업하기

## 짚고 넘어가야하는 point!

### 저장소의 종류

- **중앙 원격 저장소**

  여러 사람들이 함께 프로젝트를 관리하는 데 사용하는 저장소를 말한다. 그룹 계정의 원격 저장소 organization의 사용자와 저장소, 권한 설정들은 팀으로 관리한다.

- **원격 저장소(remote repository)**

  파일이 Github 전용 서버에서 관리되는 원격 저장소

- **로컬 저장소(local repository)**

  내 PC에 파일이 저장되는 개인 전용 저장소, 지역 저장소 (나만 볼 수 있는 공간!)



### 알고 있어야 하는 것들

- **clone**

  GitHub에 있는 특정 repository를 자신의 local 저장소에 복제하여 local에 새로운 저장소를 만드는 명령어

  ```
  $ git clone [remote repository URL]
  ```

  원격 저장소의 특정 branch를 clone 할 때

  ```
  $ git clone -b [브랜치 이름] [원격저장소 URL] 
  ```

- **fetch**

  원격 저장소의 데이터를 로컬에 가져옴

- **pull**

  원격 저장소의 내용을 가져와 자동으로 merge 작업 실행

  **pull = fetch + merge**

- `$ git branch`

  명령어로 branch 목록 확인

- git clone 이후 branch를 만들어 해당 branch에서 작업을 진행 한 후 중앙 원격 저장소(remote repository)에 push한다.

  ```
  $ git add * // 변경된 모든 파일 스테이징 영역에 추가
  $ git add [file-name]	// 파일을 선택하여 스테이징 영역에 추가
  $ git commit -m "commit message"
  ```

- pull request

  1. 커밋 완료 후 작업한 내용을 포함한 브랜치를 중앙 원격 저장소에 push한다.

     ```
     $ git push -u origin [branch name]
     ```

  2. push 이후 작업한 branch에서 pull request한다.

     **pull request**

     pull request는 기능 개발이 끝나고 master에 바로 병합(merge)하는 것이 아니라 브랜치를 중앙 원격 저장소에 올리고 master에 **병합(merge)요청**을 하는 것을 말한다.

  3. compare & pull request를 선택 해 메시지를 작성하고 PR을 한다.

  4. 코드 리뷰 이후 merge 여부를 선택한다.

  5. "merge를 했다"는 동기화 및 branch를 삭제했다 라는 행위이다.

     원격 저장소에 merge가 완료되면 로컬 코드와 원본 저장소의 코드를 동기화한다.

     master branch로 이동 후 해당 명령어를 실행하여 코드를 동기화시킨다.

     ```
     $ git pull master
     	or
     $ git pull origin master
     $ git branch -d [branch-name]
     ```

     (추가 작업은 git pull master 명령어를 통해 원본 저장소와 동기화를 진행하여 branch 생성 후 작업을 진행한다.)



### 원격 저장소 내 다른 branch를 가져올 때

**사례**

- 협업을 하고 있는 다른 팀원의 branch를 가져와 작업하는 경우
- 개인이 여러 환경에서 작업하는 경우

1. 원격 저장소 branch 확인

   - `git branch -r`

     원격 저장소의 branch 리스트 확인

   - `git branch -a`

     로컬, 원격 저장소의 branch 리스트 확인

   - `git push origin --delete [branch_name]`

     원격 브랜치 삭제

2. 원격 저장소 branch 가져오기

   - `git checkout -t [원격 저장소 branch 이름]`

     로컬에 branch를 생성하고 해당 branch로 checkout

   - `git checkout -b [생성할 branch 이름] [원격 저장소 branch 이름]`

     원격 저장소 branch를 가져오면서 이름을 변경



### forking workflow

- **fork**

  중앙 원격 저장소를 포크(fork)해서 자신만의 원격 저장소를 만든다.

  - 중앙 원격 저장소를 자신의 github 계정 저장소(repository)에 복제한다.
  - 중앙 원격 저장소와 똑같은 내용의 저장소로 복제!
  - 개인 공개 저장소로 저장되므로 중앙 원격 저장소와 독립적으로 운영됨

- **git clone**

  자신의 원격 저장소 (fork 후 생긴) 를 로컬 저장소에 복제함

- 원격 저장소와 연결한다.

  `git remote add upstream[자신이 정한 중앙 원격 저장소 url의 이름] [중앙 원격 저장소 url]`

  - 각 url에 이름을 붙여 줄 수 있음
  - 프로젝트 중앙 원격 저장소는 **upstream**으로 이름을 지음

- 자신이 구현할 기능 이름으로 브랜치 생성 후, 그 브랜치로 이동하여 프로젝트 작업 진행

  - 새로운 기능 개발을 할 때는, master 브랜치와 격리된 새로운 branch를 만들 것

  - branch 이름은 구현할 기능 이름으로!

  - 새로 만든 브랜치로 이동한 후 코드를 작성하고 변경 내용을 커밋하여 프로젝트를 진행함

    `git checkout -b [branch name]`

    ```c
    git branch [branch name] // 새로운 브랜치 생성
    git checkout [branch name] // 해당 브랜치로 작업 위치 이동
    ```

- 로컬 저장소에서 커밋한 이력을 자신의 원격 저장소로 push!

  - 기능 구현을 마친 후 커밋한 내용을 푸시 할 때, 프로젝트 중앙 원격 저장소가 아닌, 자신이 복제(clone) 자신의 원격 저장소에 push!

    ```
    git add . // 나 코드 작성 해서 변경 한 것 추가 할 거다.
    git commit -m "커밋 메세지"   // 이번에 변경한 것은 "commit 메세지" 참고해라
    git push origin [branch name]  // [branch name]에 해당하는 브랜치를 자신의 원격 저장소에 push
    ```

- 이후 과정은 위에 나온 pull request 과정

- 중앙 원격 저장소에 새로운 커밋은 로컬 저장소에 갱신!

  `git pull upstream master`

  - 최신 상태로 동기화 시킨다.
  - 중앙 코드 베이스가 변경되면, 모든 프로젝트 팀원은 자신의 로컬 저장소를 동기화해서 최신 상태로 만든다.

- 새로운 기능을 추가 할 때는 그 작업에 대한 branch를 생성한다.

  - 이때 최신 상태로 동기화된 로컬 저장소의 master 브랜치에서 새로운 작업에 대한 브랜치를 생성하여 또 다른 작업 하기
  - master 브랜치는 항상!! 최신 상태 유지