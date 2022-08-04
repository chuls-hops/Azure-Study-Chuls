### SQL MI Private End point 테스트 
1. 192.168.0.0 대역에 SQL MI를 배포하고, Private End Point를 10.0.0.0 대역에 만든 후 
2. SSMS로 연결 테스트 해보면 일단 IP주소로는 연결이 안됨 을 알수 있었고 
3. 제공된 URL로는 접속이 잘되었다. hosts파일에 강제로 Private Endpoint 아이피를 박아서 해당 DNS가 10 망으로 트래픽이 흐르도록 셋팅한다음 연결 하니 접속이 잘됨.





