## describe-regions

### 설명
현재 사용하는 계정에서 활성화된 리전을 조회할 수 있는 명령어이다.

### SubCommand
describe-regions에서 사용 가능한 subcommand는 전부 global option

### 사용 예제
```bash
$ aws ec2 describe-regions
```

```json
{
    "Regions": [
        {
            "Endpoint": "ec2.eu-north-1.amazonaws.com",
            "RegionName": "eu-north-1",
            "OptInStatus": "opt-in-not-required"
        },
        {
            "Endpoint": "ec2.ap-south-1.amazonaws.com",
            "RegionName": "ap-south-1",
            "OptInStatus": "opt-in-not-required"
        },
        {
            "Endpoint": "ec2.eu-west-3.amazonaws.com",
            "RegionName": "eu-west-3",
            "OptInStatus": "opt-in-not-required"
        },
        ...
    ]
}
```