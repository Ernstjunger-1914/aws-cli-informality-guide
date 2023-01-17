## export-image

### 설명
ami를 vm 파일로 내보낸다.   
자세한 내용은 [이 문서](https://docs.aws.amazon.com/ko_kr/vm-import/latest/userguide/vmexport_image.html)를 참고

### SubCommand
```bash
aws ec2 export-image
[--client-token <string>]
[--description <string>]
[--disk-image-format <string>]
[--dry-run | --no-dry-run]
[--image-id <string>]
[--s3-export-location <structure>]
[--role-name <string>]
[--tag-specifications <list>]
[--cli-input-json <string>]
[--generate-cli-skeleton <string>]
```

`--client-token`
> export 이미지 요청에 대한 id 권한을 활성화하기 위한 토큰

`--description`
> export할 이미지에 대한 설명이다.   
> 최대 255자까지 작성이 가능하다.

`--disk-image-format`
> 디스크 이미지의 format 형식   
> 사용 가능한 값은 `VMDK`, `RAW`, `VHD`이다.

`--dry-run` | `--no-dry-run`   
> 실제로 요청을 보내지는 않고 작업에 필요한 권한이 있는지 확인하고 에러 응답을 제공한다.   
> 필요한 권한이 있을 경우의 응답은 `DryRunOperation`, 그렇지 않는 경우의 응답은 `UnauthorizedOperation`이다.   

`--image-id`
> 이미지 id

`--s3-export-location`
> 대상 이미지의 s3 버킷   
> `S3Bucket`   
>> 대상 s3 버킷   
>
> `S3Prefix`   
>> 버킷의 접두사

`--role-name`
> 이미지를 s3 버킷으로 export할 수 있는 `vm import/export` 권한을 부여하는 역할의 이름

`--tag-specifications`
> export할 이미지 작업에 적용할 태그

`--cli-input-json`   
> 제공된 json 데이터를 기반으로 서비스 작업을 수행한다.   
> json 데이터는 `--generate-cli-skeleton` subcommand에서 제공하는 형태를 따르며 CLI에 다른 인수가 제공된 경우 CLI 값이 json에서 제공한 값을 재정의한다.   
> `file://` 접두사를 통해 사전에 작성된 파일을 파라미터로 전달하여 명령을 실행한다.   

`--generate-cli-skeleton`   
> 해당 subcommand를 사용하면 명령이 실행되지 않지만, 이후 명령에 입력으로 사용할 수 있는 파라미터 템플릿을 생성 및 표시할 수 있다.   
> 사용 가능한 값은 `input`, `yaml-input`, `output`이며 기본값은 input이다.  

### 사용 예제

#### AMI 내보내기

아래의 명령어는 ami를 명령어로 지정한 format과 s3 버킷으로 내보내는 명령어이다.
```bash
$ aws ec2 export-image \
    --image-id <ami id> \
    --disk-image-format <디스크 이미지 format 형식> \
    --s3-export-location S3Bucket=<s3 버킷 이름>,S3Prefix=<s3 버킷 내 디렉토리>
```

ami가 정상적으로 내보내지면 아래와 같이 출력된다.
```json
{
    "DiskImageFormat": "<디스크 이밎 format 형식>",
    "ExportImageTaskId": "<내보내기한 이미지 id>"
    "ImageId": "<ami id>",
    "RoleName": "<적용된 iam 역할>",
    "Progress": "0",
    "S3ExportLocation": {
        "S3Bucket": "<s3 버킷 이름>",
        "S3Prefix": "<s3 버킷 내 디렉토리>"
    },
    "Status": "active",
    "StatusMessage": "validating"
}
```