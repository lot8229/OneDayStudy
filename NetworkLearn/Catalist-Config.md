# 카탈리스트 스위치 구성 
- Duplex 는 통신 방식으로 Half Duplex 와 Full Duplex 로 나누어지며 Audo 로 설정하면 상대편의 상태의 따라 내가 맞추겠다는 의미이다.

    Speed 역시 상대와 속도가 맞지 않으면 문제가 발생한다.
- IP 주소를 세팅하면 나중에 스위치 구성을 확인/변경할 떄 텔넷을 이용한 접속이 가능하기 때문에 스위치에 IP 주소를 셋팅한다.
- 네트워크 관리시스템(NMS) 같은 장비에서 스위치를 관리하는 데도 IP 주소가 필요함 
- '>' 표시 상태를 유저 모드라고 한다.
- enable 명령을 사용하여 프리빌리지 모드에서 스위치의 구성을 확인하고 변경이 가능 
  
  '>' 에서 # 로 바뀜
- 구성모드로 들어가는 명령은 configure terminal 이다.
    
    switch# 에서 Switch#(config)# 으로 바뀜
- exit 명령을 사용하여 한 단계씩 빠져나옴
- Switch#(프리빌리지 모드)  에서 show interface vlan 1을 입력하면 현재 vlan 1에 해당된 Ip 주소를 알수 있다.
  IP주소는 vlan 인터페이스 모드에서 디폴트 게이트웨이는 일반 구성모드에서 세팅 
  
  show interface 명령 - 인테페이스 의 대한 구성을 볼때
 -