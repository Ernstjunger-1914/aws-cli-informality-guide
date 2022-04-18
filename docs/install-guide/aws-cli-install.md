## AWS CLI 설치
이 문서의 가이드는 CLI 방식으로 엑세스 AWS에 엑세스가 가능한 IAM 계정이 존재한다는 것을 전재로 작성했다.   
CLI 방식으로 AWS에 엑세스할 수 있는 계정이 없다면 [이 문서](https://github.com/Ernstjunger-1914/aws-cli-informality-guide/blob/docs/docs/install-guide/create-iam-account.md)를 참고바란다.   

### Windows에 설치
OS는 Windows 10으로 하여 작업했으니 Windows 11과는 다소 차이가 있을 수 있다.   
우선 [이 페이지](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html#cliv2-windows-install)에서 AWS CLI2 설치파일을 다운받는다.   
   
<p align="center" width="100%">
    <br /><br /><img src="https://github.com/Ernstjunger-1914/aws-cli-informality-guide/blob/docs/image/install/download-awscli2-windows_1.png"><br />
    그림 1. 설치파일 실행
</p>

설치파일을 실행시키면 **그림 1**과 같은 화면이 나타난다.   
Next를 눌러 다음으로 넘어간다.  

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/Ernstjunger-1914/aws-cli-informality-guide/blob/docs/image/install/download-awscli2-windows_2.png"><br />
    그림 2. 약관 동의
</p>

약관에 동의 후, 다음으로 넘어간다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/Ernstjunger-1914/aws-cli-informality-guide/blob/docs/image/install/download-awscli2-windows_3.png"><br />
    그림 3. 경로 지정
</p>

AWS CLI가 설치되는 경로를 지정할 수 있는 항목이다.   
특별히 경로를 변경하고 싶다면 변경해주고 다음으로 넘어간다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/Ernstjunger-1914/aws-cli-informality-guide/blob/docs/image/install/download-awscli2-windows_4.png"><br />
    그림 4. 설치
</p>

마지막으로 설치를 눌러주면 AWS CLI의 설치가 시작된다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/Ernstjunger-1914/aws-cli-informality-guide/blob/docs/image/install/download-awscli2-windows_5.png"><br />
    그림 5. 설치 완료
</p>

설치가 완료되면 **그림 5**와 같이 설치 파일을 종료할 수 있다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/Ernstjunger-1914/aws-cli-informality-guide/blob/docs/image/install/download-awscli2-windows_6.png"><br />
    그림 6. 버전 확인
</p>

AWS CLI가 정상적으로 설치되었는지 확인하기 위해 Command Prompt나 Power Shell을 키고 명령어 `aws --version` 를 입력하여 AWS CLI의 버전을 확인한다.   
정상적으로 설치가 되었다면 **그림 6**과 같이 버전에 관한 정보를 확인할 수 있다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/Ernstjunger-1914/aws-cli-informality-guide/blob/docs/image/install/download-awscli2-windows_7.png"><br />
    그림 7. configure
</p>

AWS CLI를 사용하기 위해 명령어 `aws configure`를 입력하여 엑세스 키의 ID와 비밀 엑세스 키를 붙여넣고 작업할 리전과 출력 형식을 입력해준다.   
출력 형식은 json, table, text, yaml, yaml-stream이 있다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/Ernstjunger-1914/aws-cli-informality-guide/blob/docs/image/install/download-awscli2-windows_8.png"><br />
    그림 8. configure edit
</p>

설정을 변경하고 싶다면 명령어 `aws configure`를 입력하여 설정을 변경하거나 **그림 8**과 같이 홈 디렉토리에 .aws 디렉토리에서 config 파일과 credentials 파일을 만져서 설정을 변경할 수도 있다.   
이렇게 Windows 환경에서 AWS CLI를 사용할 준비가 끝났다.

### Linux에 설치
OS는 Ubuntu로 하였으니 Debian 계열 외의 리눅스 OS에선 다소 차이가 있을 수 있다.   

```sh
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
$ unzip awscliv2.zip
```

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
CloudShell은 웹브라우저로 AWS 콘솔에 접근하여 직접 사용할 수 있다.   
다만, 현재(2022. 04. 15 기준)는 버지니아 북부, 오레곤, 아일랜드, 도쿄 등 몇몇 리전에서만 사용이 가능한 서비스이다.   
CloudShell은 AWS CLI2가 세팅되어 있는 상태라 별 다른 설정 없이 AWS CLI를 다룰 수 있다.   
이 외에도 Python과 Node 런타임, Bash, PowerShell, git, ECS CLI, jq, npm, pip 등이 포함되어 있으며 향후 더 많은 기능이 제공될 예정이다.   
