

dns는 도메인이름으로 특정 웹사이트를 호출 시 호스팅하는 서버의 IP로 변환시켜주는 서버이다.
dns는 특정 국가가 아닌 각 국가에 분산되어 서버를 같이 운영 중.

dns 스푸핑은 bettercap 통해 이뤄지는 데 타깃을 리디렉션할 장소.
apache2 (칼리리눅스에서 제공하는 서버 이름)

스푸핑은
칼리리눅스 터미네이터에서 
bettercap -iface eht0 -caplet /root/spoof.cap
bettercap을 활성화 시켜주고
help dns.spoof 커맨드를 입력
다양한 기능 설명이 나온다.
dns.spoof.address는 타겟이 리디렉션될 주소로 뒤에 default 되어 있다면 해당 ip를 넣어줘야함.
dns.spoof.all는 false로 비활성화가 기본인데 true 바꿔서 bettercap이 모든 dns요청에 응답하게 함.
옵션값을 바꾸는 커맨드는 set.dns.spoof.all. true라고 하면된다.
dns.spoof.domains는 타켓인 대상 도메인들을 입력하는 것으로 ,사용해서 여러 도메인을 넣을 수 있음.
