## create-key-pair

### 설명
키 페어는 지정된 이름과 pem이나 ppk format 형식으로 ed25519나 2048비트의 rsa로 생성되며 공개 키는 AWS EC2에 저장되고 개인 키는 키 파일에 저장된다.   
키 페어를 생성할 때 이름이 중복된다면 키 페어가 생성되지 않는다.   
   
키 페어는 해당 키 페어를 생성한 리전에서만 사용이 가능하며 직접 키 페어를 만들어 키 페어 가져오기를 통해 해당 키 페어를 모든 리전에 업로드하여 사용할 수 있다.   
   
키 페어는 리전 당 최대 5,000개까지 생성할 수 있다.   

### SubCommand
```bash
aws ec2 create-key-pair --key-name <string>
[--dry-run | --no-dry-run]
[--key-type <string>]
[--tag-specifications <list>]
[--key-format <string>]
[--cli-input-json <string>]
[--generate-cli-skeleton <string>]
```

`--key-name`   
> 키 페어의 고유 이름을 지정하는 subcommand이다.   
> 키 이름은 최대 255자의 ASCII 문자로 지정이 가능하다.  

`--dry-run` | `--no-dry-run`   
> 실제로 요청을 보내지는 않고 작업에 필요한 권한이 있는지 확인하고 에러 응답을 제공한다.   
> 필요한 권한이 있을 경우의 응답은 `DryRunOperation`, 그렇지 않는 경우의 응답은 `UnauthorizedOperation`이다.   

`--key-type`   
> 키 페어 타입을 지정하는 subcommand이다.   
> 사용 가능한 값은 `rsa`와 `ed25519`이다.
> 기본값은 rsa이며 Windows OS의 인스턴스에서는 ED25519 키가 지원되지 않는다.   

`--tag-specifications`   
> 키 페어에 적용할 태그를 지정하는 subcommand이다.   

`--key-format`   
> 키 페어의 format 형식을 지정하는 subcommand이다.   
> 사용 가능한 값은 `pem`과 `ppk`이며 기본값은 pem이다.

`--cli-input-json`   
> 제공된 json 데이터를 기반으로 서비스 작업을 수행한다.   
> json 데이터는 `--generate-cli-skeleton` subcommand에서 제공하는 형태를 따르며 CLI에 다른 인수가 제공된 경우 CLI 값이 json에서 제공한 값을 재정의한다.   
> `file://` 접두사를 통해 사전에 작성된 파일을 파라미터로 전달하여 명령을 실행한다.   

`--generate-cli-skeleton`   
> 해당 subcommand를 사용하면 명령이 실행되지 않지만, 이후 명령에 입력으로 사용할 수 있는 파라미터 템플릿을 생성 및 표시할 수 있다.   
> 사용 가능한 값은 `input`, `yaml-input`, `output`이며 기본값은 input이다.   

### 사용 예제
#### 키 페어 생성
아래의 명령어는 키 페어를 생성하는 명령어이다.   
```bash
$ aws ec2 create-key-pair --key-name <키 페어 이름>
```

명령어가 정상적으로 실행되면 아래와 같이 개인 키, 키 지문, 키 이름과 id가 출력된다.   
```bash
{
    "KeyFingerprint": "aa:bb:cc...",
    "KeyMaterial": "-----BEGIN RSA PRIVATE KEY-----\n...\n-----END RSA PRIVATE KEY-----",
    "KeyName": "..",
    "KeyPairId": "key-0b..."
}
```

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/Ernstjunger-1914/aws-cli-informality-guide/blob/main/image/ec2/create-key-pair-console.png"><br />
    그림 1. 콘솔에서 키 페어 생성 확인
</p> 

AWS CLI를 통해 생성된 키 페어는 `그림 1`과 같이 AWS 콘솔에서도 키 페어가 실행된 것을 확인할 수 있다.   