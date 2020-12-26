# git/github tutorial

본 문서는 Git/Github이 처음이신 참가자들을 위한 Git/Github 및 간단한 명령어와 기능 소개를 담은 문서입니다.

1. Git/Github란?

2. Git의 명령어 소개

   add, commit, push, branch, clone

3. Github 기능 소개

   pull request, issue, review, merge

4. 시작해보기



## Git/Github란?

### Git이 무엇인가요?

- 효율적인 버전 관리 시스템을 사용하기 위해
- 빠르게 협업환경을 조성할 수 있음
- 여러 사람들과 함께 누가, 언제, 무엇을 수정했는지 리뷰가능
- Github을 이용해 자신의 local에서 개발한 내용 공유 가능
- visual studio, IntelliJ, Android Studio 등 다양한 IDE에서 git 연동 제공



### GitHub은 왜 사용하나요?

- Git의 데이터를 저장하는 서버의 역할을 함
- 커뮤니티 기능이 잘 되어 있음. (Issue를 통한 버그 제시 등)

- 코드를 보면서 의견을 나눌 수 있음(리뷰 기능)
- 오픈 소스의 발전에 영향을 미침



### Git/Github란?

여러 대의 **컴퓨터**들(Git)과 하나의 **메인서버**(GitHub)가 **소통**하는 관계



## Git의 명령어소개

add, commit, push, branch, clone

- **add**

  저장을 원하는 파일들을 묶어 올리겟다. / 스테이지에 올린다.

  *(내가 구현한 기능을 전달하기 위한 준비 단계를 한다.)*

- **commit**

  저장하는 파일들을 묶어서 **save** 하겠다.

  *(내가 구현한 기능들은 말이지... "horse"야!)*

- **push**
  내 컴퓨터에 저장된 작업 내용을 github에 업로드한다.

  *(내가 "horse"를 구현했는데 너희들에게 보낼게! 확인 부탁해!)*

- **branch**

  개발 영역을 분담해서 작업할 때, 충돌 예방 방지를 위해 자체에서 개별 branch를 생성해, 기존에 있던 내용을 가져와 개별적으로 작업한다.

  *(너가 'horse'를 구현했으니! 나는 'dolphin'을 구현해야겠군!)*

- **clone**

  원격 저장소 내려 받기(저장소 복제하기)

  *(개발해둔 horse v1 기반으로 v1.1을 만드려는데 기존에 작성한 코드를 참고해야겠다.)*



## GitHub의 기능소개

pull request, review, merge

- **pull request**

  Github의 강력한 협업 기능

  *(세상 사람들! 우리 'horse'가 걸을 수 있어요~ 한번 이상 없는지 봐주세요!)*

- **review**

  pull request내용을 점검하는 기능, 리뷰를 통해 공동 학습 할 수 있음

  *(오! 네 알겠습니다. 음 'horse'의 이 부분은 좀 더 수정봐야할 것 같아요!)*

- **merge**

  각자의 branch를 합치는 과정



## 시작해보기

### 설치

아래의 바로가기를 통해 진행해주세요!

[바로가기](https://git-scm.com/downloads)

### 설정

1. git의 config 과정을 진행합니다.	

   ```
   $ git config --global user.name "username"
   $ git config --globas user.email "useremail@email.com"
   ```

2. `git clone` 명령어를 통해 원격저장소에 저장된 파일을 컴퓨터로 복사해옵니다.

   ```
   $ git clone https://github.com/Oasis-hackathon/2021-oasis-hackathon.git 
   ```

   |                        주소 복사하기                         |          terminal           |
   | :----------------------------------------------------------: | :-------------------------: |
   | <img src="./img/clone image.png" alt="clone image" style="zoom:50%;" /> | ![clone2](./img/clone2.png) |

   `git clone` 을 통해 원격파일을 복사해오면, `origin`에는 `clone`해온 리모트 URL이 저장되있습니다.

   

### 시작하기

1. 개발을 진행하신 후`git add` 명령어를 이용해서 소스 코드를 업로드 합니다.

   ```
   $ git add . 
   ```

<img src="./img/add.png" alt="clone image" style="zoom:50%;" />

2. 