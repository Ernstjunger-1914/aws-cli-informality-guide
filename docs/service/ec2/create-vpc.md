## create-vpc

### 설명
지정된 IPv4 cidr 블록을 사용하여 vpc를 생성하는 명령어이다.   

### SubCommand
```bash
aws ec2 create-vpc
[--cidr-block <string>]
[--amazon-provided-ipv6-cidr-block | --no-amazon-provided-ipv6-cidr-block]
[--ipv6-pool <string>]
[--ipv6-cidr-block <string>]
[--ipv4-ipam-pool-id <string>]
[--ipv4-netmask-length <integer>]
[--ipv6-ipam-pool-id <string>]
[--ipv6-netmask-length <integer>]
[--dry-run | --no-dry-run]
[--instance-tenancy <string>]
[--ipv6-cidr-block-network-border-group <string>]
[--tag-specifications <list>]
[--cli-input-json <string>]
[--generate-cli-skeleton <string>]
```

`--cidr-block`
> vpc에 대한 IPv4 네트워크 범위(cidr 표기법)

`--amazon-provided-ipv6-cidr-block` | `--no-amazon-provided-ipv6-cidr-block`
> vpc의 접두어 길이가 /56인 IPv6 cidr  블록을 요청한다.
> IP 주소의 범위나 cidr 블록의 크기는 지정할 수 없다.

`--ipv6-pool`
> IPv6 cidr 블록을 할당할 IPv6 wnth pool의 id

`--ipv6-cidr-block`
> IPv6 주소 pool의 IPv6 cidr 블록이다.   
> IPv6Pool을 지정할 수 있지만 aws에서 IPv6 cidr 블록을 지정하도록 하려면 해당 subcommand는 사용하면 안된다.

