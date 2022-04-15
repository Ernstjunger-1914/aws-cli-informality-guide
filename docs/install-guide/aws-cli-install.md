## AWS CLI 설치
이 문서의 가이드는 CLI 방식으로 엑세스 AWS에 엑세스가 가능한 IAM 계정이 존재한다는 것을 전재로 작성했다.   
CLI 방식으로 AWS에 엑세스할 수 있는 계정이 없다면 [이 문서](https://github.com/Ernstjunger-1914/aws-cli-informality-guide/blob/docs/docs/install-guide/create-iam-account.md)를 참고바란다.   

### Windows에 설치
OS는 Windows 10으로 하여 작업했으니 Windows 11과는 다소 차이가 있을 수 있다.   
우선 [이 페이지](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html#cliv2-windows-install)에서 AWS CLI2 설치파일을 다운받는다.   

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
