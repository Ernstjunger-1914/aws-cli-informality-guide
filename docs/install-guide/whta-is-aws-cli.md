## AWS CLI란 무엇인가
<p align="center" width="100%">
   <img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/aws-cli.png">
</p>
   
AWS CLI는 CLI Shell 명령어를 사용하여 AWS 서비스를 관리할 수 있는 [오픈소스](https://github.com/aws/aws-cli) 도구이다.
AWS CLI를 통해 터미널에서 브라우저로 AWS 콘솔에서 작업하는 것과 동일하게 기능을 구현할 수 있다.   
또한, AWS CLI를 다루는 것이 능숙해진다면 AWS 서비스의 Public API에 엑세스가 가능하며 리소스를 관리하거나 기능을 구현하는 Shell Script를 작성하여 작업을 자동화할 수 있다.   

AWS CLI의 명령 구조는 아래와 같다.
```bash
$ aws <command> <subcommand> <옵션이나 파라미터>
```

CLI에서 도움말 설명서를 보려면 아래의 명령어 중 하나를 입력하면 된다.   
각각 AWS CLI, AWS CLI 명령어, AWS CLI 하위 명령어에 대한 도움말 설명서이다.
```bash
$ aws help
$ aws <command> help
$ aws <command> <subcommand> help
```

명령어에 대한 디버깅을 하고 싶으면 명령어를 아래와 같은 형식으로 작성한다.
```bash
$ aws --debug <command> <subcommand> <옵션이나 파라미터>
```