`--ipv4-ipam-pool-id`
> vpc의 cidr를 할당하는데 사용할 IPv4 IPAM pool의 id   
> IPAM에 대한 자세한 내용은 [이 페이지](https://docs.aws.amazon.com/ko_kr/vpc/latest/ipam/what-it-is-ipam.html) 참고

`--ipv4-netmask-length`
> vpc ipam pool에서 vpc에 할당할 IPv4 cidr의 netmask 길이

`--ipv6-ipam-pool-id`
> vpc와 IPv6 cidr를 할당하는데 사용할 IPv6 ipam pool의 id

`--ipv6-netmask-length`
> vpc ipam pool에서 vpc에 할당할 IPv6 cidr의 netmask 길이

`--dry-run` | `--no-dry-run`   
> 실제로 요청을 보내지는 않고 작업에 필요한 권한이 있는지 확인하고 에러 응답을 제공한다.   
> 필요한 권한이 있을 경우의 응답은 `DryRunOperation`, 그렇지 않는 경우의 응답은 `UnauthorizedOperation`이다.   

`--instance-tenancy`
> vpc로 시작된 인스턴스의 테넌트 옵션   
> 기본적으로 인스턴스는 공유 테넌트로 실행되며 모든 테넌트가 포함된 인스턴스를 공유 테넌시 vpc로 시작할 수 있다.
> 사용 가능한 값은 `default`, `dedicated`, `host`이며 기본 값은 default이다.

`--ipv6-cidr-block-network-border-group`
> IPv6 cidr 블록을 지원하는 location의 이름   
> 주소를 이 location으로 제한하려면 해당 subcommand를 사용하면 된다.

`--tag-specifications`
> vpc에 할당할 태그

`--cli-input-json`   
> 제공된 json 데이터를 기반으로 서비스 작업을 수행한다.   
> json 데이터는 `--generate-cli-skeleton` subcommand에서 제공하는 형태를 따르며 CLI에 다른 인수가 제공된 경우 CLI 값이 json에서 제공한 값을 재정의한다.   
> `file://` 접두사를 통해 사전에 작성된 파일을 파라미터로 전달하여 명령을 실행한다.   

`--generate-cli-skeleton`   
> 해당 subcommand를 사용하면 명령이 실행되지 않지만, 이후 명령에 입력으로 사용할 수 있는 파라미터 템플릿을 생성 및 표시할 수 있다.   
> 사용 가능한 값은 `input`, `yaml-input`, `output`이며 기본값은 input이다.  

### 사용 예제

#### VPC 생성

아래의 명령어는 IPv4 cidr와 태그를 사용하여 vpc를 생성하는 명령어이다.
```bash
$ aws ec2 create-vpc \
    --cidr-block 10.0.0.0/18 \
    --tag-specification "ResourceType=vpc,Tags=[{Key=<tag key>,Value=<tag value>},{Key=<tag key>,Value=<tag value>}]"
```

vpc가 정상적으로 생성되면 아래와 같이 vpc 정보가 출력된다.
```json
{
    "Vpc": {
        "CidrBlock": "10.0.0.0/18",
        "DhcpOptionsId": "<dhcp 옵션 id>",
        "State": "pending",
        "VpcId": "<vpc id>",
        "OwnerId": "<소유자 id>",
        "InstanceTenancy": "default",
        "Ipv6CidrBlockAssociationSet": [],
        "CidrBlockAssociationSet": [
            {
                "AssociationId": "<vpc cidr association id>",
                "CidrBlock": "10.0.0.0/18",
                "CidrBlockState": {
                    "State": "associated"
                }
            }
        ],
        "IsDefault": false,
        "Tags": [
            {
                "Key": "<tag key>",
                "Value": "<tag value>"
            },
            {
                "Key": "<tag key>",
                "Value": "<tag value>"
            }
        ]
    }
}
```

아래의 명령어는 전용 테넌트를 사용하여 vpc를 생성하는 명령어이다.
```bash
$ aws ec2 create-vpc \
    --cidr-block 10.0.0.0/18 \
    --instance-tenancy dedicated \
    --tag-specification "ResourceType=vpc,Tags=[{Key=<tag key>,Value=<tag value>}]"
```

vpc가 정상적으로 생성되면 아래와 같이 vpc 정보가 출력되는데 이때 InstanceTenancy가 명령어에서 지정한 dedicated로 나타나는 것을 확인할 수 있다.
```json
{
    "Vpc": {
        "CidrBlock": "10.0.0.0/18",
        "DhcpOptionsId": "<dhcp 옵션 id>",
        "State": "pending",
        "VpcId": "<vpc id>",
        "OwnerId": "<소유자 id>",
        "InstanceTenancy": "dedicated",
        "Ipv6CidrBlockAssociationSet": [],
        "CidrBlockAssociationSet": [
            {
                "AssociationId": "<vpc cidr association id>",
                "CidrBlock": "10.0.0.0/18",
                "CidrBlockState": {
                    "State": "associated"
                }
            }
        ],
        "IsDefault": false,
        "Tags": [
            {
                "Key": "<tag key>",
                "Value": "<tag value>"
            }
        ]
    }
}
```

아래의 명령어는 IPv6 cidr 블록을 사용해 vpc를 생성하는 명령어이다.
```bash
$ aws ec2 create-vpc \
    --cidr-block 10.0.0.0/18 \
    --amazon-provided-ipv6-cidr-block
```

정상적으로 생성됐을 시, 아래와 같이 출력이 된다.   
여기서 일반적으로 생성했을 때는 `Ipv6CidrBlockAssociationSet` key의 value가 비어있었지만 IPv6 cidr 블록을 사용해서 생성했을 땐 value 값에 내용이 있는 것을 확인할 수 있다.
```json
{
    "Vpc": {
        "CidrBlock": "10.0.0.0/18",
        "DhcpOptionsId": "<dhcp 옵션 id>",
        "State": "pending",
        "VpcId": "<vpc id>",
        "OwnerId": "<소유자 id>",
        "InstanceTenancy": "default",
        "Ipv6CidrBlockAssociationSet": [
            {
                "AssociationId": "<ipv6 vpc cidr association id>",
                "Ipv6CidrBlock": "",
                "Ipv6CidrBlockState": {
                    "State": "associating"
                },
                "NetworkBorderGroup": "<리전>",
                "Ipv6Pool": "Amazon"
            }
        ],
        "CidrBlockAssociationSet": [
            {
                "AssociationId": "<vpc cidr association id>",
                "CidrBlock": "10.0.0.0/18",
                "CidrBlockState": {
                    "State": "associated"
                }
            }
        ],
        "IsDefault": false
    }
}
```

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/ec2/vpc-ipv6-cidr.png"><br />
    그림 1. VPC IPv6 CIDR
</p>

IPv6 cidr 블록을 통해 vpc를 생성하면 `그림 1`과 같이 AWS 콘솔에서 vpc 상세 정보에 cidr에 IPv6가 있는 것을 확인할 수 있다.

***

vpc를 생성할 때 ipam pool에서 cidr를 사용하여 생성할 수 있다.
명령어 형식은 아래와 같다.
```bash
$ aws ec2 create-vpc --ipv4-ipam-pool-id <ipam pool id>
```

vpc가 정상적으로 생성되었을 때의 출력은 아래와 같다.
```json
{
    "Vpc": {
        "CidrBlock": "10.0.1.0/24",
        "DhcpOptionsId": "<dhcp 옵션 id>",
        "State": "pending",
        "VpcId": "<vpc id>",
        "OwnerId": "<소유자 id>",
        "InstanceTenancy": "default",
        "Ipv6CidrBlockAssociationSet": [],
        "CidrBlockAssociationSet": [
            {
                "AssociationId": "<vpc cidr association id>",
                "CidrBlock": "10.0.1.0/24",
                "CidrBlockState": {
                    "State": "associated"
                }
            }
        ],
        "IsDefault": false
    }
}
```