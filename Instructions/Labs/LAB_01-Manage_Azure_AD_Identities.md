---
lab:
  title: '랩 01: Azure Active Directory ID 관리'
  module: Administer Identity
---

# 랩 01 - Azure Active Directory ID 관리

# 학생용 랩 매뉴얼

## 랩 시나리오

Contoso 사용자가 Azure AD를 사용하여 인증할 수 있도록 하려면 사용자 및 그룹 계정을 프로비전해야 합니다. 그룹의 구성원은 사용자 직위에 따라 자동으로 업데이트되어야 합니다. 또한 테스트 사용자 계정이 있는 Azure AD 테넌트를 만들고 Contoso Azure 구독의 리소스에 대한 제한된 권한을 해당 계정에 부여해야 합니다.

                **참고:** **[대화형 랩 시뮬레이션](https://mslabs.cloudguides.com/guides/AZ-104%20Exam%20Guide%20-%20Microsoft%20Azure%20Administrator%20Exercise%201)** 을 사용하여 이 랩을 원하는 속도로 클릭할 수 있습니다. 대화형 시뮬레이션과 호스트된 랩 간에 약간의 차이가 있을 수 있지만 보여주는 핵심 개념과 아이디어는 동일합니다.

## 목표

이 랩에서는 다음을 수행합니다.

+ 작업 1: Azure AD 사용자 만들기 및 구성
+ 작업 2: 할당된 동적 구성원을 사용하여 Azure AD 그룹 만들기
+ 작업 3: AD(Azure Active Directory) 테넌트 만들기(선택 사항 - 랩 환경 이슈)
+ 작업 4: Azure AD 게스트 사용자 관리(선택 사항 - 랩 환경 이슈)

## 예상 소요 시간: 30분

## 아키텍처 다이어그램
![이미지](../media/lab01.png)

### Instructions

## 연습 1

## 작업 1: Azure AD 사용자 만들기 및 구성

이 작업에서는 Azure AD 사용자를 만들고 구성합니다.

>**참고**: 이전에 이 Azure AD 테넌트에서 Azure AD Premium용 평가판 라이선스를 사용했다면 새 Azure AD 테넌트를 만들고 새 Azure AD 테넌트에서 작업 3 후에 작업 2를 수행해야 합니다.

1. [Azure Portal](https://portal.azure.com)에 로그인합니다.

1. Azure Portal에서 **Azure Active Directory**를 검색하고 선택합니다.

1. Azure Active Directory 블레이드에서 **관리** 섹션까지 아래로 스크롤하여 **사용자 설정**을 클릭하고 사용 가능한 구성 옵션을 검토합니다.

1. Azure Active Directory 블레이드의 **관리** 섹션에서 **사용자**를 클릭한 다음 사용자 계정을 클릭하여 **프로필** 설정을 표시합니다. 

1. **속성 편집**을 클릭하고 **설정** 탭에서 **사용 위치**를 **미국**으로 설정하고 **저장**을 클릭하여 변경 내용을 저장합니다.

    >**참고**: 이것은 이 랩의 후반부에서 사용자 계정에 Azure AD Premium P2 라이선스를 할당하려면 필요합니다.

1. **사용자 - 모든 사용자** 블레이드로 다시 이동한 다음 **+ 새 사용자**를 선택하세요.

1. 다음 설정을 사용하여 새 사용자를 만듭니다(다른 설정은 기본값으로 유지).

    | 설정 | 값 |
    | --- | --- |
    | 사용자 계정 이름 | **az104-01a-aaduser1** |
    | 표시 이름 | **az104-01a-aaduser1** |
    | 암호 자동 생성 | 선택 해제 |
    | 초기 암호 | **보안 암호 제공** |
    | 직호(속성 탭) | **클라우드 관리자** |
    | 부서(속성 탭) | **IT** |
    | 사용 위치(속성 탭) | **미국** |

    >**참고**: 전체 **사용자 계정 이름**(사용자 이름 및 도메인)을 **클립보드에 복사합니다**. 이 이름은 이 작업 뒷부분에서 필요합니다.

1. 사용자 목록에서 새로 만든 사용자 계정을 클릭하여 해당 블레이드를 표시합니다.

1. **관리** 섹션에서 사용할 수 있는 옵션을 검토하고 사용자 계정에 할당된 Azure AD 역할 및 Azure 리소스에 대한 사용자 계정의 권한을 식별할 수 있습니다.

1. **관리** 섹션에서 **할당된 역할**을 클릭한 다음, **+ 할당 추가** 단추를 클릭하고 **사용자 관리자** 역할을 **az104-01a-aaduser1**에 할당합니다.

    >**참고**: 새 사용자를 프로비전하는 경우 Azure AD 역할을 할당할 수도 있습니다.

1. **InPrivate** 브라우저 창을 열고 새로 만든 사용자 계정을 사용하여 [Azure Portal](https://portal.azure.com)에 로그인합니다. 암호를 업데이트하라는 메시지가 표시되면 암호를 선택한 보안 암호로 변경합니다. 

    >**참고**: 사용자 이름(도메인 이름 포함)을 입력하는 대신 클립보드의 콘텐츠를 붙여 넣을 수 있습니다.

1. **InPrivate** 브라우저 창의 Azure Portal에서 **Azure Active Directory**를 검색하고 선택합니다.

    >**참고**: 이 사용자 계정은 Azure Active Directory 테넌트에 액세스할 수 있지만 Azure 리소스에는 액세스할 수 없습니다. Azure 역할 기반 액세스 제어를 사용하여 이러한 액세스를 명시적으로 부여해야 하므로 이것이 예상됩니다. 

1. **InPrivate** 브라우저 창의 Azure AD 블레이드에서 **관리** 섹션으로 아래로 스크롤하여 **사용자 설정**을 클릭합니다. 구성 옵션을 수정할 수 있는 권한이 없다는 것에 유의하십시오.

1. **InPrivate** 브라우저 창의 Azure AD 블레이드의 **관리** 섹션에서 **사용자**를 클릭한 다음, **+ 새 사용자**를 클릭합니다.

1. 다음 설정을 사용하여 새 사용자를 만듭니다(다른 설정은 기본값으로 유지).

    | 설정 | 값 |
    | --- | --- |
    | 사용자 계정 이름 | **az104-01a-aaduser2** |
    | 표시 이름 | **az104-01a-aaduser2** |
    | 암호 자동 생성 | 선택 해제  |
    | 초기 암호 | **보안 암호 제공** |
    | 직함 | **시스템 관리자** |
    | department | **IT** |
    | 사용 위치 | **미국** |
    
1. Azure Portal에서 az104-aaduser1 사용자로 로그아웃하고 InPrivate 브라우저 창을 닫습니다.

## 작업 2: 할당된 동적 구성원을 사용하여 Azure AD 그룹 만들기

이 작업에서는 할당된 동적 구성원을 사용하여 Azure Active Directory 그룹을 만듭니다.

1. **사용자 계정**으로 로그인한 Azure Portal로 돌아가서 Azure AD 테넌트의 **개요** 블레이드로 다시 이동한 다음, **관리** 섹션에서 **라이선스**를 클릭합니다.

    >**참고**: 동적 그룹을 구현하려면 Azure AD Premium P1 또는 P2 라이선스가 필요합니다.

1. **관리** 섹션에서 **모든 제품**을 클릭합니다.

1. **+ 시용/구매** 클릭하여 Azure AD Premium P2의 무료 평가판을 활성화합니다.

1. 브라우저 창을 새로 고치고 성공적으로 활성화되었는지 확인합니다. 

 >**참고**: 라이선스를 활성화하는 데 최대 10분이 소요될 수 있습니다. 페이지가 나타날 때까지 계속 새로 고칩니다. 라이선스가 활성화될 때까지 진행하지 마세요.

1. **라이선스 - 모든 제품** 블레이드에서 **Azure Active Directory Premium P2** 항목을 선택하고 Azure AD Premium P2의 모든 라이선스 옵션을 사용자 계정 및 새로 만든 두 사용자 계정에 할당합니다.

1. Azure Portal에서 Azure AD 테넌트 블레이드로 돌아가서 **그룹**을 클릭합니다.

1. **+ 새 그룹** 단추를 사용하여 다음 설정을 사용하여 새 그룹을 만듭니다.

    | 설정 | 값 |
    | --- | --- |
    | 그룹 형식 | **보안** |
    | 그룹 이름 | **IT 클라우드 관리자** |
    | 그룹 설명 | **Contoso IT 클라우드 관리자** |
    | 멤버 자격 유형 | **동적 사용자** |

    >**참고**: **멤버십 유형** 드롭다운 목록이 회색으로 표시되면 잠시 기다렸다가 브라우저 페이지를 새로 고칩니다.

1. **동적 쿼리 추가**를 클릭합니다.

1. **동적 구성원 규칙** 블레이드의 **규칙 구성** 탭에서 다음 설정으로 새 규칙을 만듭니다.

    | 설정 | 값 |
    | --- | --- |
    | 속성 | **jobTitle** |
    | 연산자 | **같음** |
    | 값 | **Cloud Administrator** |

1. **+ 식 추가** 및 **저장**을 클릭하여 규칙을 저장합니다. **새 그룹** 블레이드로 돌아가서 **만들기**를 클릭합니다. 

1. Azure AD 테넌트의 **그룹 - 모든 그룹** 블레이드로 돌아와서 **+ 새 그룹** 단추를 클릭하고 다음 설정을 사용하여 새 그룹을 만듭니다.

    | 설정 | 값 |
    | --- | --- |
    | 그룹 형식 | **보안** |
    | 그룹 이름 | **IT 시스템 관리자** |
    | 그룹 설명 | **Contoso IT 시스템 관리자** |
    | 멤버 자격 유형 | **동적 사용자** |

1. **동적 쿼리 추가**를 클릭합니다.

1. **동적 구성원 규칙** 블레이드의 **규칙 구성** 탭에서 다음 설정으로 새 규칙을 만듭니다.

    | 설정 | 값 |
    | --- | --- |
    | 속성 | **jobTitle** |
    | 연산자 | **같음** |
    | 값 | **System Administrator** |

1. **+ 식 추가** 및 **저장**을 클릭하여 규칙을 저장합니다. **새 그룹** 블레이드로 돌아가서 **만들기**를 클릭합니다. 

1. Azure AD 테넌트의 **그룹 - 모든 그룹** 블레이드로 돌아와서 **+ 새 그룹** 단추를 클릭하고 다음 설정을 사용하여 새 그룹을 만듭니다.

    | 설정 | 값 |
    | --- | --- |
    | 그룹 형식 | **보안** |
    | 그룹 이름 | **IT 랩 관리자** |
    | 그룹 설명 | **Contoso IT 랩 관리자** |
    | 멤버 자격 유형 | **할당됨** |
    
1. **선택한 구성원 없음**을 클릭합니다.

1. **구성원 추가** 블레이드에서 **IT 클라우드 관리자** 및 **IT 시스템 관리자** 그룹을 검색 및 선택하고 **새 그룹** 블레이드로 돌아가서 **만들기**를 클릭합니다.

1. **그룹 - 모든 그룹** 블레이드로 돌아가서 **IT 클라우드 관리자** 그룹을 나타내는 항목을 클릭하여 **구성원** 블레이드를 표시합니다. **az104-01a-aaduser1**이 그룹 구성원 목록에 나타나는지 확인합니다.

    >**참고**: 동적 구성원 그룹의 업데이트로 지연이 발생할 수 있습니다. 업데이트를 신속하게 처리하려면 그룹 블레이드로 이동하여 **동적 구성원 규칙** 블레이드를 표시하고 끝에 공백을 추가하여 **규칙 구문** 텍스트 상자에 나열된 규칙을 **편집**하고 변경 내용을 **저장**합니다.

1. **그룹- 모든 그룹** 블레이드로 돌아가서 **IT 시스템 관리자** 그룹을 나타내는 항목을 클릭하여 해당 **구성원** 블레이드를 표시합니다. **az104-01a-aaduser2**가 그룹 구성원 리스트에 나타나는지 확인합니다.

## 작업 3: AD(Azure Active Directory) 테넌트 만들기(선택 사항 - 랩 환경 이슈)

이 작업에서는 새 Azure AD 테넌트를 만듭니다.
    
1. Azure Portal에서 **Azure Active Directory**를 검색하고 선택합니다.

    >**참고**: 랩 환경에서 Captcha 인증에 대해 알려진 이슈가 있습니다. **만들지 못했습니다. 요청이 너무 많습니다. 나중에 다시 시도하세요.** 오류가 표시되면 다음을 수행합니다.<br>
    - 만들기를 몇 번 시도합니다.<br>
    - **테넌트 관리** 섹션을 확인하여 테넌트가 백그라운드에서 만들어지지 않았는지 확인합니다. <br>
    - 새 **InPrivate** 창을 열고 Azure Portal을 사용하여 해당 위치에서 테넌트 만들기를 시도합니다.<br>
     트레이너 문제를 제기한 다음 **[대화형 랩 시뮬레이션](https://mslabs.cloudguides.com/guides/AZ-104%20Exam%20Guide%20-%20Microsoft%20Azure%20Administrator%20Exercise%201)** 을 사용하여 단계를 봅니다. <br>
    - 나중에 이 작업을 시도할 수 있지만 다른 랩에서는 테넌트 만들기가 필요하지 않습니다. 

1. **테넌트 관리**를 클릭한 후, 다음 화면에서 **+ 만들기**를 클릭하고, 다음 설정을 지정합니다.

    | 설정 | 값 |
    | --- | --- |
    | 디렉터리 유형 | **Azure Active Directory** |
    
1. **다음: 구성** 클릭

    | 설정 | 값 |
    | --- | --- |
    | 조직 이름 | **Contoso 랩** |
    | 초기 도메인 이름 | 소문자와 숫자로 구성된 유효하며 문자로 시작하는 DNS 이름 | 
    | 국가/지역 | **United States** |

   > **참고**: **초기 도메인 이름**이 귀사나 다른 조직과 잠재적으로 일치하는 합법적 이름이어서는 안 됩니다. **초기 도메인 이름** 텍스트 상자의 녹색 확인 표시는 입력한 도메인 이름이 유효하고 고유한지 여부를 나타냅니다.

1. **검토 + 만들기**를 클릭한 다음, **만들기**를 클릭합니다.

1. Azure Portal 도구 모음의 **새 테넌트로 이동하려면 여기를 클릭: Contoso 랩** 링크 또는 **디렉터리 + 구독** 단추(Cloud Shell 단추의 바로 오른쪽에 있음)를 사용하여 새로 만든 Azure AD 테넌트의 블레이드를 표시합니다.

## 작업 4: Azure AD 게스트 사용자 관리.

이 작업에서는 Azure AD 게스트 사용자를 만들어 Azure 구독의 리소스에 대한 액세스 권한을 부여합니다.

1. Contoso 랩 Azure AD 테넌트를 표시하는 Azure Portal의 **관리** 섹션에서 **사용자**를 클릭한 다음, **+ 새 사용자**를 클릭합니다.

1. 다음 설정을 사용하여 새 사용자를 만듭니다(다른 설정은 기본값으로 유지).

    | 설정 | 값 |
    | --- | --- |
    | 사용자 계정 이름 | **az104-01b-aaduser1** |
    | 표시 이름 | **az104-01b-aaduser1** |
    | 암호 자동 생성 | 선택 해제  |
    | 초기 암호 | **보안 암호 제공** |
    | 직함 | **System Administrator** |
    | department | **IT** |

1. 새로 만든 프로필을 클릭합니다.

    >**참고**: 전체 **사용자 계정 이름**(사용자 이름 및 도메인)을 **클립보드에 복사합니다**. 이 이름은 이 작업 뒷부분에서 필요합니다.

1. Azure Portal 도구 모음의 **디렉터리 + 구독** 단추(Cloud Shell 단추 오른쪽)를 사용하여 기본(첫 번째) Azure AD 테넌트로 다시 전환합니다.

1. **사용자 - 모든 사용자** 블레이드로 다시 이동한 다음, **+ 외부 사용자 초대**를 클릭합니다.

1. 다음 설정을 사용하여 새 게스트 사용자를 초대합니다(다른 설정은 기본값으로 유지).

    | 설정 | 값 |
    | --- | --- |
    | 메일 | 이 작업의 앞부분에서 복사한 사용자 주체 이름 |
    | 표시 이름(속성 탭)  | **az104-01b-aaduser1** |
    | 직호(속성 탭) | **랩 관리자** |
    | 부서(속성 탭) | **IT** |
    | 사용 위치(속성 탭) | **미국** |

1. **초대**를 클릭합니다. 

1. 다시 **사용자 - 모든 사용자** 블레이드로 돌아와서 새로 만들어진 게스트 사용자 계정을 나타내는 항목을 클릭하세요.

1. **az104-01b-aaduser1- 프로필** 블레이드에서 **그룹**을 클릭하세요.

1. **+ 멤버십 추가**를 클릭하고 게스트 사용자 계정을 **IT 랩 관리자** 그룹에 추가합니다.


## 작업 5: 리소스 정리

> **참고**: 더 이상 사용하지 않는 새로 만든 Azure 리소스는 모두 제거하세요. 사용하지 않는 리소스를 제거하면 예상하지 못한 비용이 발생하지 않습니다. 이 경우 Azure Active Directory 테넌트 및 해당 개체와 관련된 추가 요금이 없지만, 이 랩에서 만든 사용자 계정, 그룹 계정 및 Azure Active Directory 테넌트를 제거하는 것이 좋습니다.

 > **참고**:  랩 리소스를 즉시 제거할 수 없어도 걱정하지 마세요. 리소스에 종속성이 있고 삭제하는 데 시간이 더 오래 걸리는 경우가 있습니다. 리소스 사용량을 모니터링하는 것은 일반적인 관리자 작업이므로 포털에서 리소스를 주기적으로 검토하여 정리가 어떻게 진행되고 있는지 확인합니다. 

1. **Azure Portal**의 검색 창에서 **Azure Active Directory**를 검색합니다. **Azure Active Directory**의 **관리**에서 **라이선스**를 선택합니다. **관리** 아래의 **라이선스**에서 **모든 제품**을 선택한 다음, 목록에서 **Azure Active Directory Premium P2** 항목을 선택합니다. **허가된 사용자**를 선택하여 계속 진행합니다. 이 랩에서 라이선스를 할당한 사용자 계정 **az104-01a-aaduser1** 및 **az104-01a-aaduser2**를 선택하고, **라이선스 제거**를 클릭하고, 확인하라는 메시지가 표시되면 **확인**을 클릭합니다.

1. Azure Portal에서 **사용자 - 모든 사용자** 블레이드로 이동하여 **az104-01b-aaduser1** 게스트 사용자 계정을 나타내는 항목을 클릭하고 **az104-01b-aaduser1 - 프로필** 블레이드에서 **삭제**를 클릭한 후 확인하라는 메시지가 표시되면 **확인**을 클릭합니다.

1. 이 랩에서 만든 남은 사용자 계정을 삭제하려면 동일한 단계 시퀀스를 반복하세요.

1. **그룹- 모든 그룹** 블레이드로 이동해서 이 랩에서 만든 그룹을 선택하고 **삭제**를 클릭하고 확인하라는 메시지가 표시되면 **확인**을 클릭합니다.

1. Azure Portal에서 Azure Portal 도구 모음의 **디렉터리 + 구독**단추(Cloud Shell 단추 오른쪽)을 이용해 Contoso 랩 Azure Azure AD 테넌트의 블레이드를 표시하세요.

1. **사용자 - 모든 사용자** 블레이드로 이동하여 **az104-01b-aaduser1** 사용자 계정을 나타내는 항목을 클릭하고, **az104-01b-aaduser1 - 프로필** 블레이드에서 **삭제**를 클릭한 후 확인하라는 메시지가 표시되면 **확인**을 클릭하세요.

1. Contoso 랩 Azure AD 테넌트의 **Contoso 랩 - 개요** 블레이드로 이동하고, **테넌트 관리**를 클릭한 후, 다음 화면에서 **Contoso 랩** 옆의 상자를 선택하고, **삭제**를 클릭하고, **테넌트 ‘Contoso 랩’ 삭제?** 블레이드에서 **Azure 리소스 삭제 권한 가져오기** 링크를 클릭하고, Azure Active Directory의 **속성** 블레이드에서 **Azure 리소스에 대한 액세스 관리**를 **예**로 설정하고, **저장**을 클릭합니다.

1. **테넌트 삭제 ‘Contoso 랩’ 삭제** 블레이드로 돌아가서, **새로 고침**을 클릭하고, **삭제**를 클릭합니다.

> **참고**: 테넌트에 평가판 라이선스가 있는 경우 테넌트를 삭제하기 전에 평가판 라이선스 만료를 기다려야 합니다. 이로 인한 추가 비용이 발생하지 않습니다.

#### 검토

이 랩에서는 다음을 수행합니다.

- Azure AD 사용자 만들기 및 구성
- 할당된 동적 구성원을 사용하여 Azure AD 그룹 만들기
- Azure Active Directory(AD) 테넌트 만들기
- Azure AD 게스트 사용자 관리 
