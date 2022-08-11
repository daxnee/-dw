#########################################################
npm install error 최종해결


1. 레파지토리 URL복사 후 VSCode로 clone(왠만하면 D:에 저장)
참고 사이트 => https://github.com/codejone/oasis

2. clone한 파일들 중 frontend OR msa 폴더만 VSCode에서 폴더 열기=> 왼쪽 nav바 하단에 활성화된 Gradle 아w이콘 확인하기

3. frontend 터미널에 node -v , npm -v 버전 확인하고 package-lock.json파일에서 삭제 => 명령어 : npm install 입력 후 엔터

4. 트러블슈팅 
		npm ERR! code ERESOLVE
		npm ERR! ERESOLVE unable to resolve dependency tree
		npm ERR!
		npm ERR! While resolving: my-app@4.4.0
	***	npm ERR! Found: vue-property-decorator@9.1.2
		npm ERR! node_modules/vue-property-decorator
		npm ERR!   vue-property-decorator@"^9.1.2" from the root project
		npm ERR!
		npm ERR! Could not resolve dependency:
	***	npm ERR! peer vue-property-decorator@"^7.2.0 || ^8.0.0" from ag-grid-vue@25.3.0 // peer에 해결 방법이 있음!!
		npm ERR! node_modules/ag-grid-vue
		npm ERR!   ag-grid-vue@"^25.1.0" from the root project
		npm ERR!
		npm ERR! Fix the upstream dependency conflict, or retry
		npm ERR! this command with --force, or --legacy-peer-deps
		npm ERR! to accept an incorrect (and potentially broken) dependency resolution.
		npm ERR!
		npm ERR! See C:\Users\codej-220403\AppData\Local\npm-cache\eresolve-report.txt for a full report.

		npm ERR! A complete log of this run can be found in:
		npm ERR!     C:\Users\codej-220403\AppData\Local\npm-cache\_logs\2022-08-05T06_53_53_120Z-debug-0.log
	

해석 : vue-property-decorator의 찾은 버전과 현재 버전이 다르다는 의미 peer에 명시된 ' ^7.2.0 또는 ^8.0.0 ' 로 변경해줘야 한다.
	  *version만 잘 맞게 해주면된다는 뜻임
	  
	  => 이렇게 에러 났을시 mismatch된 버전들 맞춰주고 > npm install 해주면서 진행하면 된다.

5. 해결방법
	5-1) package.json 파일 열어서 dependencies에 버전 변경을 희망하는 key값을 찾아서 변경해준다. ex) "vue-property-decorator": "^9.1.2"  => "vue-property-decorator": "^8.0.0"
	5-2) 같은 에러가 계속 뜨면 표시되어있는 버전만 맞게 해준뒤 npm install 입력 => install 완료
	
6. 명령어 : npm run dev 입력 후 엔터 => 에러가 나면 해당 파일 들어가서 버전만 맞춰주면 된다.

7. 실행완료 되면 개발자도구(F12) 열어서 에러 확인 (vuejs 에서 store 관련 async 와 await 관련 오류)

8. 트러블슈팅
	Uncaught ReferenceError: regeneratorRuntime is not defined
    at componentNormalizer.js:1:62592
    at Object.install (componentNormalizer.js:1:63113)
    at Vue.use (SockJSClient.js:5107:1)
    at ./src/main.js (validate.js:70:5)
    at __webpack_require__ (bootstrap:848:1)
    at fn (bootstrap:150:1)
    at 1 (app.js:178792:18)
    at __webpack_require__ (bootstrap:848:1)
    at checkDeferredModules (bootstrap:45:1)
    at bootstrap:924:1
	
9.해결방법
참고 사이트 => https://become-a-developer.tistory.com/entry/vuejsregeneratorruntime-is-not-defined-vue-async-%EC%97%90%EB%9F%AC-%ED%95%B4%EA%B2%B0
	명령어 하나씩 실행
	npm install --save-dev babel-polyfill
	npm install --save-dev babel-plugin-transform-regenerator
	npm i babel-plugin-transform-runtime
		
	scr/main.js (scr폴더안에 main.js 파일에) 
	
	import 'regenerator-runtime/runtime' 의존성 추가
	
10. npm run dev 명령어 실행 완성!!!!!
	
#########################################################



---------------------------------------------------------
버전과 모듈 문제로인해 트러블 슈팅
	1-1) node.js 폴더 제거
	1-2) Roaming 폴더에서 npm && npm-cache 폴더 삭제
	1-3) node.js 최신버전 다운로드(프로젝트와 맞는 버전으로 설치하는게 best)
	1-4) 터미널에 npm -v 확인 , node -v 확인
	1-5) npm install --force ==> 성공
	1-6) npm install ==> 실패
참고 사이트 ==> https://manition.tistory.com/31
---------------------------------------------------------


---------------------------------------------------------
트러블 슈팅
npm WARN config global `--global`, `--local` are deprecated. Use `--location=global` instead.

해결 내용
1. Windows PowerShell 관리자 권한으로 실행
2. Set-ExecutionPolicy Unrestricted -Scope CurrentUser -Force 입력 후 엔터
3. npm-windows-upgrade 입력 후 엔터
4. 버전 화살표키로 선택 후 엔터

참고사이트 ==> https://yaongdaong.tistory.com/entry/Error-npm-WARN-config-global-global-local-are-deprecated-Use-locationglobal-instead
---------------------------------------------------------


---------------------------------------------------------
트러블 슈팅
npm ERR! code ERESOLVE
npm ERR! ERESOLVE unable to resolve dependency tree

해결방법

명령어 입력
npm install react-porject --save --legacy-peer-deps
===> 에러 발생
트러블 슈팅
npm ERR! code E404
---------------------------------------------------------


npm == Node Packaged Manager(Node.js)


명령어 ==> npm-check-updates
		npm-check-updates는 package.json의 dependencies와 devDependencies에 기록되어있는 패키지들을
		현재기준 최신버전으로 업데이트 시켜준다.
		
		npm install
		
		