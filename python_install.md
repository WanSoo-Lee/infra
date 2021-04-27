## python 설치 방법
1. python 설치시 일반 user로 설치 할지 root로 설치 할지에 대한 결정이 필요하다.
2. apt나 yum 으로 설치는 root 로 설치 해야 하지만, 일반 user도 설치 할 수 있다.
3. python 을 여러 버전으로 설치 할 수 있다.
4. python 의 가상 환경을 적극적으로 활용한다.

**. 개발 라이브러리 다운
소스설치에 필요한 라이브러리들을 다운받는다

$ sudo apt-get install build-essential checkinstall
$ sudo apt-get install libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev libffi-dev zlib1g-dev

**. 파이썬 다운
$ cd /opt
$ sudo wget https://www.python.org/ftp/python/3.9.1/Python-3.9.1.tgz
$ sudo tar xzf Python-3.9.1.tgz

**. 파이썬 컴파일
$ cd Python-3.9.1
$ sudo ./configure --enable-optimizations
$ sudo make altinstall

**. 파이썬 버전 확인
$ python3.9 -V

Python 3.9.1

**. 파이썬 3.9를 python커맨드의 디폴트로 설정하기
위와 같은 방법으로 파이썬을 설치했다면 파이썬 3.9의 경로는 /usr/local/bin/python3.9 일 것이다

update-alternatives로 python 커맨드의 디폴트 경로를 설정해줄 수 있다

sudo update-alternatives --install /usr/bin/python python /usr/local/bin/python3.9 1
혹시나 설치 경로를 못 찾겠다면 whereis 커맨드를 사용하면 된다

$ whereis python3

python3: /usr/bin/python3.9 /usr/bin/python3.9m /usr/bin/python3 /usr/lib/python3.9 /usr/lib/python3.8 /usr/lib/python3.7 /usr/lib/python3 /etc/python3.6 /etc/python3 /usr/local/bin/python3.8 /usr/local/bin/python3.8-config /usr/local/lib/python3.6 /usr/local/lib/python3.8 /usr/include/python3.6m /usr/share/python3 /usr/share/man/man1/python3.9.gz
설정이 끝나면

$ python -V

Python 3.9.1


### PIP install on ubuntu 20.04
$ curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
$ python get-pip.py --user
$ /usr/bin/python -m pip install --upgrade pip
