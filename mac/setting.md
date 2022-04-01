# MacBook 초기 세팅

<br>

## home brew 설치

<img width="934" alt="image" src="https://user-images.githubusercontent.com/62639722/161256702-9d0fb63a-6449-4dbd-ab78-5e374754838d.png">


[home brew](https://brew.sh/index_ko) 접속하여 중앙에 링크 복사 후 터미널에 입력하여 설치

<br>

터미널에 `brew install cask` 입력하여 설치

<br>

`brew list` 입력하면 home brew 로 설치한 프로그램 확인 가능

<br>

## wget 설치

homebrew 를 이용하여 wget 을 설치한다.  
weget 은 url을 통해 프로그램을 설치할 수 있다.

```shell
brew install wget
```

## nvm 설치

<img width="849" alt="image" src="https://user-images.githubusercontent.com/62639722/161258779-275c8b9c-0e1b-4cb4-840a-22c8e473e1c2.png">


[nvm 공식문서](https://github.com/nvm-sh/nvm#install--update-script) 를 통해 node js 및 다양한 프로그램 설치를 위해 nvm 설치한다.(wget 으로 설치)

m1 맥북의 경우 다음의 과정이 필요하다.

* nvm 디렉터리 생성 <br> `mkdir ~/.nvm`
* vi편집기나 nano편집기를 이용해 ~/.zshrc 에 들어가서 아래내용 붙여넣기 <br>
```shell
export NVM_DIR="$HOME/.nvm"
[ -s "/usr/local/opt/nvm/nvm.sh" ] && . "/usr/local/opt/nvm/nvm.sh"  # This loads nvm
[ -s "/usr/local/opt/nvm/etc/bash_completion.d/nvm" ] && . "/usr/local/opt/nvm/etc/bash_completion.d/nvm"  # This loads nvm bash_completion
```

`nvm --version` 입력하여 nvm 버전 확인 가능

<br>

## node 설치

안정화 버전인 lts 설치

```shell
nvm install --lts
```

<br>

m1 맥북의 경우 15버전 이상으로 설치

```shell
nvm install 15
```

<br>

## vscode 설치

home brew 로 설치를 원하는 경우는 터미널에 아래 입력

```shell
brew install --cask visual-studio-code
```

<br>


[visualstudio 공식사이트](https://code.visualstudio.com) 에서도 설치 가능

<br>

터미널에 `code [path]` 입력하여 해당 경로에 vscode 를 바로 실행할 수 있는 명령어를 입력하고 싶은 경우에는. 
nano 편집기로 `~/.bash_profile` 를 아래와 같이 수정한다.

```shell
nano ~/.bash_profile
```

```shell
export PATH="\$PATH:/Applications/Visual Studio Code.app/C
```
