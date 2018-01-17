
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

* 우측 중앙의 소프트웨어 선택란을 주목하자
![default](https://user-images.githubusercontent.com/27793242/35059026-26c00f4a-fbfd-11e7-896d-360aa2ca941a.PNG)

* 작성자는 GNOME으로 설정을 해주었다.
![2](https://user-images.githubusercontent.com/27793242/35059028-26f2278c-fbfd-11e7-9885-4d9f3b9bfa37.PNG)

* 암호 및 사용자 생성란.
![vm 6](https://user-images.githubusercontent.com/27793242/34790623-a4c42c46-f685-11e7-828b-6e09f7e48828.PNG)

* 모든 과정을 거치고 CentOS7의 바탕화면이 나왔다.
![3](https://user-images.githubusercontent.com/27793242/35059029-271f0810-fbfd-11e7-912c-2de5ff05d9d9.PNG)
>>좌측 상단의 프로그램을 클릭 하면 터미널이 열리게 된다. 앞으로의 설명은 터미널을 기준으로 설명하겠다.

* 먼저 패키지 관리 도구인 yum을 설치할 것이다. 맥의 brew와 같은 개념이다.
* 먼저 yum을 설치해줘야해서 명령어를 입력하면 아래와 같은 오류가 발생한다.
![4](https://user-images.githubusercontent.com/27793242/35059030-274fd0d0-fbfd-11e7-952b-7cd9ce8e4777.PNG)
>>root권한이 있어야 해당 명령을 실행 할 수 있다고 나온다.

* 아래와 같이 su를 입력하면 암호를 입력하라 나오는데 CentOS를 설치 할 때 입력한 root권한의 암호를 입력해준다.
![5](https://user-images.githubusercontent.com/27793242/35059031-277b2898-fbfd-11e7-81dd-88e6e80f0c44.PNG)

* 루트권한을 갖게되면 yum을 설치 및 관리가 가능해진다.
* 나는 설치시 이미 yum 이 설치되어있다는 문구가 나와서 업데이트를 해주었다.
![6](https://user-images.githubusercontent.com/27793242/35059032-27aab6b2-fbfd-11e7-9adf-3b7c10140793.PNG)

* 이후에 python --version 이라고 입력해주면 python의 버전이 2.x 일것이다.
* python의 버전을 3.x로 설치 및 버전 관리를 위해서 pyenv를 설치할것이다.
* pyenv 는 로컬에 다양한 파이썬 버전을 설치하고 사용할 수 있도록 한다.
* pyenv를 사용함으로써 파이썬 버전에 대한 의존성을 해결할 수 있다.

* 해당 명령어를 터미널에 순차적으로 입력한다.
yum -y install git
yum -y groupinstall "Development Tools"
yum -y install readline-devel zlib-devel bzip2-devel sqlite-devel openssl-devel
git clone https://github.com/yyuu/pyenv.git ~/.pyenv
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
source ~/.bash_profile
exec $SHELL -l

* pyenv-virtualenv도 추가 설치.(로컬에 파이썬 환경을 구축, 사용할 수 있도록 한다.
git clone https://github.com/yyuu/pyenv-virtualenv.git ~/.pyenv/plugins/pyenv-virtualenv
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bash_profile
exec $SHELL -l

* 설치가 완료되면 pyenv install 3.6.4 를 입력하여 파이썬 3.6.4를 설치할 수 있다.
* pyenv를 통해 인스톨 가능한 목록은 pyenv install --list 를 통해 확인할 수 있다.
* 최신버전이 있다면 목록을 확인 후 설치하면 된다.
![13](https://user-images.githubusercontent.com/27793242/35059046-2964f42c-fbfd-11e7-9347-5717bf18fbd1.PNG)

* pyenv global 3.6.4 를 입력하여 버전을 변경 후 pyenv version 을 입력해주면(스크린샷에는 다르게 나와있지만 둘다 확인 가능)
![14](https://user-images.githubusercontent.com/27793242/35059047-2996c380-fbfd-11e7-8276-c8064e889361.PNG)

* system상에 두가지 버전이 존재하는것을 확인할 수 있다.
![15](https://user-images.githubusercontent.com/27793242/35059048-29c53044-fbfd-11e7-8229-87239a206f5e.PNG)

* 추가로 pip install -U pip 을 입력하면 현재 global로 지정되어있는 파이썬의 버전을 사용자 환경의 기본으로 변경한다.
