## AWS IAM 계정 만들기
이 문서에서는 AWS CLI를 다루기 위해 필요한 IAM 계정 생성을 안내한다.   

### AWS IAM 계정 생성

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/create-iam-act_1.png"><br />
    그림 1. IAM Dashboard
</p>

AWS Console에서 IAM 서비스에 접근한다.   
IAM 대시보드에서 좌측의 메뉴에서 사용자로 이동한다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/create-iam-act_2.png"><br />
    그림 2. 사용자
</p>

사용자 메뉴로 이동해주었다면 사용자 추가를 눌러 IAM 계정을 추가해주어야 한다.   
root 계정일 경우, 사용자 추가를 할 수 있지만 root 계정 이외에 IAM 계정으로 로그인하고 있다면 사용자 추가 권한이 없다면 이 작업을 할 수 없다는 것을 알아두어야 한다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/create-iam-act_3.png"><br />
    그림 3. 사용자 추가 - 1
</p>

사용자 추가를 눌렀을 때 총 5단계를 거쳐야 사용자가 추가되는데 우선 1번째 단계이다.   
사용자의 이름과 AWS 엑세스 유형을 선택하는 단계인데 여기서 **그림 2**와 같이 프로그래밍 방식 엑세스를 반드시 선택해주어야 한다.   
이것을 선택해주어야 후에 엑세스 키가 발급되고 이를 통해 AWS CLI로 작업이 가능하다.   
선택해주었다면 다음 단계로 넘어간다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/create-iam-act_4.png"><br />
    그림 4. 사용자 추가 - 2
</p>

2단계는 권한 설정이다.   
현재 생성 중인 계정이 AWS 내에서 어떤 서비스에 접근이 가능하며 얼만큼의 제어가 가능한지 지정해주는 단계이다.   
필자는 Admin 권한을 넣어주었으나 원한다면 따로 권한 설정을 하는 것도 좋다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/create-iam-act_5.png"><br />
    그림 5. 사용자 추가 - 3
</p>

사용자의 태그를 지정하는 단계이다.   
현재는 크게 중요한 부분은 아니기 때문에 설정하지 않고 다음으로 넘어가도 된다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/create-iam-act_6.png"><br />
    그림 6. 사용자 추가 - 4
</p>

마지막 검토 단계이다.
1 ~ 3단계까지 설정한 것을 검토하는데 이때 AWS 엑세스 유형에 **프로그래밍 방식 엑세스**가 반드시 있어야 한다.   
그렇지 않다면 1단계로 돌아가 프로그래밍 방식 엑세스에 체크해주어야 한다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/create-iam-act_7.png"><br />
    그림 7. 사용자 추가 - 5
</p>

이제 마지막 단계이다.   
.csv 다운로드를 눌러 .csv 파일을 다운받는다.   
이 파일에 AWS CLI나 AWS SDK로 AWS 서비스에 접근할 수 있는 엑세스 키가 있기 때문에 반드시 다운받아야 한다.   

<p align="center" width="100%">
    <br /><br /><img src="https://github.com/lock-user/aws-cli-informality-guide/blob/main/image/install/create-iam-act_8.png"><br />
    그림 8. csv
</p>

다운받은 csv 파일을 열면 **그림 8**과 같이 사용자 이름, 엑세스 키 ID, 비밀 엑세스 키 등이 적혀있다.   
이 파일에서 필요한 것은 엑세스 키 ID와 비밀 엑세스 키이다.   
또한 이러한 엑세스 정보는 타인에게 알려주지 않는 것이 좋다.   
여기까지 모두 따라왔다면 다시 [여기](https://github.com/lock-user/aws-cli-informality-guide/blob/main/docs/install-guide/aws-cli-install.md)로 돌아가도 좋다.
