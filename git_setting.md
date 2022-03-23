### git
```
*git(git-scm.com) 설치->프로그램을 관리
*github 회원가입-> 포토폴리오
*영타연습하기
* ip주소 검색 방법
->윈도우 검색창->cmd(명령프로그램)-> ipconfig-> enter
->IP주소= IPv4 주소 . . . . . . . . . : 192.168.0.15 (15는 호스트 주소)
```

### 파일 및 내용 다운로드,추가 및 수정
```
1. git clone+깃허브 주소  =   깃허브 내용 다운로드
2. git add .   =   파일 추가
3. git commit -m '(fix(수정), feat(추가) : 내용)'    =   현재까지 내용 저장
4. git push origin master       =     깃허브에 업로드
```

### ssh key 생성
```
git config --global user.(이름,메일) ""
ssh keygen -t rsa -C "mail" <"C"는 대문자 
key 생성[SHA256 암호화 방법]

회사 입사 하면 가장 먼저 해야할것 : 내 PC -보기 - 파일확장명체크 (파일 구별 위한)
내PC>C드라이브 > 사용자 > .ssh 키 파일 <보관>확장명 체크 해야 볼수 있음.


ssh keys add new
title
key 코드 복붙
bash here
>ls //파일 보임.
```

### 저장소 첫 파일 올리는 방법
```
>git init  (최초 한번만 입력)(폴더를 만들고 init을 입력하면 그 폴더는 깃저장소가 됨)
>git add .
>git config --global user.name"사용자 이름 입력"
>git config --global user.email"이메일 입력"
(git config --global core.autocrlf true//오류 발생시 입력)
>git remote add origin (파일 올릴 주소 코드)
>git commit -m "나 오늘 공부했어!"
>git push origin master 
```

### git 내용수정
```
-git add .
-git commit -m '아무내용이나'
-git push oringin master
```
