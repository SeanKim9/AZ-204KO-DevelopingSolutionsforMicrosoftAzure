---
lab:
    title: '랩: Azure API Management를 사용하여 다중 계층 API 만들기'
    module: '모듈 08: API Management 구현'
    type: 'Answer Key'
---

# 랩: Azure에서 서비스를 사용하여 다중 계층 솔루션 만들기
# 학생 랩 Answer Key

## Microsoft Azure 사용자 인터페이스

Microsoft 클라우드 도구의 동적 특성을 감안할 때, 이 교육 콘텐츠를 개발한 후 Azure UI가 변경될 수 있습니다. 이러한 변경으로 인해 랩 지침 및 단계가 일치하지 않을 수 있습니다.

Microsoft는 커뮤니티에서 주목해야 할 변경 사항이 있을 때 이 학습 과정을 업데이트합니다. 그러나 클라우드 업데이트가 자주 이루어지기 때문에 이 학습 콘텐츠가 업데이트되기 전에 UI가 변경될 수 있습니다. **이 경우 변경 사항에 적응하고 필요에 따라 랩에서 작업합니다.**

## 지침

### 시작하기 전에

#### 랩 가상 머신에 로그인

다음 자격 증명을 사용하여 Windows 10 VM(가상 머신)에 로그인합니다.
    
-   사용자 이름: **Admin**

-   암호: **Pa55w.rd**

> **참고**: 강사가 가상 랩 환경 연결에 대한 지침을 제공합니다.

#### 설치된 응용 프로그램 리뷰

Windows 10 데스크톱에서 작업 표시줄을 찾습니다. 작업 표시줄에는 이 랩에서 사용할 애플리케이션에 대한 아이콘이 포함되어 있습니다.
    
-   Microsoft Edge

### 연습 1: Docker 컨테이너 이미지를 사용하여 Azure App Service 리소스 만들기

#### 작업 1: Azure Portal 열기

1.  작업 표시줄에서 **Microsoft Edge** 아이콘을 선택합니다.

