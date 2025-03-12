네트워크 해킹은 arp해킹
즉 arp가 ip주소만 알고 서로 통신할 경우 맥주소를 요청하는 방식을 이용해서
클라이언트와 라우터 사이에 내가 중간에서 패킷을 가로채는 방식임.
해당 방법은 bettercap -iface eth0 -caplet /root/spoof.cap 를 리눅스 터미널에서 커맨드
이후 대상 클라이언트에 cmd에서 arp-a를 커맨드하면 xx.xx.xx.1 의 맥주소가 내 eth0 맥주소로 변경되어 있음.
xx.xx.xx.1.은 대게 클라이언트가 서버에 접속하기 위해 라우터와 연결하는 포트임.
xarp를 설치, 실행하며면 맥주소가 임의로 변경됨을 나타냄. 

wireshark로 의심스러운 해킹을 찾는 방법.
wiresharks의 configuration profiles를 들어간다.
preferences 창 좌측에  protocols의 arp를 들어간다.
해당 창에 detect arp request storms 박스를 클릭
해당 네트워크 내 모든 기기를 검색하려하면 경보를 알려준다.

arp 검색을 가정해서
칼리 터미네이터에 netdiscover를 커맨드
netdiscover -i eth0(인터페이스) -r 10.20.14.1/24(범위, 네트워크내 모든 기기 확인은 ip 마지막에 1/24로 설정)

그러고 난 뒤 wireshark에 상단 analyze 창의 expert information에 들어가면 arp패킷 폭주를 확인할 수 있다.
다른 방법은 윈도우 CMD에서 arp -a를 커맨드 후 type에 dynamic 된 부분으 static으로 바꾸면 arp스푸핑이 되지 않기에 방지 가능
다만 해당 부분을 수동으로 일일이 해줘야 해서 번거로움이 많다.

이를 위해 HTTPS everwhere이라는 플러그인을 설치.
https가 있는 사이트를 http로 다운그래이드시 자동으로 hsts 기능으로 https로 연결시킴.
하지만 여전히 bettercap 등을 사용하면 id, pw 같은 상세 패킷은 확인 되지 않아도 해당 ip 클라이언트가 어떤 사이트로 이동하는 지 정보는 확인됨.

vpn을 활용하면 해당 서버와 클라이언트 사이에 암호화가 되어 다운그레이드나 hijacking 당하지 않고 데이터 캡처 당하지 않는다.
하지만 vpn을 사용하면 vpn공급자가 패킷 등을 볼 수 있음.
그래서 제일 좋은 것은 vpn사용 + https everwhere를 같이 사용하면 vpn공급자도 패킷을 볼 수 없게 되어 보완가능.

 서버 공격을 해야하는 이유는 
 개인 컴퓨터를 사용하는 클라이언트에는 ip만으로는 침투가 어렵다.
 같은 네트워크 하에 있는 것이 아니기에 ip만으로 찾아가기 어려움.
 라우터 뒤에 개인이 클라이언트를 두고 있는 형태라.
 그래서 직접 서버를 공격해야 개인에 대한 해킹이 가능하다.
 
상대가 동일한 네트워크 하에 실제 ip를 가진 경우
metasploitable 머신 실행
ipconfig를 하면 해당 머신의 ip주소를 확인 가능
확인한 ip를 칼리 리눅스의 터미네이터에서 ping 해당 ip 입력
그러면 정상적인 ip라면 핑을 보내준다 
그러면 해킹을 할 수 있다.
