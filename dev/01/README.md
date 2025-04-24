# IDE 설치 - ECLIPSE
JAVA 설치(홈페이지) - JDK21
---
### 1. [Oracle](https://www.oracle.com/kr/java/technologies/downloads/#jdk21-mac) 접속하여 파일 다운로드 및 설치

|설치과정|
|-|
|![image](./img/01.png)|
|![image](./img/02.png)|
|![image](./img/03.png)|
|![image](./img/04.png)|
|![image](./img/05.png)|
|![image](./img/06.png)|

<br>

### 2. 설치 및 버전 확인
- Spotlight 검색(command + space)에서 터미널 오픈 후 명령어 입력

> 명령어
```
java --version
```

|버전 확인|
|-|
|![image](./img/07.png)|
|![image](./img/08.png)|

<Br>

### 3. 설치 경로 확인
- Spotlight 검색(command + space)에서 터미널 오픈 후 명령어 입력

> 명령어
```
which java
```

|경로 확인|
|-|
|![image](./img/09.png)|

<br>

### 4. 환경변수 설정

|환경변수|
|-|
|![image](./img/10.png)|
|![image](./img/11.png)|
|![image](./img/12.png)|
|![image](./img/13.png)|
|![image](./img/14.png)|

<br>

> 1. Java 기본 설치 경로 이동
```
cd /Library/Java/JavaVirtualMachines
```
- 'ls' 명령어를 통해 설치한 JDK 파일 있는지 확인


<br>

> 2. 설치된 JDK 확인 후 홈 이동
```
cd 확인한 JDK 폴더명/Contents/Home
```

<br>


> 3. 환경변수로 설정할 JDK 경로 복사
```
pwd
```

<br>

> 4. 복사한 경로를 .bash_profile 에 붙여넣어 JAVA 경로 설정
```
vi ~/.bash_profile
```
- vi 편집기는 처음 실행시 읽기 모드
  
  - i를 눌러 insert 모드로 변환 후 입력

<br>

> 5. 환경변수 설정
```
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-21.jdk/Contents/Home
PATH=&{PATH}:&JAVA_HOME/bin
export JAVA_HOME
export PATH
```
- Esc 키를 눌러 vi 편집기를 insert 모드에서 다시 읽기 모드로 변경
  
  - 읽기 모드에서 shift + ; 눌러 나가기 모드로 전환
    
    - Wq! 입력 후 enter (저장 후 나가기)

<br>

> 6. vi편집기로 입력한 환경변수 값 적용
```
source .bash_profile
```
- vi편집기로 환경변수 값을 저장한 후 source 명령어를 이용해 적용

  - macOS 버전 10.15 인 ‘카탈리나’ 부터 기본 쉘 (Shell) 이 bash 에서 zsh (Z shell) 로 변경
  
  - 맥 터미널에서 zsh쉘을 디폴트로 사용하므로 bash_profile에 있는 환경변수들을 불러오지 못하는 문제 발생
 
    - `source: no such file or directory: .bash_profile`

<br>

#### 💡 [해결] .zshrc 파일을 vim로 들어가 아래 코드 작성
```
vim ~/.zshrc
```
```
if [ -f ~/.bash_profile ]; then
        . ~/.bash_profile
fi
```
- 터미널 종료 후 다시 실행

<br>

> 7. 설정된 환경변수 확인
```
echo $JAVA_HOME 
```
- JAVA_HOME 으로 입력한 값이 설정되었는지 확인

<br>

---

<br>

JAVA 설치(HOME BREW) - JDK1.8
---
### 1. [홈브류 홈페이지](https://brew.sh) 접속 후 Install Homebrew 명령어 복사

|brew|
|-|
|![image](./img/21.png)|

<br>

### 2. 터미널에서 실행 후 맥북 비밀번호 입력 후 엔터
> 명령어
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

|brew|
|-|
|![image](./img/22.png)|
|![image](./img/23.png)|

<br>

### 3. 경로 설정

|brew|
|-|
|![image](./img/24.png)|

> Next steps 의 명령어 추가 실행
```
echo >> /Users/사용자명/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/사용자명/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

<br>

### 4. 설치 확인

|brew|
|-|
|![image](./img/25.png)|

> 명령어
```
brew --version
```

<br>

### 5. JAVA8 설치를 위한 명령어 입력
> Apple Silicon 인지 Intel인지 확인
```
arch
```
- arm64면 Apple Silicon, i386이면 Intel

<br>

> Rosetta 2 설치 (Apple Silicon Mac의 경우)
```
softwareupdate --install-rosetta --agree-to-license
```

<br>

> temurin@8 설치
```
brew install --cask temurin@8
```

<br>

> 설치 확인
```
/usr/libexec/java_home -V
```

|brew|
|-|
|![image](./img/26.png)|

<br>

> JAVA_HOME 환경 변수 설정
```
export JAVA_HOME=$(/usr/libexec/java_home -v 1.8)
```

<br>

#### 💡 홈브류 기본 명령어
> 홈브류
```
brew update - brew 업데이트
brew search <패키지 이름> - 해당 패키지 검색
brew install <패키지 이름> - 해당 패키지 설치
```

<br>

> 확인
```
brew list - 설치 된 패키지 리스트 확인
brew info <패키지 이름> - 해당 패키지 상세 정보 확인
```

<br>
 
> 업그레이드 (업데이트)
```
brew outdated - 업데이트가 필요한 패키지 찾아보기
brew upgrade - 패키지 전체 업데이트
brew upgrade <패키지 이름> - 해당 패키지 업데이트
```

<br>

> 삭제
```
brew cleanup <패키지 이름> - 여러 개의 버전이 있을 때, 가장 최신 버전만 살리고 나머지는 삭제
brew uninstall <패키지 이름> - 해당 패키지 삭제
```

>> 홈브류 완전 삭제
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall.sh"
```

<br>

---

<Br>

이클립스 설치 - 4.35
---
### 1. [이클립스](https://www.eclipse.org/downloads/packages/) 접속하여 파일 다운로드 및 설치
|Eclipse IDE for Enterprise Java and Web Developers|
|-|
|![image](./img/15.png)|
|![image](./img/16.png)|
|![image](./img/17.png)|
|![image](./img/18.png)|
|![image](./img/19.png)|

<Br>

### 2. 바탕화면에 생긴 Eclipse 을 없애기
> 마우스우클릭 → 'Eclipse' 추출 클릭하여 추출

|Eclipse IDE for Enterprise Java and Web Developers|
|-|
|![image](./img/20.png)|

<br>

---

<br>

전자정부프레임워크 - 
---
