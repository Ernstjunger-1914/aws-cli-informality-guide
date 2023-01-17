## AWS CLI 설치
이 문서의 가이드는 CLI 방식으로 엑세스 AWS에 엑세스가 가능한 IAM 계정이 존재한다는 전제 하에 작성했다.   
CLI 방식으로 AWS에 엑세스할 수 있는 계정이 없다면 [이 문서](https://github.com/lock-user/aws-cli-informality-guide/blob/main/docs/install-guide/create-iam-account.md)를 참고바란다.   

### Windows에 설치
OS는 Windows 10으로 하여 작업했으니 Windows 11과는 다소 차이가 있을 수 있다.   
우선 [이 페이지](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html#cliv2-windows-install)에서 AWS CLI2 설치파일을 다운받는다.   
   
<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-awscli2-windows_1.png"><br />
    그림 1. 설치파일 실행
</p>

설치파일을 실행시키면 **그림 1**과 같은 화면이 나타난다.   
Next를 눌러 다음으로 넘어간다.  

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-awscli2-windows_2.png"><br />
    그림 2. 약관 동의
</p>

약관에 동의 후, 다음으로 넘어간다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-awscli2-windows_3.png"><br />
    그림 3. 경로 지정
</p>

AWS CLI가 설치되는 경로를 지정할 수 있는 항목이다.   
특별히 경로를 변경하고 싶다면 변경해주고 다음으로 넘어간다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-awscli2-windows_4.png"><br />
    그림 4. 설치
</p>

마지막으로 설치를 눌러주면 AWS CLI의 설치가 시작된다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-awscli2-windows_5.png"><br />
    그림 5. 설치 완료
</p>

설치가 완료되면 **그림 5**와 같이 설치 파일을 종료할 수 있다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-awscli2-windows_6.png"><br />
    그림 6. 버전 확인
</p>

AWS CLI가 정상적으로 설치되었는지 확인하기 위해 Command Prompt나 Power Shell을 키고 명령어 `aws --version` 를 입력하여 AWS CLI의 버전을 확인한다.   
정상적으로 설치가 되었다면 **그림 6**과 같이 버전에 관한 정보를 확인할 수 있다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-awscli2-windows_7.png"><br />
    그림 7. configure
</p>

AWS CLI를 사용하기 위해 명령어 `aws configure`를 입력하여 엑세스 키의 ID와 비밀 엑세스 키를 붙여넣고 작업할 리전과 출력 형식을 입력해준다.   
출력 형식은 json, table, text, yaml, yaml-stream이 있다.   
그 후, 아래의 명령어로 AWS CLI로 현재 계정에서 EC2로 접근 가능한 리전을 확인한다.   
명령어가 **그림 7**과 같이 결과를 잘 뱉으면 현재 계정으로 AWS CLI를 다룰 수 있다는 의미이다.   
```
aws ec2 describe-regions
```

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-awscli2-windows_8.png"><br />
    그림 8. configure edit
</p>

설정을 변경하고 싶다면 명령어 `aws configure`를 입력하여 설정을 변경하거나 **그림 8**과 같이 홈 디렉토리에 .aws 디렉토리에서 config 파일과 credentials 파일을 만져서 설정을 변경할 수도 있다.   
이렇게 Windows 환경에서 AWS CLI를 사용할 준비가 끝났다.   
   

### Linux에 설치
OS는 Ubuntu로 하였으니 Debian 계열 외의 리눅스 OS에선 다소 차이가 있을 수 있다.   
또한 순수 리눅스 환경에서 작업한 것이 아닌 WSL에서 작업을 진행했다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-awscli2-linux_1.png"><br />
    그림 1. awscli 압축 파일 download
</p>

아래의 명령어로 AWS CLI 압축 파일을 다운받는다.   
그 후, 압축 해제 명령어를 통해 다운받은 압축 파일의 압축을 해제한다.   
압축 해제 명령어가 없다면 설치를 받아야 한다.   

```sh
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
$ unzip awscliv2.zip
```
   
<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-awscli2-linux_2.png"><br />
    그림 2. 권한 부여 및 심볼 링크 생성
</p>

아래의 명령어를 통해 설치 프로그램을 실행하는 동시에 권한을 부여한다.   
그럼 기본적으로 설치는 `/usr/local/aws-cli`에 되며 `/usr/local/bin`에 심볼 링크가 생성된다.   
설치 프로그램을 실행 후, 실행한 디렉토리를 -i 옵션으로 복사할 디렉토리와 -b 옵션으로 심볼릭 링크로 연결해준다.   
다음 명령어는 AWS CLI를 업데이트하는 명령어인데, 기존 심볼 링크 및 설치 관리자 정보를 추가하여 `--update` 파라미터를 포함한 `install` 명령을 구성한다.   
마지막으로 AWS CLI 버전을 확인했을 때 **그림 2**와 같이 버전 정보가 확인된다면 정상적인 설치가 완료된 것이다.   

```sh
$ sudo ./aws/install
$ sudo ./aws/install --bin-dir /usr/local/bin --install-dir /usr/local/aws-cli --update
$ ls -l /usr/local/bin/aws
$ aws --version
```

### macOS에 설치
<<작성 예정>>


## 이 외에 AWS CLI를 다루는 방법
이번 항목에서는 위에서 소개했던 방식 이외에 AWS CLI를 다루는 방식들을 소개한다.   

### CloudShell

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/aws-cloud-shell.png"><br />
    그림 1. Cloud Shell
</p>

CloudShell은 웹브라우저로 AWS 콘솔에 접근하여 직접 사용할 수 있다.
다만, 현재(2022. 04. 15 기준)는 버지니아 북부, 오레곤, 아일랜드, 도쿄 등 몇몇 리전에서만 사용이 가능한 서비스이다.   
CloudShell은 AWS CLI2가 세팅되어 있는 상태라 별 다른 설정 없이 AWS CLI를 다룰 수 있으며 Python과 Node 런타임, Bash, PowerShell, git, ECS CLI, jq, npm, pip 등이 포함되어 있으며 향후 더 많은 기능이 제공될 예정이다.   
   
이 외에 CloudShell에 대해서는 아래와 같이 간단히 정리해두었다.   
> 스토리지 : `$HOME`에 저장된 파일은 Cloud Shell 호출 간에도 유지되지만 그 이외에 설치한 SW는 유지되지 않으며 용량은 리전당 1G로 제한된다.   
>    
> 요금 : 리전 당 최대 10개의 Shell을 동시에 사용했을 때 무료로 사용이 가능하며 Cloud Shell에서 AWS CLI로 작업을 하여도 Cloud Shell은 과금이 되지 않는다.  
>    
> 시간 초과 및 지속성 : 20분 동안 사용하지 않으면 세션이 만료된다.    
>    
> 네트워크 엑세스 : 세션은 인터넷 아웃바운드 연결을 생성이 가능하지만, 인바운드 연결은 불가능하며 세션은 private VPC 서브넷 내의 리소스에 접근할 수 없지만 이 기능은 단기 로드맵에 존재한다.   
   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/cloud-shell_1.png"><br />
    그림 2. AWS Console
</p>

Cloud Shell을 사용하는 방법은 매우 간단하다.   
우선 AWS Console에 로그인 후, Cloud Shell의 사용을 지원하는 리전에서 **그림 2**와 같이 우측 상단에 존재한다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/cloud-shell_2.png"><br />
    그림 3. AWS Cloud Shell
</p>

Cloud Shell는 AWS CLI가 기본으로 깔려있기 때문에 따로 세팅해줄 것은 거의 없다고 보면 된다.   
입문자 중에 local에 AWS CLI 환경 세팅을 하기 어려워 하는 사람들이 쓰면 좋을거 같다.   
필자는 AWS Console에서 작업 중이라 터미널을 키기 귀찮을 때 가끔 사용한다.   

### AWS Shell

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/aws-shell.png"><br />
    그림 1. AWS Shell
</p>

AWS Shell은 AWS CLI 셸 프로그램으로 AWS CLI를 사용하는 사용자에게 도움되는 자동 완성, OS Shell 명령 실행, 실행한 명령의 결과를 text 편집기로 내보내기 등 편리한 기능이 탑재되어 있다.   
AWS CLI만을 사용하면 간혹 옵션이 헷갈리거나 기억나지 않는 경우가 있는데 AWS Shell을 사용하면 이러한 경우를 대폭 줄일 수 있다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-aws-shell_1.png"><br />
    그림 2. install pip
</p>

설치 과정을 설명하기 앞서 필자는 WSL 환경에서 작업을 진행하였으나 아나콘다 IDE에서도 [AWS Shell을 지원](https://anaconda.org/conda-forge/aws-shell)하고 있다.   
각자 편한 방식으로 AWS Shell을 설치하여 사용해도 큰 문제는 없다.   
   
AWS Shell을 설치하기 위해서는 python과 pip가 필요한데 pip가 없는 사람은 설치를 해준다.   
python이 없으면 마찬가지로 python을 설치해준다.   
이미 설치되어 있는 사람들은 이곳을 무시하고 다음으로 넘어가면 된다.   
```sh
$ sudo apt install python3-pip -y
```

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-aws-shell_2.png"><br />
    그림 3. aws-shell install
</p>

pip를 통해 AWS Shell을 설치해준다.   
```sh
$ sudo pip install aws-shell
```

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-aws-shell_3.png"><br />
    그림 4. aws-shell 실행
</p>

설치가 완료되면 AWS Shell을 실행시켜준다.   
실행하는 명령어는 `aws-shell`이다.   
보통 터미널에서 AWS CLI를 사용하면 앞에 무조건 aws를 붙여야 하는데 AWS Shell에서는 앞에 aws를 붙일 필요가 없다.   
즉 AWS Shell에서는 `<command> <subcommand> <옵션이나 파라미터>`과 같이 명령어를 작성할 수 있다.   
또한 자동 완성 기능 또한 편리하기에 유용하다.   
필자는 명령어가 정상적으로 동작하는지 확인하기 위해 명령어 하나를 실행시켜 보았다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-aws-shell_4.png"><br />
    그림 5. 명령어 동작 확인
</p>

명령어는 잘 동작한다.   
필자는 이미 계정 정보를 설정해두어서 잘 동작하는 것이다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/download-aws-shell_5.png"><br />
    그림 6. aws-shell configure
</p>

계정 정보의 설정을 하지 않고 AWS Shell만 설치한 사람은 **그림 6**과 같이 AWS Shell 내에서 명령어 `configure`를 통해 설정이 가능하다.   
AWS Shell에서 나가려면 `F10`을 누르면 나갈 수 있다.   
