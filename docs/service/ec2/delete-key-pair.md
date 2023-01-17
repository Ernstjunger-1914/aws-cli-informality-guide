## delete-key-pair

### 설명
EC2에서 키 페어를 제거하는 명령어이다.   
   
### SubCommand
```bash
aws ec2 delete-key-pair --key-name <string>
[--key-pair-id <string>]
[--dry-run | --no-dry-run]
[--cli-input-json <string>]
[--generate-cli-skeleton <string>]
```

`--key-name`   
> 제거할 키 페어의 이름을 지정하는 subcommand이다.   

`--key-pair-id`   
> 키 페어의 id를 지정하는 subcommand이다.   

`--dry-run` | `--no-dry-run`   
> 실제로 요청을 보내지는 않고 작업에 필요한 권한이 있는지 확인하고 에러 응답을 제공한다.   
> 필요한 권한이 있을 경우의 응답은 `DryRunOperation`, 그렇지 않는 경우의 응답은 `UnauthorizedOperation`이다.   

`--cli-input-json`   
> 제공된 json 데이터를 기반으로 서비스 작업을 수행한다.   
> json 데이터는 `--generate-cli-skeleton` subcommand에서 제공하는 형태를 따르며 CLI에 다른 인수가 제공된 경우 CLI 값이 json에서 제공한 값을 재정의한다.   
> `file://` 접두사를 통해 사전에 작성된 파일을 파라미터로 전달하여 명령을 실행한다.   

`--generate-cli-skeleton`   
> 해당 subcommand를 사용하면 명령이 실행되지 않지만, 이후 명령에 입력으로 사용할 수 있는 파라미터 템플릿을 생성 및 표시할 수 있다.   
> 사용 가능한 값은 `input`, `yaml-input`, `output`이며 기본값은 input이다.  

### 사용 예제

#### 키 페어 제거
키 페어를 제거하는 방법은 다양하다.   
우선, 키 페어 이름을 통해 키 페어를 제거하는 명령어이다.   
키 페어가 정상적으로 제거가 되면 `create-key-pair`와 다르게 아무 응답이 없다.   
```bash
$ aws ec2 delete-key-pair --key-name <키 페어 이름>
```

키 페어 id로 키 페어를 제거하는 명령어이다.   
키 페어 id는 AWS 콘솔 혹은 AWS CLI로 키 페어를 생성했을 때 출력되는 정보를 통해 확인이 가능하다.   
```bash
$ aws ec2 delete-key-pair --key-pair-id <키 페어 id>
```

이번에는 json 파일을 통해 키 페어를 제거하는 과정이다.   
우선 json 파일을 생성해주어야 하는데 json 파일의 형식은 AWS CLI로 키 페어를 생성했을 때 출력되는 형식에 맞추면 된다.   
```json
{
    "KeyName": "<키 페어 이름>"
}
```

그리고 아래의 명령어를 통해 키 페어를 제거할 수 있다.   
여기서 json 파일이 현재 작업 중인 경로에 존재해야 아래의 명령어를 통해 키 페어를 제거할 수 있다.   
```bash
$ aws ec2 delete-key-pair --cli-input-json file://<json 파일 이름>
```

