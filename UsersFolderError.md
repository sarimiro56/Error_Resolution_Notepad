# USERS forder name edit error

![image](https://github.com/sarimiro56/Error_Resolution_Notepad/assets/128454837/a3f05635-afb7-4955-b0de-81c3a7738fa8)

:   상황설명

윈도우 로컬 계정을 하나 만들었는데 한글 이름으로 되어있었다. 그래서 나는 계정명을 영어로 변경했다.
그러나 계정명을 영어로 변경해도 사용자 폴더의 사용자명이 변경이 안된 것이었다.
그로 인하여 나는 그 상태로 프로그램들을 설치하고 사용하다가 어떤 프로그램을 설치하려 했는데,
한글 이름으로 되어있으면 설치가 안된다는 것이었다.

나는 인터넷에 검색한 대로 명령 프롬프트, 제어판, netplwiz에도 접속하여 이름을 계속 바꾸어보았으나
폴더의 사용자명이 변경이 안된 것이었다.
그래서 사용자 폴더명을 직접 수정해버렸더니 로컬 계정으로도 접속이 안되는 상황까지 벌어졌다.
그래서 내가 해결했던 방법은 https://wikidocs.net/161290 이 사이트에 있던 방법 2를 이용하는 것이었다.

결론. 로컬 사용자명 변경해도 사용자 폴더명이 변경되지 않고, 사용자 폴더명을 직접 수정했을 경우 해결 방법.

![image](https://github.com/sarimiro56/Error_Resolution_Notepad/assets/128454837/6507b185-f661-4f23-89ae-5d494db02056)

<ol>
    <li>관리자 권한을 가진 다른 계정으로 접속(내 경우에는 슈퍼 관리자가 cyci였다.)</li>
    <li>window + R 키를 누르고 "regidit"를 입력하여 레지스트리 실행.</li>
    <li>레지스트리 편집기에서 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList\<사용자 SID>\를 찾아서 ProfileImagePath의 값을 알맞게 변경.</li>
    <li>컴퓨터 재부팅.</li>
</ol>

##### 사용자 SID는 사용자 본인이 이게 어떤 건지 모를 경우가 더 많다.
##### 나 같은 경우에는 ProfileList에 있는 폴더들을 클릭해보다가 ProfileImagePath에 사용자 폴더 경로명이 적혀있는 걸 보고 구분해서 값을 변경했다.
##### SID 찾는 법은 직접 인터넷으로 찾아보길 바란다.

##### 예를 들어 내 로컬 계정 이름을 "사과"라고 지었는데, "apple"로 변경해도 폴더명이 변경 안 되어서 직접 변경했다면 레지스트리에서 경로 들어간 뒤에 C:\Users\사과 -> C:\Users\apple 이라고 값을 변경하고 재부팅만 하면 된다.

##### 이러면 로컬 계정에는 접속이 가능하나, 다른 문제가 생긴다.
##### 로컬 계정의 파일 탐색기에 등록되어있던 즐겨찾기 경로를 타고 가도 찾을 수 없다고 뜨거나, 기존에 설치된 프로그램들이 저장소를 못 찾는다고 난리를 칠 것이다.
##### 이럴 때는 침착하게 기존 경로들은 다 삭제하고 바뀐 경로로 바꾸어두면 웬만해서는 해결된다.
