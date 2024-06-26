---
description: CloudFormation에서는 스택이라는 하나의 단위로 리소스들을 관리합니다.
---

# 스택

## 1. 개요

* 스택이라는 하나의 단위로 리소스를 관리합니다.&#x20;
* 스택의 모든 리소스는 스택의 CloudFormation 템플릿으로 정의합니다.&#x20;
* 스택에서 실행 중인 리소스를 변경해야하는 경우 스택을 업데이트합니다.&#x20;

## 2. 스택 업데이트&#x20;

> 스택의 설정을 변경하거나 리소스를 변경하는 경우 스택 업데이트를 이용해서 간편하게 변경할 수 있습니다.&#x20;

### 2-1. 원리

1. 변경사항(새 입력 파라미터 값 또는 업데이트된 템플릿)을 작성합니다.&#x20;
2. CloudFormation에서는 제출한 변경사항과 스택의 현재 상태를 비교하여 변경된 리소스만 업데이트합니다.&#x20;

### 2-2. 업데이트 방법&#x20;

> 직접 업데이트와 변경 세트 생성 및 실행 총 두 가지 방법을 제공합니다.&#x20;

#### a. 스택을 직접 업데이트&#x20;

* 변경사항을 제출합니다.&#x20;
* AWS CloudFormation에서 즉시 해당사항을 배포합니다.&#x20;

{% hint style="info" %}
업데이트를 빠르게 배포할 때 사용합니다.&#x20;
{% endhint %}

#### b. 변경 세트 사용&#x20;

1. &#x20;AWS CloudFormation에서 스택에 대해 변경사항을 미리 확인합니다.&#x20;
2. 변경사항을 적용할지 결정합니다.&#x20;





### 2-3 스택 리소스의 업데이트 동작&#x20;

> 업데이트한 리소스의 경우 AWS CloudFormation에서는 다음 동작 중 하나를 사용합니다.&#x20;



#### a.업데이트(무중단)

> 해당 리소스의 작동을 중단하지 않고, 리소스의 물리적 ID를 변경하지 않는 상태에서 리소스를 업데이트합니다.

#### b.업데이트(중단)

> 리소스를 업데이트하지만, 다소 중단이 발생합니다.&#x20;

#### c.대체

> 업데이트 도중 리소스를 다시 생성하며, 물리적 ID도 생성합니다.&#x20;

일반적인 방법은 아래와 같습니다.&#x20;

1. 리소스를 먼저 생성합니다.
2. 대체 리소스를 가리키도록 종속 리소스의 참조를 변경합니다
3. 이전 리소스를 삭제합니다.&#x20;

{% hint style="info" %}
AWS 리소스 유형에 따라 업데이트하는 속성이 달라집니다. \
각 속성에 대한 업데이트 동작은 [AWS 리소스 유형 참조](https://docs.aws.amazon.com/ko\_kr/AWSCloudFormation/latest/UserGuide/aws-template-resource-type-ref.html)에 설명되어 있습니다.
{% endhint %}





### 2-3. AWS 리소스를 대체해야하는 경우 설정하기&#x20;

> RDS의 Port를 업데이트하는 경우 CloudFormation에서는 업데이트된 포트 설정을 사용하여 새 DB 인스턴스를 생성하고 대체하여 무중단 배포를 구성할 수 있습니다. 방법은 아래와 같습니다.&#x20;

1. 현재 DB의 스냅샷을 생성합니다.&#x20;
2. DB 인스턴스를 바꾸는 동안 해당 DB를 사용하는 앱에서 중단을 처리할 방법을 준비합니다.&#x20;
3. 앱에서 업데이트된 포트 설정과 기타 고려사항이 적용되었는지 확인합니다.&#x20;
4. DB 스냅샷을 사용하여 새 DB 인스턴스에서 정보를 복원합니다.



&#x20;
