## describe-instances

### 설명
EC2 인스턴스를 조회할 수 있는 명령어이다.   
조회되는 인스턴스는 명령어에 붙인 조건에 따라 다르게 조회될 수 있다.   

### SubCommand
```bash
aws ec2 describe-instances
[--filters <list>]
[--instance-ids <list>]
[--dry-run | --no-dry-run]
[--cli-input-json <string>]
[--starting-token <string>]
[--page-size <integer>]
[--max-items <integer>]
[--generate-cli-skeleton <string>]
```

`--filters`   
> 사용 가능한 필터 옵션   
> - **affinity** Dedicated Host에서 실행되는 인스턴스의 선호도 설정(`default` | `host`)
> - **architecture** 조회할 인스턴스 아키텍처를 설정(`i386` | `x86_64` | `arm64`)
> - **availability-zone** 조회할 인스턴스의 가용 영역을 설정.   
> - **block-device-mapping.attach-time** 조회할 인스턴스에 매핑된 ebs 볼륨의 연결 시간을 설정.   
> 값은 아래와 같이 넣어준다.   
> `2022-12-15T17:15:20.000Z`   
> - **block-device-mapping.delete-on-termination** 인스턴스 종료 시 ebs 볼륨 제거 여부.   
> - **block-device-mapping.device-name** 인스턴스 블록 디바이스 매핑에 지정된 디바이스.   
> - **block-device-mapping.status** ebs 볼륨의 상태(`attaching` | `attached` | `detaching` | `detached`)   
> - **block-device-mapping.volume-id** ebs 볼륨 id   
> - **capacity-reservation-id** 인스턴스가 시작된 용량 예약의 id   
> - **client-token** 인스턴스를 시작할 때 제공한 id 권한 토큰   
> - **dns-name** 인스턴스의 public dns 이름   
> - **group-id** 인스턴스에 적용된 보안 그룹 id(ec2 클래식에만 해당)   
> - **group-name** 인스턴스에 적용된 보안 그룹 이름(ec2 클래식에만 해당)   
> - **hibernation-options.configured** 인스턴스의 최대 절전 모드 설정 여부.   
> - **host-id** 실행 중인 인스턴스의 전용 호스트 id   
> - **hypervisor** 인스턴스의 하이퍼바이저 유형(`ovm` | `xen`)
> - **iam-instance-profile.arn** 인스턴스에 연결된 프로필(arn으로 지정)
> - **image-id** 인스턴스를 시작할 때 사용된 이미지 id
> - **instance-id** 인스턴스 id
> - **instance-lifecycle** 스팟 인스턴스인지 예약된 인스턴스인지 나타낸다.(`spot` | `scheduled`)
> - **instance-state-code** 인스턴스의 상태 코드
> 자세한 건 아래의 표 참고   
> 
|상태|상태 코드|
|---|---|
|pending|0|
|running|16|
|shutting-down|32|
|terminated|48|
|stopping|64|
|stopped|80|
> - **instance-state-name** 인스턴스의 상태   
> 자세한 건 위의 표 참고
> - **instance-type** 인스턴스의 타입   
> 자세한 건 [이 페이지](https://aws.amazon.com/ko/ec2/instance-types/) 참고
> - **instance.group-id** 인스턴스에 적용된 보안 그룹의 id
> - **instance.group-name** 인스턴스에 적용된 보안 그룹의 이름
> - **ip-address** 인스턴스의 public IPv4
> - **kernel-id** 커널 id
> - **key-name** 인스턴스 키 페어의 이름
> - **launch-index** 여러 인스턴스를 시작할 때 index
> - **launch-time** 인스턴스가 시작된 시간(UTC 표준 시간 기준)   
> 형식은 `YYYY-MM-DDThh:mm:ss.sssZ`와 같이 작성한다.
> - **metadata-options.http-tokens** 메타데이터 request 권한 부여 여부(`optional` | `required`)
> - **metadata-options.http-put-response-hop-limit** http 메타데이터 request에서 put response hop 제한(1 ~ 64)
> - **metadata-options.http-endpoint** http 엔드포인트에서 메타데이터 엑세스 사용 여부(`enable` | `disable`)
> - **monitoring-state** 상세 모니터링 여부(`enable` | `disable`)
> - **network-interface.addresses.private-ip-address** 네트워크 인터페이스와 연결된 private IPv4
> - **network-interface.addresses.primary** 네트워크 인터페이스의 IPv4 주소가 기본 전용 여부
> - **network-interface.addresses.association.public-ip** 탄력적 IP 주소와 네트워크 인터페이스의 연결 id
> - **network-interface.addresses.association.ip-owner-id** 네트워크 인터페이스와 연결된 전용 IPv4 주소의 소유자 id
> - **network-interface.association.public-ip** 네트워크 인터페이스에 바인딩된 탄력적 IP 주소
> - **network-interface.association.ip-owner-id** 네트워크 인터페이스와 연결된 탄력적 ip 주소의 소유자
> - **network-interface.association.allocation-id** 네트워크 인터페이스에 탄력적 ip를 할당할 때 반환되는 할당 id
> - **network-interface.association.association-id** 네트워크 인터페이스가 IPv4 주소와 연결되었을 때 반환되는 연결 id
> - **network-interface.attachment.attachment-id** 인터페이스 연결 id
> - **network-interface.attachment.instance-id** 네트워크 인터페이스와 연결된 인스턴스의 id
> - **network-interface.attachment.instance-owner-id** 네트워크 인터페이스와 연결된 인스턴스의 소유자 id
> - **network-interface.attachment.device-index** 네트워크 인터페이스가 연결된 장치 index
> - **network-interface.attachment.status** 연결 상태(`attaching` | `attached` | `detaching` | `detached`)
> - **network-interface.attachment.attach-time** 네트워크 인터페이스와 인스턴스와 연결된 시간
> - **network-interface.attachment.delete-on-termination** 인스턴스가 종료될 때 연결 끊음 여부
> - **network-interface.availability-zone** 네트워크 인터페이스의 가용 영역
> - **network-interface.description** 네트워크 인터페이스 설명
> - **network-interface.group-id** 네트워크 인터페이스에 연결된 보안 그룹 id
> - **network-interface.group-name** 네트워크 인터페이스에 연결된 보안 그룹 이름
> - **network-interface.ipv6-addresses.ipv6-address** 네트워크 인터페이스와 연결된 IPv6 주소
> - **network-interface.mac-address** 네트워크 인터페이스의 mac 주소
> - **network-interface.network-interface-id** 네트워크 인터페이스 id
> - **network-interface.owner-id** 네트워크 인터페이스의 소유자 id
> - **network-interface.private-dns-name** 네트워크 인터페이스의 private dns 이름
> - **network-interface.requester-id** 네트워크 인터페이스의 요청자 id
> - **network-interface.requester-managed** 네트워크 인퍼페이스가 aws에서 관리되는지의 여부
> - **network-interface.status** 네트워크 인터페이스의 상태(`available` | `in-use`)
> - **network-interface.source-dest-check** 네트워크 인터페이스의 원본/대상 검사 수행 여부(`true` | `false`)
> - **network-interface.subnet-id** 네트워크 인터페이스의 서브넷 id
> - **network-interface.vpc-id** 네트워크 인터페이스의 vpc id
> - **outpost-arn** arn 출력
> - **owner-id** 인스턴스 소유자의 aws 계정 id
> - **placement-group-name** 인스턴스의 배치 그룹 이름
> - **placement-partition-number** 인스턴스의 파티션
> - **platform** 플랫폼
> - **private-dns-name** 인스턴스의 private IPv4 dns 이름
> - **private-ip-address** 인스턴스의 private IPv4
> - **product-code** 인스턴스를 시작할 때 사용된 ami의 제품 코드
> - **product-code.type** 제품 코드 유형(`devpay` | `marketplace`)
> - **ramdisk-id** 램디스트 id
> - **reason** 현재 인스턴스 상태에 대한 이유
> - **requester-id** 사용자를 대신해 인스턴스를 시작한 엔티티 id(ex. aws 관리 콘솔, auto scaling 등)
> - **reservation-id** 인스턴스 예약 id
> - **root-device-name** root 디바이스 볼륨의 디바이스 이름(ex. `/dev/sda1`)
> - **root-device-type** root 디바이스 볼륨의 유형(`ebs` | `instance-store`)
> - **source-dest-check** 인스턴스의 원본/대상 검사 수행 여부(`true` | `false`)
> - **spot-instance-request-id** 스팟 인스턴스 요청 id
> - **state-reason-code** 상태 변경 reason 코드
> - **state-reason-message** 상태 변경을 설명하는 메세지
> - **subnet-id** 인스턴스의 서브넷 id
> - **tag:key** 리소스에 할당된 태그의 key/value
> - **tag-key** 리소스에 할당된 태그 키.   
> 태그의 value에 관계 없이 특정 key를 가진 태그가 있는 모든 리소스를 조회할 수 있다.
> - **tenancy** 인스턴스의 tenancy(`dedicated` | `default` | `host`)
> - **virtualization-type** 인스턴스의 가상화 유형(`paravirtual` | `hvm`)
> - **vpc-id** 실행 중인 인스턴스의 vpc id

`--instance-ids`   
> 조회할 인스턴스 id를 지정하는 subcommand이다.   

`--dry-run` | `--no-dry-run`   
> 실제로 요청을 보내지는 않고 작업에 필요한 권한이 있는지 확인하고 에러 응답을 제공한다.   
> 필요한 권한이 있을 경우의 응답은 `DryRunOperation`, 그렇지 않는 경우의 응답은 `UnauthorizedOperation`이다.   

`--cli-input-json`   
> 제공된 json 데이터를 기반으로 서비스 작업을 수행한다.   
> json 데이터는 `--generate-cli-skeleton` subcommand에서 제공하는 형태를 따르며 CLI에 다른 인수가 제공된 경우 CLI 값이 json에서 제공한 값을 재정의한다.   
> `file://` 접두사를 통해 사전에 작성된 파일을 파라미터로 전달하여 명령을 실행한다.   

`--starting-token`   
> `--max-items`가 기본 API 호출에서 반환하는 전체 항목 수보다 적을 경우, 사용자가 다음 항목 세트를 검색하기 위해 후속 명령에 전달할 수 있도록 출력에 `NextToken`이 포함된다.   

`--page-size`   
> AWS CLI에서 각 AWS 서비스에 호출할 항목 수를 지정할 수 있는 subcommand이다.   
> 해당 subcommand를 통해 페이지 크기를 지정하면 AWS CLI는 전체 목록을 검색하지만, 백그라운드에서 많은 수의 서비스 API 호출을 수행하고 각 호출마다 더 적은 수의 항목을 검색하기 때문에 각각의 요청이 시간 초과 없이 호출에 성공할 확률이 증가한다.   

`--max-items`   
> 사용자가 지정한 항목 수만 출력되도록 지정할 수 있는 subcommand이다.   
> 조회 가능한 총 항목 수가 지정된 값을 초과한다면 명령 출력에 `NextToken`이 제공된다.   
> 페이지 분할을 하기 위해서는 `--starting-token`에 `NextToken` 값을 입력하면 된다.   

`--generate-cli-skeleton`   
> 해당 subcommand를 사용하면 명령이 실행되지 않지만, 이후 명령에 입력으로 사용할 수 있는 파라미터 템플릿을 생성 및 표시할 수 있다.   
> 사용 가능한 값은 `input`, `yaml-input`, `output`이며 기본값은 input이다.  

### 사용 예제

#### 인스턴스 조회
***
조회할 인스턴스에 아무 제한을 두지 않은 명령어이다.    
```bash
$ aws ec2 describe-instances
```

명령어에서 제한을 두지 않았기 때문에 리전 내 모든 인스턴스가 조회된다.   
명령어에서 옵션이나 필터를 지정하지 않는다면 리전 내 모든 인스턴스 정보가 포함되어 출력되기 때문에 성능에 영향을 줄 수 있으니 이렇게 사용하는 건 되도록 삼가하는 것이 좋다.  
```json
{
    "Reservations": [
        ..
    ]
}
```

***

인스턴스 id를 통해 해당 인스턴스의 정보만 조회하는 명령어이다.   
아래와 같이 `--instance-ids` subcommand subcommand의 파라미터로 인스턴스의 id를 넣어주면 된다.   
```bash
$ aws ec2 describe-instances --instance-ids <인스턴스 id>
```

해당 id를 가진 인스턴스가 존재한다면 아래와 같이 해당 인스턴스에 대한 정보가 출력된다.   
```json
{
    "Reservations": [
        {
            "Groups": [
                ..
            ],
            "Instances": [
                {
                    ..
                }
            ],
            "OwnerId": "<OwnerId>",
            "ReservationId": "<ReservationId>"
        }
    ]
}
```

***

`--filters` subcommand를 사용해 지정한 인스턴스 유형을 기준으로 조회하는 명령어이다.   
아래의 명령어는 인스턴스 유형이 t2.micro인 인스턴스를 찾는 명령어이다.   
```bash
$ aws ec2 describe-instances --filters Name=instance-type,Values=t2.micro
```

`--filters` subcommand에서 2개 이상의 조건을 적용하여 조회하는 명령어이다.   
아래의 명령어는 인스턴스 유형과 인스턴스에 적용된 보안 그룹 id를 기준으로 알맞는 인스턴스를 조회한다.   
```bash
$ aws ec2 describe-instances --filters Name=instance-type,Values=t2.micro Name=instance.group-id,Values=<보안 그룹 id>
```

`--filters` subcommand도 마찬가지로 파일을 사용하여 명령어를 수행할 수 있다.   
명령어 형식은 아래와 같다.
```bash
$  aws ec2 describe-instances --filters file://<파일 이름>
```

파일은 아래와 같이 작성하면 된다.   
필터가 더욱 복잡해지면 사전에 작성한 파일을 통해 비교적 쉽게 필터 조건을 지정할 수 있다.   
```json
[
        {
                "Name": "instance-type",
                "Values": [
                        "t2.micro"
                ]
        },
        {
                "Name": "availability-zone",
                "Values": [
                        "ap-northeast-2"
                ]
        }
]
```

***

global subcommand라고 할 수 있는 `--query` subcommand는 출력을 필터링할 수 있는 subcommand이다.   
아래의 명령어는 인스턴스의 정보 중에 인스턴스 id, 키 페어 이름, vpc id, 서브넷 id를 출력하는 명령어이다.   
```bash
$ aws ec2 describe-instances \
    --query 'Reservations[*].Instances[*].{Instance:InstanceId,KeyPair:KeyName,Vpc:VpcId,Subnet:SubnetId}'
```

```json
[
    [
        {
            "Instance": "<인스턴스 id>",
            "KeyPair": "<키 페어 이름>",
            "Vpc": "<vpc id>",
            "Subnet": "<서브넷 id>"
        }
    ]
]
```

`--filters`와 `--query`를 같이 사용하면 `--filters`에서 지정한 조건에 알맞게 인스턴스를 필터링하고 `--query`에서 지정한 값만 출력할 수 있다.
```bash
$ aws ec2 describe-instances \
    --filters "Name=instance-type,Values=t2.micro" \
    --query 'Reservations[*].Instances[*].{Instance:InstanceId,KeyPair:KeyName,Vpc:VpcId,Subnet:SubnetId}'
```
