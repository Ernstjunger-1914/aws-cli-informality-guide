## create-default-vpc

### 설명
특정 리전 내에 기본 vpc를 생성하는 명령어이다.   
기본 vpc의 구성은 사용자가 지정할 수 없으며 기본 vpc의 구성에 대해서는 [이 문서](https://docs.aws.amazon.com/ko_kr/vpc/latest/userguide/default-vpc.html)를 참고하면 된다.   

### SubCommand
```bash
aws ec2 create-default-vpc
[--dry-run | --no-dry-run]
[--cli-input-json <string>]
[--generate-cli-skeleton <string>]
```

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

#### 기본 VPC 생성

기본 vpc를 생성하는 명령어는 아래와 같다.   
subcommand는 `SubCommand` 항목에서 소개한 3개의 subcommand 외에 global option도 사용이 가능하지만 굳이 붙일 필요는 없다.
```bash
$ aws ec2 create-default-vpc
```

기본 vpc가 정상적으로 생성되면 아래와 같이 vpc 정보가 출력된다.
```json
{
    "Vpc": {
        "CidrBlock": "172.31.0.0/16",
        "DhcpOptionsId": "<dhcp 옵션 id>",
        "State": "pending",
        "VpcId": "<vpc id>",
        "OwnerId": "<소유자 id>",
        "InstanceTenancy": "default",
        "Ipv6CidrBlockAssociationSet": [],
        "CidrBlockAssociationSet": [
            {
                "AssociationId": "<vpc cidr association id>",
                "CidrBlock": "172.31.0.0/16",
                "CidrBlockState": {
                    "State": "associated"
                }
            }
        ],
        "IsDefault": true,
        "Tags": []
    }
}
```

리전 내에 기본 vpc가 존재할 경우, 아래와 같이 출력된다.
```text
An error occurred (DefaultVpcAlreadyExists) when calling the CreateDefaultVpc operation: A Default VPC already exists for this account in this region.
```