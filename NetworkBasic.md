## OSI 계층 구조
![OSI_계층구조](https://user-images.githubusercontent.com/94053008/223013555-203274fc-ffb7-47d1-b8fa-7f401e2527f9.png)


Link: http://wiki.hash.kr/index.php/응용계층

## L7 응용 계층
+ 실제 네트워크 애플리케이션(프로세스)들이 다루는 영역
+ 이용자의 적용 업무를 처리하는데 필요한 모든 기능을 이용자측에서 정의하고. 처리하는 부분
+ 대표적인 프로토콜
   - HTTP, DHCP, SMTP, FTP
   - DNS

<img width="641" alt="image" src="https://user-images.githubusercontent.com/94053008/223012076-9686c33a-cec9-4e9a-bfc0-3755a1342e19.png">

## DNS (Domain Name System)
 + 일종의 주소록
 + 분산 DB
   - 도메인 이름, IP 등을 서비스


### 지원하는 기능 - 레코드 타입
 + A: 도메인에 대한 IP 응답
 + NS: 특정 도메인의 Name Server 정보 응답
 + CNAME: canonical name 설정
 + MX: 도메인의 메일 수신 서버 주소를 응답
 + TXT: 임의 문자열 부가 정보 관리, SPF, DKIM 용으로도 사용
 + SRV: IP 외에 Port 번호까지 서비스 가능


### DNS QUERY FLOW
<img width="596" alt="image-1" src="https://user-images.githubusercontent.com/94053008/223012978-cbf27374-6c6c-4d95-aa5c-bfe59d9c778d.png">

 + Local DNS에 캐싱이 되어 있는 경우는 바로 응답
 + 캐싱이 되어 있지 않은 경우에는 Root, TLD, Authoratative DNS 순서에 질의하여 결과 응답

