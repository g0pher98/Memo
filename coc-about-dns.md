# 팀장님이 내주신 과제 : DNS편
## 과제내용
```
DNS 심화과제 (2020-03-07 ~)
	1. DNS 동작방식 2가지
	2. 역DNS 왜 사용하는지
	3. 애니캐스트 작동방식
	4. 러시아나 중국이 자체 DNS를 운용하면 벌어지는 일
```
## DNS란
DNS(Domain Name System)는 도메인을 IP로 변환해주거나 IP를 도메인으로 변환해주는 서비스를 말한다. 보통 PC는 DHCP로 IP를 할당받을 때 DHCP Option6으로 도메인을 받아 설정한다.

## DNS 동작방식 (Recursive Query)
- 브라우저 -> Local DNS 질의 (PC에 파일로 저장되어있음.)
- Local DNS -> Root DNS 질의
- Local DNS -> .com 도메인 관리 서버 (Top-level Domain Name : TLD)
- Local DNS -> naver.com 도메인 관리 서버 (Second-level Domain Name : SLD)
- Local DNS 캐싱
- Local DNS -> 브라우저

# Reverse DNS
보통 메일의 스팸여부를 판단하는데 많이 쓰이는듯 하다.  
`nslookup -type=ptr 메일서버ip`  
위 명령으로 IP에 대한 도메인을 역으로 요청할 수 있다.

## 러시아나 중국이 자체 DNS를 운용하면 벌어지는 일
러시아나 중국이 자체 DNS를 운용하게 되면 해당 DNS를 이용하는 사용자(대다수 국민)이 어떤 사이트에 접속을 요청하는지 알 수 있다. 이 경우 DNS서버 설정을 믿을 수 있는 DNS서버로 직접 변경하여 이용하면 해결될 것이다.

## 참고
https://www.netmanias.com/ko/post/blog/5353/dns/dns-basic-operation