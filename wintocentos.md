
# VirtualBox 다운로드 링크
* VirtualBox 5.2.4 platform packages의 Windows hosts로 다운로드.
* 추가로 VirtualBox 5.2.4 Oracle VM VirtualBox Extension Pack 의 
* All supported platforms. 확장팩도 다운로드.

>>[VirtualBox Link](https://www.virtualbox.org/wiki/Downloads)

# CentOS 다운로드 링크
* 무난하게 DVD ISO로 받는것을 추천.
>>[CentOS7 Link](https://extrememanual.net/7184)

# VirtualBox에러라서 VM Ware로 갈아탐
# VM Ware 다운로드는 구글의 vmware 워크스테이션 9 버전으로 찾아서 설치 권장(32,64비트를 전체 지원. 10버전부터 64비트만)
* 설치 후 실행시 Create a new virtual machine클릭
* 선택지가 두개가 있는데 Typical을 선택하자

* 그 다음엔 아래처럼 CentOS ISO파일을 지정해주고 NEXT 클릭
>>![vm 0](https://user-images.githubusercontent.com/27793242/34790615-a391caae-f685-11e7-96a5-ad31682138a6.PNG)

* next Step
>>![vm 1](https://user-images.githubusercontent.com/27793242/34790616-a3bbeff0-f685-11e7-894e-9374f42df884.PNG)

* 할당 용량 관련 설정. store virtual disk 를 체크
>>![vm 2](https://user-images.githubusercontent.com/27793242/34790617-a3e82bb0-f685-11e7-8ef6-0535924bd4d2.PNG)

* 내 설정에 대한것. Customize Hardware에는 다양한 설정이 있는데 건들지 말자.
>>![vm 3](https://user-images.githubusercontent.com/27793242/34790618-a41293a0-f685-11e7-927d-b723087b94ad.PNG)

* 이제 설치 바로 직전이다. 왼쪽 상단의 녹색 재생버튼을 누르면 라이센스를 등록하라고 나온다
![vm 4](https://user-images.githubusercontent.com/27793242/34790619-a4408300-f685-11e7-8bbf-8b40f23c7e12.PNG)
* 등록할 수 있는 라이센스 코드가 있는 웹 페이지 주소
>>![라이센스 코드](http://blog.naver.com/PostView.nhn?blogId=pdj2885&logNo=120176054673)

* 스크린샷에서 잘렸는데 설치요약 부분의 하단에 시스템란 하단에 네트워크 설정이 있는데 켬 으로 설정하자
![vm 5](https://user-images.githubusercontent.com/27793242/34790620-a46e22ec-f685-11e7-913c-fa8ad50ecdde.PNG)

* 암호 및 사용자 생성란.
![vm 6](https://user-images.githubusercontent.com/27793242/34790623-a4c42c46-f685-11e7-828b-6e09f7e48828.PNG)

* 설치가 완료되면 창이 열린다! 등록한 사용자명, 패스워드를 입력하고 python 설치에 도전한다.
![python 1](https://user-images.githubusercontent.com/27793242/34790614-a365c67a-f685-11e7-903c-e9ef17f9e4c2.PNG)

# 여기부터는 글로 설명
* CentOS 설치시 python 명령어를 입력하면 현재 버전은 2.7.5 정도일것이다( 확인후 리눅스 쉘로 나올땐 ctrl+d)

## 최신 환경 업데이트 순서
### 리눅스 환경 업데이트
* 먼저 현재 root로 로그인 된 상태가 아니니 root로 바꿔준다.
* su //입력시 root로 변환
* yum install // 입력 후 환경 업데이트. 다소 시간이 걸린다. 중간에 선택지가 나오는데 모두 y로 처리 하자
* yum install wget // 입력 설치. wget으로 파이썬을 설치할 예정
* wget https://www.python.org/ftp/python/3.6.4/Python-3.6.4.tgz // 입력하여 파일 받기
* ls // 입력하여 다운받은 파일 확인
* tar xvfz Python-3.6.4.tgz // 입력
* cd(change directory) 를 이용하여 파이썬 폴더로 이동
* ./configure --prefix=/usr/local/python3.6.4 --enable-shared // 설치. 중간에 뭐 선택지 나오면 무조건 y.
* 위의 과정이 끝나면 make install 입력
* yum install zlib-devel 입력
* ls // 입력하여 complete를 확인.
#　
# 　
#　
#　
# 여기까지 하고 나면 에러가 난다......
![default](https://user-images.githubusercontent.com/27793242/34790627-a5723f7a-f685-11e7-9ebc-486384b4617f.PNG)
