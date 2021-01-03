# STP 순서 정하기
**꼭 외워야 함**
  - 1.누가 더 작은 ROOT BID 를 가지는가?
  - 2.루트 브리지까지의 Path Costs 값은 누가 더 작은가?
  - 3.누구의 BID (Sensor Bid)가 더 낮은가?
  - 4.누구의 Port ID 가 더 낮은가?

브리지는 스패닝 트리 정보를 자기들끼리 주고 받기 위해서 특수한 프레임 을 사용하는데,이를 "BPDU(Bridge Protocol Data Unit)" 이라고 한다.

**BPDU 에는 루트브리지의 BID (Root BID),루트 브리지 까지 가는 경로값인 Root Path Cost, 보내는 브리지의 BID 인 Sender BID, 그리고 어떤 포트에서 보냈는지 알수있는 Port ID 등 정보가 실려있다.**

스위치 (브릿지) 가 부팅을 하게 되면 BPDU 를 매 2초마다 내보내면서 서로의 스패닝 트리 정보를 주고 받게 됩니다. 즉 브리지는 이 BPDU 를 주고 받으면서 누가 루트 브리지고 어떤 포트가 루트포트가 될지 정하게 된다.

SenDer BID 값을 비교해서 루트 브리지 선출.

Path Code 비교해서 데지네이티드 포트 선출.

