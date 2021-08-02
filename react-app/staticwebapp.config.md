(공급자 및 역할에 대한 액세스 구성)[https://docs.microsoft.com/ko-kr/learn/modules/publish-static-web-app-authentication/5-providers-roles]

## Azure Static Web Apps 구성파일

Azure Static Web Apps의 구성은 staticwebapp.config.json 파일에 정의되어 있으며, 이 파일은 다음 설정을 제어합니다.

라우팅
인증
권한 부여
대체(fallback) 규칙
HTTP 응답 재정의
글로벌 HTTP 헤더 정의
사용자 지정 MIME 형식
staticwebapp.config.json의 권장 위치는 배포 중에 선택한 app_location 설정으로 설정된 폴더입니다. 하지만 애플리케이션 소스 코드 폴더 내부의 모든 위치에 파일을 배치할 수 있습니다.

이 사용 사례에서는 원하는 것을 달성하기 위한 라우팅 구성을 살펴보겠습니다.

## 인증 공급자 제한

이전 섹션에서는 기본적으로 모든 인증 공급자가 사용하도록 설정되었습니다. 구성에서 라우팅 규칙을 추가하여 이를 변경할 수 있습니다.

예를 들어 GitHub 공급자를 통한 로그인을 사용하지 않으려면 staticwebapp.config.json 파일에 다음과 같은 회람 규칙을 추가할 수 있습니다.

```{.json}
{
  "routes": [
    {
      "route": "/.auth/login/github",
      "statusCode": "404"
    }
  ]
}
```

GitHub 공급자로 인증하는 데 사용되는 경로 /.auth/login/github이 404(찾을 수 없음) 오류를 반환하도록 강제 적용하면 사용자는 액세스할 수 없습니다. 경로 규칙은 원하는 만큼 추가하여 모든 원하지 않는 공급자를 사용하지 않도록 설정할 수 있습니다.
