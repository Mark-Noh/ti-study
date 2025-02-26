

dns는 도메인이름으로 특정 웹사이트를 호출 시 호스팅하는 서버의 IP로 변환시켜주는 서버이다.
dns는 특정 국가가 아닌 각 국가에 분산되어 서버를 같이 운영 중.

dns 스푸핑은 bettercap 통해 이뤄지는 데 타깃을 리디렉션할 장소.
apache2 (칼리리눅스에서 제공하는 서버 이름)

스푸핑은
칼리리눅스 터미네이터에서 
bettercap -iface eht0 -caplet /root/spoof.cap
bettercap을 활성화 시켜주고
dns.spoof 커맨드를 입력
