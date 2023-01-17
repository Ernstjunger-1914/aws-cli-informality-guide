## copy-image

### 설명

### SubCommand
```bash
aws ec2 copy-image
[--description <string>]
[--encrypted | --no-encrypted]
[--kms-key-id <string>]
[--name <string>]
[--source-image-id <string>]
[--source-region <string>]
[--region <string>]
```

`--description`
> ami 설명이다.

`--encrypted` | `--no-encrypted`

`--kms-key-id`
> 암호화된 볼륨을 생성할 때 사용할 대칭키 관리 서비스의 식별자이다.   
> 해당 subcommand를 따로 지정하지 않으면 ebs용 kms 키가 사용된다.   
> kms 키를 지정하는 경우에는 `--encrypted` subcommnad를 사용하여 암호화 상태를 true로 설정해야 한다.

`--name`
> ami의 이름이다.

`--source-image-id`
> 복사할 ami의 id이다.

`--source-region`
> 복사할 ami가 있는 리전의 이름이다.

`--region`
> 복사한 ami를 옮길 리전의 이름이다.

### 사용 예제

#### AMI 복사

아래의 명령어는 특정 리전에 있는 ami를 다른 리전으로 복사하는 명령어이다.
```bash
$ aws ec2 copy-image \
    --region <복사한 ami를 옮길 리전> \
    --name <ami 이름> \
    --source-region <ami가 있는 리전> \
    --source-image-id <복사할 ami id> \
    --description "<ami 설명>"
```

ami가 정상적으로 복사되면 아래와 같이 ami의 id가 출력된다.
```json
{
    "ImageId": "<ami id>"
}
```


