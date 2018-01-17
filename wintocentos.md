
# VirtualBox 다운로드 링크
* VirtualBox 5.2.4 platform packages의 Windows hosts로 다운로드.
* 추가로 VirtualBox 5.2.4 Oracle VM VirtualBox Extension Pack 의 
* All supported platforms. 확장팩도 다운로드.

>>[VirtualBox Link](https://www.virtualbox.org/wiki/Downloads)

# CentOS 다운로드 링크
* 무난하게 DVD ISO로 받는것을 추천.
>>[CentOS7 Link](https://extrememanual.net/7184)

# VirtualBox에러시엔 VM Ware로 갈아타면 된다. 작성기준은 VM WARE9 버전이다.

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

#별첨
### 아래 기술된 부분은 pyenv에 대한 추가적인 설명이다.
파이썬 버전 선택 순서
pyenv은 여러 개의 파이썬 버전을 설치할 수 있다. 그리고 pyenv가 파이썬 버전을 선택하는 순서를 올바르게 이해하고 정확히 사용하려는 파이썬 버전을 선택해야 한다.

PYENV_VERSION 환경변수의 값

pyenv shell 명령어로 현재 터미널 세션의 환경변수를 설정한다. 터미널이 열린 상태에서 특정 파이썬 버전을 선택하여 명령할 때 유용하다.

만약 환경변수 설정을 제거하려면 pyenv shell --unset으로 명령하거나 터미널을 종료하고 새로 연다.

.python-version 파일의 값

pyenv local 명령어로 현재 디렉토리 및 하위 디렉토리에서 실행되는 파이썬 버전을 설정한다. pyenv local 명령어로 .python-version 파일이 만들어지고 이 파일이 있는 디렉토리부터 재귀적으로 모든 하위 디렉토리에 적용된다. 따라서, 프로젝트 디렉토리 안에서 명시적으로 특정 파이썬 버전을 선택하고자 할 때 유용하다.

만약 디렉토리 설정을 제거하려면 pyenv local --unset으로 명령하거나 디렉토리 안에 .python-version 파일을 삭제한다.

$(pyenv root)/version 파일의 값

pyenv global 명령어로 시스템 전역의 파이썬 버전을 설정한다. $(pyenv root)/version 파일이 존재하지 않을 경우에는 "system" 디폴트 파이썬을 사용하는 것으로 간주한다.

많은 튜토리얼이 pyenv로 설치한 파이썬을 사용하기 위해 pyenv shell, pyenv local, pyenv global 명령어로 지정할 수 있다고 설명하고 각각의 차이를 설명하는 경우가 적다. 설정 우선순위 관계를 올바로 이해해야 사용할 때 혼동이 없다.

여러 개의 파이썬 버전 선택
tox 유틸리티로 호환성 검사할 때 매우 유용한 기능이다. pyenv를 통해 파이썬2와 파이썬3를 동시에 설치하여 빌드 검사를 할 수 있다.

앞서 우분투 16.04 LTS의 경우 시스템 패키지로 파이썬 버전 2.7.12, 3.5.2 버전이 설치되고 system 파이썬으로 분류된다고 언급했다. 그리고 pyenv install 명령어로 필요에 따라 여러 개의 파이썬을 설치했다.

python 명령어로 실행되는 기본적으로 실행되는 system 파이썬은 아래와 같다:

$ python -V
Python 2.7.12
$ python3 -V
Python 3.5.2
pyenv를 사용하여 개발환경을 구축하기로 한 이상 system 버전은 사용하지 않도록 하겠다.

이제 시스템 안에서 여러 개의 파이썬 버전을 선택하기 위해 python global 명령어로 버전을 나열해 지정할 수 있다.

$ pyenv global 3.6.2 3.5.3 3.4.7 2.7.13
이제 시스템에서 python, python3 명령어로 불러오는 버전을 확인해보면 다음과 같이 모두 pyenv로 설치한 3.6.2 버전인 것을 알 수 있다.

$ python -V
Python 3.6.2
$ python3 -V
Python 3.6.2
만약 3.5.3, 3.4.7, 2.7.13 같은 버전을 사용하고 싶다면 각각 python3.5, python3.4, python2.7 명령어로 호출할 수 있다. 아래 예시는 python2.7로 system 기본 버전 2.7.12가 아니라 2.7.13 버전이 실행되는 것을 확인할 수 있다.

$ python2.7
Python 2.7.13 (default, Aug 20 2017, 15:43:40) 
[GCC 5.4.0 20160609] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
파이썬 인터프리터 실행 파일의 위치를 확인하려면 아래의 명령어로 확인할 수 있다.

$ pyenv which python3.6
/home/user/.pyenv/versions/3.6.2/bin/python3.6
만약에 아래와 같이 오류가 발생한다면 파이썬이 올바로 설치되지 않은 것이다.

pyenv: python3.6: command not found

The `python3.6' command exists in these Python versions:
  3.6.2
또한 참고로 여러 버전의 파이썬을 지정하기 위해 python global 명령어가 아니라 python local 명령어로도 지정할 수 있다.

설치한 파이썬 삭제
pyenv install 명령어로 설치한 파이썬은 pyenv uninstall 명령어로 삭제할 수 있다.

pyenv uninstall 3.6.2
pyenv 삭제
pyenv 설정이 꼬이고 설치된 여러 버전의 파이썬이 뭔가 문제를 일으킨다면 pyenv 자체를 삭제할 수 있다.

pyenv의 삭제는 $(pyenv root) 경로의 디렉토리를 간단히 삭제하면 되는데 일반적으로는 ~/.pyenv 디렉토리이다.

virtualenv 가상환경
준비
curl로 인스톨러를 내려받아 pyenv 설치한 경우에는 virtualenv가 같이 설치되기 때문에 따로 설치할 필요는 없다. 그리고 앞서 ~/.bashrc 또는 ~/.bash_profile 파일에 다음 줄을 추가했기 때문에 가상환경을 위한 준비가 이미 되어 있다.

eval "$(pyenv virtualenv-init -)"
가상환경 생성
가상환경의 생성은 pyenv virtualenv 명령어로 생성한다.

pyenv virtualenv venv
현재 파이썬의 환경으로 venv 이름의 가상환경을 만들고 아래와 같이 결과를 확인할 수 있다.

$ pyenv versions
  system
* 2.7.13 (set by /home/user/.pyenv/version)
* 3.4.7 (set by /home/user/.pyenv/version)
* 3.5.3 (set by /home/user/.pyenv/version)
* 3.6.2 (set by /home/user/.pyenv/version)
  3.6.2/envs/venv
  venv
시스템 기본 파이썬 버전이 3.6.2이기 때문에 해당 버전을 기준으로 가상환경이 만들어졌다.

명시적으로 파이썬 특정 버전을 지정해서 가상환경을 만드려면 다음과 같이 명령한다.

$ pyenv virtualenv 3.5.3 venv
3.5.3 버전을 지정했고 그 결과는 아래와 같이 확인할 수 있다.

$ pyenv versions
  system
* 2.7.13 (set by /home/user/.pyenv/version)
* 3.4.7 (set by /home/user/.pyenv/version)
* 3.5.3 (set by /home/user/.pyenv/version)
  3.5.3/envs/venv
* 3.6.2 (set by /home/user/.pyenv/version)
  venv
가상환경 선택
가상환경을 선택하는 것은 결국 pyenv에서 어떤 버전의 파이썬을 선택할 것인가 하는 문제와 같다. 따라서 필요에 따라 pyenv shell, pyenv local, pyenv global 명령어 중 하나로 파이썬 버전을 선택한다.

$  pyenv shell venv
위와 같이 특정 가상환경을 선택하고 python, python3 버전을 확인해보면 다음과 같다.

(venv) $ pyenv which python
/home/user/.pyenv/versions/venv/bin/python
(venv) $ python -V
Python 3.5.3
(venv) $ pyenv which python3
/home/user/.pyenv/versions/venv/bin/python3
(venv) $ python3 -V
Python 3.5.3
위와 같이 쉘에서 (venv) 가상환경으로 진입한 경우에는 pyenv로 설치한 3.4, 3.6 같은 다른 버전의 파이썬을 명령행에서 찾을 수 없다.

$ pyenv which python3.4
pyenv: python3.4: command not found

The `python3.4' command exists in these Python versions:
  3.4.7
가상환경 삭제
가상환경의 삭제는 pyenv install로 설치한 파이썬을 삭제하는 pyenv uninstall 명령어와 같다.

$ pyenv uninstall venv
요약: pyenv/virtualenv 실무적 시나리오
pyenv를 사용하는 가장 큰 이유 중 하나가 tox와 연동하여 여러 버전의 파이썬으로 빌드 테스트하는 것이다. tox를 설명하는 것이 아니라 개발 환경을 만들고 tox를 연동하기 위한 방법을 설명한다.

pyenv 설치
$ apt-get install curl
$ curl -L https://raw.githubusercontent.com/pyenv/pyenv-installer/master/bin/pyenv-installer | bash
~/.bashrc 또는 ~/.bash_profile 파일 생성
export PATH="${HOME}/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
빌드 컴파일러 및 라이브러리 패키지 설치
$ sudo apt-get install build-essential libreadline-dev zlib1g-dev libbz2-dev libsqlite3-dev libssl-dev
pyenv로 파이썬 다운로드 빌드 설치
$ pyenv install 2.7.13
$ pyenv install 3.4.7
$ pyenv install 3.5.3
$ pyenv install 3.6.2
가상환경 설치 (-p 옵션을 주지 않으면 가상환경으로 진입했을 때 다른 버전의 python을 찾을 수 없음)
$ pyenv virtualenv -p python3.6 3.6.2 venv
여러 개의 파이썬 버전 선택(디폴트=venv 3.6.2 버전 가상환경)
$ pyenv global venv 3.5.3 3.4.7 2.7.13
만약 여러 개의 파이썬 버전을 등록해두지 않으면 이후 tox 명령어 실행 시 파이썬 인터프리터를 찾지 못해 가상환경이 생성하지 않는 오류가 발생할 수 있다.

파이썬 버전 쉘로 지정 ((venv) 프롬프트가 활성화되지 않은 경우)
$ pyenv shell venv
tox 설치 및 실행
$ pip install tox
$ tox
