# DNS

## DNS란 무엇인가 ?

<br />

![https://www.seobility.net/de/wiki/DNS-Server](https://www.seobility.net/de/wiki/images/d/d0/DNS-Server.png)

**DNS란,** 도메인 이름 시스템(Domain Name System)으로
<br />
사람이 읽을 수 있는 도메인 이름(예: www.amazon.com)을 머신이 읽을 수 있는 IP 주소(예: 192.0.2.44)로 변환하는 것
<br />
<br />

www.google.com과 같이 사람이 기억하기 쉬운 도메인 이름은 인터넷을 통한 컴퓨터 간의 통신에 적합하지 않다.
<br />

따라서 컴퓨터와 다른 장치가 인터넷이나 다른 네트워크를 통해 서로 통신하기 위해 각 장치에는 고유한 **IP주소**가 할당된다.
<br />

긴 전화번호와 마찬가지로 이 웹사이트의 IP는 사람들이 기억하기 어려우므로 DNS는 <span style="color: #2d3748; background-color: #fff5b1">**사용자가 웹사이트의 IP주소를 알 필요 없이 웹사이트에 대한 연결을 가능**</span>하게 한다.
<br />
<br />
<br />

---

<br />

## DNS 서버 요구사항

DNS서버는 인터넷 초기에 구현되었을 때와 마찬가지로 오늘날에도 같은 방식으로 작동하기 때문에, 일반적으로 수신 및 저장하는 정보와 데이터가 올바른지 또는 합법적인 소스에서 왔는지 확인하지 않는다.

<br />

오늘날 해커는 이러한 검증 부족으로 가짜 데이터를 주입하거나 기밀 정보를 얻거나 DNS 스푸핑, 캐시 포이즈닝 또는 Man-In-Middle-Attack(MITM)과 같은 공격 방법을 사용하여 위조 데이터를 주입하거나 기밀 정보에 액세스하거나 사용자를 다른 서버로 리디렉션한다.
이러한 이유로 **DNS 서버에 대한 보안 요구 사항이 크게 증가**했다.

<br />

**_DNSSEC(Domain Name System Security Extensions)_**와 같은 보안 조치를 통해 공용 키를 사용하여 암호화 해서 DNS 서버의 보안을 강화할 수 있다.

<br />
<br />
<br />

---

<br />

### 함께 보면 좋은 자료

[🔗 aws : What is DNS?](https://youtu.be/e2xLV7pCOLI)

[🔗 YouTube 생활코딩 : DNS record & CNAME](https://www.youtube.com/watch?v=N_T_vhUsn1A)

### Reference

[🔗 aws : DNS란 무엇입니까?](https://aws.amazon.com/ko/route53/what-is-dns/)

[🔗 seobility wiki : DNS-Server](https://www.seobility.net/de/wiki/DNS-Server)