1.  열려 있는 브라우저 창에서 Azure Portal(<https://portal.azure.com>)로 이동합니다.

1.  로그인 페이지에서 Microsoft 계정의 이메일 주소를 입력한 후 **다음**을 선택합니다.

1.  Microsoft 계정의 암호를 입력한 다음 **로그인**을 선택합니다.

    > **참고**: Azure Portal에 처음 로그인하는 경우 포털 둘러보기 기능이 제공됩니다. 둘러보기를 건너뛰고 포털을 사용하려면 **시작하기**를 선택합니다.

#### 작업 2: httpbin 컨테이너 이미지를 사용하여 Azure App Service 리소스를 통해 웹앱 만들기

1.  Azure Portal 탐색 창에서 **리소스 만들기**를 선택합니다.

1.  **새로 만들기** 블레이드에서 **마켓플레이스 검색** 텍스트 상자를 찾습니다.

1.  검색 상자에서 **웹 앱**을 입력한 다음 Enter 키를 선택합니다.

1.  **마켓플레이스** 검색 결과 블레이드에서 **웹 앱** 결과를 선택합니다.

1.  **웹 앱** 블레이드에서 **만들기**를 선택합니다.

1.  두 번째 **웹앱** 블레이드에서 **기본**과 같은 블레이드의 탭을 찾습니다.

    > **참고**: 각 탭은 새 웹앱을 만드는 워크플로의 단계를 나타냅니다. 언제든지 **검토 + 만들기**를 선택하여 나머지 탭을 건너뛸 수 있습니다.

1.  **기본** 탭에서 다음 작업을 수행합니다.
    
    1.  **구독** 텍스트 상자를 기본값으로 설정합니다.
    
    1.  **리소스 그룹** 섹션에서 **새로 만들기**를 선택하고 **ApiService**를 입력한 다음 **확인**을 선택합니다.
    
    1.  **이름** 텍스트 상자에 **httpapi*[yourname]*** 을(를) 입력합니다.

    1.  **게시** 섹션에서 **Docker 컨테이너**를 선택합니다.

    1.  **운영 체제** 섹션에서 **Linux**를 선택합니다.

    1.  **지역** 드롭다운 목록에서 **East US** 지역을 선택합니다.

    1.  **Linux 플랜(East US)** 섹션에서 **새로 만들기**를 선택하고 **이름** 텍스트 상자에 **ApiPlan**을 입력한 다음 **OK**를 선택합니다.

    1.  **SKU 및 크기** 섹션을 기본값으로 둡니다.

    1.  **다음: Docker**를 선택합니다.

1.  **Docker** 탭에서 다음 작업을 합니다.

    1.  **옵션** 드롭다운 목록에서 **단일 컨테이너**를 선택합니다.

    1.  **이미지 소스** 드롭다운 목록에서 **Docker Hub**를 선택합니다.

    1.  **액세스 형식** 드롭다운 목록에서 **공개**를 선택합니다.

    1.  **이미지 및 태그** 텍스트 상자에 **kennethreitz/httpbin:latest**를 입력합니다.

    1.  **검토 + 만들기**를 선택합니다.

1.  **검토 + 만들기** 탭에서 이전 단계에서 선택한 옵션을 검토합니다.

1.  지정된 구성을 사용하여 웹앱을 만들려면 **만들기**를 선택합니다. 

    > **참고**: 이 랩을 진행하기 전에 만들기 작업이 완료될 때까지 기다립니다.

#### 작업 3: httpbin 웹 애플리케이션 테스트

1.  Azure Portal의 탐색 창에서 **리소스 그룹**을 선택합니다.

1.  **리소스 그룹** 블레이드에서 앞서 전에 만든 **ApiService** 리소스 그룹을 선택합니다.

1.  앞서 만든 **httpapi*[yourname]*** 웹앱을 선택합니다.

1.	**웹앱** 블레이드 개요 상단메뉴에서 **찾아보기**를 선택합니다.

1.  웹 애플리케이션에서 다음 작업을 합니다.

    1.  **Response formats**을 선택합니다.

    1.  **GET /xml**을 선택합니다.

    1.  **Try it out**를 선택합니다.

    1.  **Execute**을 선택합니다.

    1.  **Response body** 및 **Response headers** 텍스트 상자의 값을 관찰합니다.

    1.  **Request URL** 텍스트 상자의 값을 관찰합니다.

1.  웹 애플리케이션의 브라우저 창을 닫습니다.

1.  Azure Portal에서 **httpapi*[yourname]*** 웹앱의 **웹앱** 블레이드를 다시 찾습니다.

1.  **설정** 섹션에서 **속성** 링크를 선택합니다.

1.  **속성** 섹션에서 **URL** 텍스트 상자 값을 기록합니다. 이 값을 나중에 랩에서 사용하여 API에 대한 요청을 합니다.

#### 검토

이 연습에서는 Docker Hub에서 얻은 컨테이너 이미지를 사용하여 새 Azure 웹앱을 만들었습니다.

### 연습 2: Azure API Management를 사용한 API 프록시 계층 빌드

#### 작업 1: API Management 리소스 만들기

1.  Azure Portal 탐색 창에서 **리소스 만들기**를 선택합니다.

1.  **새로 만들기** 블레이드에서 **마켓플레이스 검색** 텍스트 상자를 찾습니다.

1.  검색 상자에서 **API**를 입력한 다음 Enter 키를 선택합니다.

1.  **마켓플레이스** 검색 결과 블레이드에서 **API Management** 결과를 선택합니다.

1.  **API Management** 블레이드에서 **만들기**를 선택합니다.

1.  **API Management 서비스** 블레이드에서 다음 작업을 수행합니다.
    
    1.  **이름** 텍스트 상자에 **prodapi*[yourname]*** 을(를) 입력합니다.
    
    1.  **구독** 텍스트 상자를 기본값으로 설정합니다.
    
    1.  **리소스 그룹** 목록에서 이 랩에서 전에 만든 **ApiService** 그룹을 선택합니다.
    
    1.  **위치** 목록에서 **미국 동부**를 선택합니다.
    
    1.  **조직 이름** 텍스트 상자에 **Contoso**를 입력합니다.
    
    1.  **관리자 이메일** 텍스트 상자를 기본값으로 설정한 상태로 둡니다.
    
    1.  **가격 책정 계층** 목록에서 **소비(99.9 SLA, %)** 을 선택합니다.
    
    1.  **만들기**를 선택합니다.

    > **참고**: 이 랩을 진행하기 전에 만들기 작업이 완료될 때까지 기다립니다.

#### 작업 2: 새 API 정의

1.  Azure Portal의 탐색 창에서 **리소스 그룹**을 선택합니다.

1.  **리소스 그룹** 블레이드에서 이 랩에서 전에 만든 **ApiService** 리소스 그룹을 선택합니다.

1.  **ApiService** 블레이드에서 이전에 랩에서 만든 **prodapi*[yourname]*** API Management 계정을 선택합니다.

1.  **APIs** 섹션에서 **API**를 선택합니다.

1.  **Add a new API** 섹션에서 **Blank API**를 선택합니다.

1.  **Create a blank API** 창에서 다음 작업을 합니다.
    
    1.  **Display name** 텍스트 상자에 **HTTPBin API**를 입력합니다.
    
    1.  **Name** 텍스트 상자에 **httpbin-api**를 입력합니다.
    
    1.  **Web service URL** 텍스트 상자에 이전에 랩에서 복사한 웹앱의 URL을 입력합니다.

        > **참고**: URL을 복사하는 방법에 따라, 유효한 URL 값을 만들기 위해 "http://" 접두사를 추가해야 할 수 있습니다.

    1.  **API URL suffix** 텍스트 상자를 비워 둡니다.

    1.  **Create**를 선택합니다.

    > **참고**: 새 API가 생성될 때까지 기다립니다.

1.  **Design** 탭에서 **Add operation**를 선택합니다.

1.  **Add operation** 섹션에서 다음 작업을 수행합니다.
    
    1.  **Display name** 텍스트 상자에 **Echo Headers**를 입력합니다.
    
    1.  **Name** 텍스트 상자에 **echo-headers**를 입력합니다.
    
    1.  **URL** 목록에서 **GET**을 선택합니다.

    1.  **URL** 텍스트 상자에 **/** 를 입력합니다.
    
    1.  **저장**을 선택합니다.

1.	**Design** 탭으로 돌아가 작업 목록에서 **All Operations**을 선택합니다.

1.	**All Operations**의 **Design** 섹션에서 **Inbound processing** 타일을 찾아 **Add policy**를 선택합니다.

1.	**Add inbound policy** 섹션에서 **Set headers** 타일을 선택합니다.

1.	**Inbound processing에서 Set headers** 섹션에서 다음 작업을 합니다.
    
    1.  **NAME** 텍스트 상자에 **source**를 입력합니다.
    
    1.  **VALUE** 텍스트 상자에서 목록을 선택하고 **Add value**를 선택한 후 **azure-api-mgmt**를 입력합니다.
    
    1.  **Action** 목록에서 **append**를 선택합니다.
    
    1.  **Save**을 선택합니다.

1.	**Design** 탭으로 돌아가 작업 목록에서 **Echo Headers**를 선택합니다.

1.	**Echo Headers**의 **Design** 섹션에서 **Backend** 타일을 찾은 다음 연필 아이콘을 선택합니다.

1.  **Backend** 섹션에서 다음 작업을 합니다.

    1.  **Service URL** 섹션에서 **Override** 체크 박스를 선택합니다.

    1.  **Service URL** 텍스트 상자에서 현재 값에 **http://httpapi*[yourname]*.azurewebsites.net/headers** 값을 추가합니다.

        > **참고**: 예를 들어 현재 값이 **http://httpapi*[yourname]*.azurewebsites.net** 인 경우 새 값은 **http://httpapi*[yourname]*.azurewebsites.net/headers**입니다.

    1.  **Save**을 선택합니다.

1.	**Design** 탭으로 돌아가 작업 목록에서 **Echo Headers**를 선택합니다.

1.	상단 메뉴 중 **Test** 탭에서 **Echo Headers** 작업을 선택합니다. 

1.	**Echo Header** 섹션에서 **Send**를 선택합니다.

1.	API 요청의 결과를 관찰합니다.

    > **참고**: 응답에 반영되는 요청의 일부로 전송되는 헤더가 얼마가 많은지 관찰합니다. 특히 이 작업의 일부로 만든 새 **Source** 헤더를 확인할 수 있습니다.

1.	작업 목록으로 돌아가려면 **Design** 탭을 선택합니다.

#### 작업 3: API 응답 조작

1.  **Design** 탭에서 **Add operation**을 선택합니다.

1.  **Add operation** 섹션에서 다음 작업을 합니다.
    
    1.  **Display name** 텍스트 상자에 **Get Legacy Data**를 입력합니다.
    
    1.  **Name** 텍스트 상자에 **get-legacy-data**를 입력합니다.
    
    1.  **URL** 목록에서 **GET**를 선택합니다.
    
    1.  **URL** 텍스트 상자에 **/xml**을 입력합니다.
    
    1.  **Save**을 선택합니다.

1.  **Design** 탭으로 돌아가 작업 목록에서 **Get Legacy Data**를 선택합니다.

1.	**Test** 탭에서 **Get Legacy Data** 작업을 선택합니다.   

1.	**Get Legacy Data** 섹션에서 **Send**를 선택합니다.

1.	API 요청의 결과를 관찰합니다.

    > **참고**: 이 시점에서 결과는 XML 형식이어야 합니다.

1.	**Design** 탭으로 돌아가 작업 목록에서 **Get Legacy Data**를 선택합니다.

1.  **Get Legacy Data** 작업의 **Design** 섹션에서 **Outbound processing** 타일을 찾아 **Add policy**를 선택합니다.

1.  **Add outbound policy** 섹션에서 **Other policies** 타일을 선택합니다.

1.  정책 코드 편집기에서 XML 콘텐츠의 다음 블록을 찾습니다.

    ```
    <outbound>
        <base />
    </outbound>
    ```

1.	XML의 해당 블록을 다음 XML로 바꿉니다.

    ```
    <outbound>
        <base />
        <xml-to-json kind="direct" apply="always" consider-accept-header="false" />
    </outbound>
    ```

1.  정책 코드 편집기에서 **Save**을 선택합니다.

1.  **Design** 탭으로 돌아가 작업 목록에서 **Get Legacy Data**를 선택합니다.

1.	**Test** 탭에서 **Get Legacy Data** 작업을 선택합니다.   

1.	**Get Legacy Data** 섹션에서 **Send**를 선택합니다.

1.	API 요청의 결과를 살펴봅니다.

    > **참고**: 새 결과는 JSON(JavaScript Object Notation) 형식으로 표시됩니다.

1.  **HTTP response** 섹션에서 다음 작업을 합니다.

    1.  **Trace**을 선택합니다.

    1.  **Backend** 및 **Outbound** 텍스트 상자의 콘텐츠를 살펴봅니다.

#### 검토

이 연습에서는 App Service 리소스와 쿼리를 만들려는 개발자 간에 프록시 계층을 구축했습니다.

### 연습 3: 구독 정리 

#### 작업 1: Azure Cloud Shell 열기

1.  포털에서 **Cloud Shell** 아이콘을 선택하여 새 셸 인스턴스를 엽니다.

1.  포털에서 **Cloud Shell** 명령 프롬프트에 다음 명령을 입력하고 Enter 키를 눌러 구독의 모든 리소스 그룹을 나열합니다.

    ```
    az group list
    ```

1.  다음 명령을 입력하고 Enter 키를 눌러 리소스 그룹 삭제에 사용할 수 있는 명령 목록을 살펴봅니다.

    ```
    az group delete --help
    ```

#### 작업 2: 리소스 그룹 삭제

1.  다음 명령을 입력하고 Enter 키를 눌러 **ApiService** 리소스 그룹을 삭제합니다.

    ```
    az group delete --name ApiService --no-wait --yes
    ```
    
1.  Portal에서 Cloud Shell 창을 닫습니다.

#### 작업 3: 활성 애플리케이션 닫기

-   현재 실행 중인 Microsoft Edge 애플리케이션을 닫습니다.

#### 검토

이 연습에서는 이 랩에 사용된 리소스 그룹을 제거하여 구독을 정리했습니다.
