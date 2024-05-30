---
description: AWS 리소스 구축을 위한 청사진입니다.
---

# 템플릿

## 템플릿&#x20;

> AWS 리소스 구축을 위한 청사진입니다.&#x20;

* .json, .yaml, .template, .txt 등을 사용합니다.&#x20;

### 예시&#x20;

> `ami-0ff8a91507f77f867` AMI ID, `t2.micro` 인스턴스 유형, `testkey` 키 페어 이름 및 Amazon EBS 볼륨을 사용하여 인스턴스를 프로비저닝하는 예시입니다.&#x20;

#### JSON&#x20;

```json
{
    "AWSTemplateFormatVersion": "2010-09-09",
    "Description": "A sample template",
    "Resources": {
        "MyEC2Instance": {
            "Type": "AWS::EC2::Instance",
            "Properties": {
                "ImageId": "ami-0ff8a91507f77f867",
                "InstanceType": "t2.micro",
                "KeyName": "testkey",
                "BlockDeviceMappings": [
                    {
                        "DeviceName": "/dev/sdm",
                        "Ebs": {
                            "VolumeType": "io1",
                            "Iops": 200,
                            "DeleteOnTermination": false,
                            "VolumeSize": 20
                        }
                    }
                ]
            }
        }
    }
}
```

#### YAML

```yaml
AWSTemplateFormatVersion: 2010-09-09
Description: A sample template
Resources:
  MyEC2Instance:
    Type: 'AWS::EC2::Instance'
    Properties:
      ImageId: ami-0ff8a91507f77f867
      InstanceType: t2.micro
      KeyName: testkey
      BlockDeviceMappings:
        - DeviceName: /dev/sdm
          Ebs:
            VolumeType: io1
            Iops: 200
            DeleteOnTermination: false
            VolumeSize: 20

```



## 템플릿 섹션&#x20;

> 템플릿에는 여러 주요 섹션이 포함되어 있습니다.&#x20;

* Resources  섹션만 필수 섹션입니다.&#x20;

### 논리적 순서&#x20;

> 기본적으로는 임의 순서대로 지정이 가능하지만, 이전 섹션을 참고할 수 있습니다. \
> 때문의 다음 순서를 사용하는 것이 좋습니다.&#x20;



<table><thead><tr><th width="137">섹션명</th><th width="426">설명</th><th>필수여부</th></tr></thead><tbody><tr><td>포멧버전</td><td><ul><li>템플릿이 따르는 AWS CloudFormation 템플릿 버전입니다.</li><li>템플릿 포맷 버전은 API 또는 WSDL 버전과 같지 않습니다. 템플릿 포맷 버전은 API 및 WSDL 버전과 상관없이 변경될 수 있습니다.</li></ul></td><td>선택사항</td></tr><tr><td>Description</td><td><ul><li>템플릿을 설명하는 텍스트 문자열입니다.</li><li>이 섹션은 항상 템플릿 포맷 버전 섹션 다음에 이어져야 합니다.</li></ul></td><td>선택사항</td></tr><tr><td>Metadata</td><td><ul><li>템플릿에 대한 추가 정보를 제공하는 객체입니다.</li></ul></td><td>선택사항</td></tr><tr><td>Parameters</td><td><ul><li>(스택을 생성하거나 업데이트할 때) 실행 시간에 템플릿에 전달하는 값입니다.</li><li>템플릿의 <code>Resources</code> 및 <code>Outputs</code> 섹션에서 파라미터를 참조할 수 있습니다.</li></ul></td><td>선택사항</td></tr><tr><td>규칙</td><td><ul><li>스택을 생성하거나 업데이트할 때 템플릿에 전달된 파라미터 또는 파라미터의 조합을 검증합니다.</li></ul></td><td>선택사항</td></tr><tr><td>Mappings</td><td><ul><li>조건부 파라미터 값을 지정하는 데 사용할 수 있는 키와 관련 값의 매핑으로, 조회 테이블과 비슷합니다.</li><li><code>Resources</code> 및 <code>Outputs</code> 섹션의 <a href="https://docs.aws.amazon.com/ko_kr/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-findinmap.html">Fn::FindInMap</a> 내장 함수를 사용하여 키를 해당 값으로 매핑할 수 있습니다.</li></ul></td><td>선택사항</td></tr><tr><td>Conditions </td><td><ul><li>스택 생성 또는 업데이트 시 특정 리소스 속성에 값이 할당되는지 또는 특정 리소스가 생성되는지 여부를 제어하는 조건입니다.</li><li>스택이 프로덕션용인지 테스트 환경용인지에 따라 달라지는 리소스를 조건부로 생성할 수 있습니다.</li></ul></td><td>선택사항</td></tr><tr><td>Transform </td><td><ul><li>서버리스에서 사용할 <a href="https://github.com/awslabs/serverless-application-specification">AWS Serverless Application Model(AWS SAM)</a>의 버전을 지정합니다.</li><li>변환을 지정할 경우 AWS SAM 구문을 사용하여 템플릿에 리소스를 선언할 수 있습니다</li></ul></td><td>선택사항</td></tr><tr><td>Resources</td><td><ul><li>스택 리소스 및 해당 속성을 지정합니다.</li></ul></td><td>필수</td></tr><tr><td>Outputs</td><td><ul><li>스택의 속성을 볼 때마다 반환되는 값을 설명합니다.</li><li><code>aws cloudformation describe-stacks</code> AWS CLI 명령을 호출하여 해당 이름을 볼 수 있습니다.</li></ul></td><td>선택사항</td></tr></tbody></table>

### 포멧버전&#x20;

> `AWSTemplateFormatVersion` 섹션은 템플릿의 기능을 식별합니다. 최신 템플릿 포맷 버전은 `2010-09-09`이며 현재 유일한 유효 값입니다.

* 값을 지정하지 않을 경우 최신 버전이라고 가정합니다.&#x20;
* 리터럴 문자이어야합니다.&#x20;
* 파라미터나 함수를 사용해 포맷 버전을 지정할 수 있습니다.&#x20;

#### JSON

```json
"AWSTemplateFormatVersion" : "2010-09-09"
```

#### YAML

```yaml
AWSTemplateFormatVersion: "2010-09-09"
```



### Description&#x20;

> 템플릿의 `Description` 섹션(선택 사항)에 템플릿에 대한 설명을 지정합니다.

* 0\~1023 바이트 길이의 리터럴 문자열이어야 합니다.
* 파라미터나 함수를 사용할 수 없습니다.&#x20;
* 업데이트 중 수정이 불가능합니다.&#x20;

#### JSON

```json
"Description" : "Here are some details about the template."
```

#### YAML

```yaml
Description: >
  Here are some
  details about
  the template.
```





