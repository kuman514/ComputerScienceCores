# 보안 모음집

## XSS (Cross Site Scripting)
- HTML 코드에 `<script>` 태그를 삽입하는 방법을 이용한 공격 방법.
  - Text input이 있으며 해당 데이터가 POST/PUT/PATCH로 보내질 때, 해당 데이터가 innerHTML을 통해 삽입된다면, `<script>` 태그가 삽입되어 중요한 정보를 탈취당하는 등의 공격을 받을 위험이 있다.
- 이를 예방하려면, HTML 태그를 Sanitizing 처리해야 한다.

## SQL Injection
- SQL 질의에 임의의 질의문을 삽입하여 데이터베이스로부터 정보를 탈취하는 공격 방법.
  - 예시: `' or 1 = 1`같은 임의의 질의문을 삽입.
- 이를 예방하려면, SQL 질의 문자열에 직접 값을 넣는 것이 아닌, 플레이스홀더를 이용한 동적인 값을 넣는 방법 등을 취해야 한다.
  - ORM(Object Relational Mapping) 등등으로 SQL 문법 대신 개발하고 있는 언어를 그대로 사용하게 만드는 방법도 좋다.

## MITM (Man In The Middle) 공격

## CSRF (Cross Site Request Forgery) 공격

## JWT (JSON Web Token)
- JWT란
  - 사용자 인증에 필요한 정보를 담은 JSON을 Base64 URL-safe Encode로 인코딩하여 직렬화한 JSON 토큰.
  - JWT 기반 인증은 HTTP 헤더에 토큰을 실어 서버가 클라이언트를 식별하는 방식의 인증이다.
- JWT의 구조 (`.`으로 구분)
  - JWT 예시
    - `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOnRydWUsImlhdCI6MTUxNjIzOTAyMn0.KMUFsIDTnFmyG3nMiGM6H9FNFUROf3wh7SmqJp-QV30`
    - 혜더: `{ "alg": "HS256", "typ": "JWT" }`
    - 내용: `{ "sub": "1234567890", "name": "John Doe", "admin": true, "iat": 1516239022 }`
    - 서명: (HS256 기준) `HMACSHA256(base64url(header) + "." + base64url(payload), secret_key)`의 결과값
  - 헤더: 서명 암호화 알고리즘(`alg`)과 토큰 타입(`typ`)을 명시한다.
  - 내용: 토큰에 담고 싶은 데이터를 JSON 형태로 담는다.
  - 서명: `헤더.내용`을 비밀키로 서명한 값이다. 서버는 이 서명을 검증하여 토큰이 변조되었는지 확인한다.
- 액세스 토큰 (Access Token)
  - API 요청 인가 등, 서비스 접근에 필요한 토큰.
  - 탈취되었을 경우 보안에 위협이 되므로, 만료 주기를 (몇 분에서 1시간 정도로) 짧게 설정한다.
- 리프레시 토큰 (Refresh Token)
  - 액세스 토큰이 만료되었을 때 새로 발급할 수 있는 용도로 사용되는 토큰.
  - 만료 주기를 (며칠에서 몇 주 정도로) 길게 설정한다.
  - 왜 필요한가?
    - 만료 주기가 짧은 액세스 토큰만 사용할 경우 재로그인을 빈번하게 해야 하는 불편함이 발생한다.
    - 그래서, 액세스 토큰의 짧은 주기가 가져오는 보안상 이점을 챙기면서도, 재로그인의 불편함을 방지해주는 수단이 필요한데, 이게 긴 주기로 재발급의 기회를 주는 리프레시 토큰을 사용하는 이유다.
