# 네트워크 Hard Ware
- Lan Card 는 네트워크 어댑터 또는  NIC (Network InterFace Card)라고 한다.

- PC 의 버스 방식 3가지 

   ***1. PCI***

   ***2. ISA***

    ***3. EISA***
   
- 허브 란 ?
  - **멀티포트 리피터 라고 말할수있다. 멀티포트는 말 그대로 포트가 많이 붙어있다는 뜻이고 . 리피터는 들어온 데이터를 그대로 재전송 하는 의미를 가지고 있다. 즉 허브는 포트가 여러개 달린 장비이며 한포트로 들어온 데이터를 나머지 모든 포트로 뿌려주는 것이다.**
  
  - 허브는 붙어 있는 모든것들은 같은 콜리젼 도메인 안에 있다.
    ```
    콜리젼 도메인은 메세지 전송시 충돌이 일어나는 영역을 말하는것이다.
    ```
  - 허브의 한계 : 아무리 빠른 속도를 내는 허브라도 어느 한순간에는 한 PC만이 데이터를 보낼수 있게 된다.
  
  - 인텔리전트(Intelligent)허브 : NMS(네트워크 관리 시스템)을 통해서 관리가 된다.문제가 계속되는 포트를 방출 시키는 기능(isolation),분리된 포트는 허브에서 **램프**로 표시되는 기능 (Auto Partition)
  
  - 더미 허브 란?
  - 세미 더미 허브 :인텔리 전트 허브와 연결되면 인텔리전트 허브가 되고 혼자 있을떄는 더미허브가 되는 허브.

  - 스태커블 (Stakable) 허브와 단독형 허브의 차이점

    ***1. 스태커블 끼리 연결하면 훨씬 빨라지고 연결된 장비 중에 하나가 고장이 나도 다른 장비에 영향을 주지 않는다.***

    ***2. 스태커블 허브는 마치 한 대의 장비처럼 관리 할 수 있다.***

    ***3. 단독형은 이러한 스태커블 허브의 특징이 없다.***
- 스위치 란?
  - 허브와의 차이점: **1,2번 포트가 통신이 일어나도 3.4 포트에서 통신이 가능하다. 또한 속도가 빠르고 데이터 처리 방법이 우수 하며 데이터의 전송 에러등을 복구 해주는 기능이 있다.**
  
  - 스위치 와 허브의 사용여부는 네트워크 의 트래픽이나 용도에 따라 달라지긴 하지만 요즘은 스위치의 가격이 많이 내려서 허브대신 스위치를 사용하는 추세이다.

- 브리지 란?
  - 브리지란 허브로 만들어진 콜리전 도메인 사이를 반으로 나누고 중간에 다리를 놓는것이다.
  - 브리지나 스위치는 콜리전 도메인을 나누어주는 기능을 한다.

- 브리지 / 스위치 의 기능
    1. Learning : 자신의 포트에 연결된 PC가 통신을 위해서 프레임을 내보내면 그때 이 PC 의 맥 어드레스를 읽어서 자신의 브리지 테이블에 저장한다.
    ***이때 브리지나 스위치가 기억할수 있는 맥 어드레스는 이 장비가 가지고 있는 메모리의 크기에 따라 달라진다.***
    
    2. Flooding : 들어온 포트를 제외한 나머지를 모든 포트에 뿌리는 것을 의미한다. 브로드캐스트나 멀티캐스트의 경우에도 발생하게된다.()
    
    3. Fowarding : 브리지가 목적지의 맥 어드레스를 자신의 브리지 테이블에 가지고 있고, 이 목적지가 출발지의 목적지와 다른 세그먼트에 존재하는 경우에 발생하게 된다.

    ***포워딩과 플로딩 차이 : 포워딩은 해당 포트로만 넘어가고 플로딩은 들어온 모든 포트를 제외한 나머지 포트로 넘어간다.***

    4. Filtering : 브리지를 못넘어가게 막는다는 것을 뜻합니다. 브리지가 목적지의 맥 어드레스를 자신의  브리지 테이블에 가지고 있고, 이 목적지가 출발지와 같은 세그먼트에 존재하는 경우 발생한다.
    
    5. Aging : 브리지 테이블 도 시간이 지나고 나면 이 정보를 테이블에서 지우게된다. 디폴트로 5분이다. Aging 이 끝나기 전에 같은 출발지를 가진 녀석이 또 브리지로 들어오게 되면 브리지는 타이머를 리셋한다.
   
- Looping 
  - 루핑이란 ?  프레임이 네트워크 상에서 무한정으로 뱅뱅 돌기 때문에 이더넷 특성상 전송이 불가능 해진 상태
  - 자동으로 루핑을 막아주는 알고리즘이 필요한데 이 알고리즘을 스패닝 트리 알고리즘 이라고 한다.
- 폴트 룰러런트(Fault Toelerant)와 로드 밸런싱 (Load Balancing)
  - 폴트 룰러런트 : 장애 대비책으로 대부분 이중구조를 의미하고 전체 네트워크가 하나의 지점에서 발생한 장애로 인해 영향을 받는것을 방지하기 위한 대책
  - 로드 밸런싱 : 회선을 두개를 사용하여 로드가 분산되는 효과를 얻을수 있으며 도한 회선 하나가 끊어지면 다른 회선으로 이전할 수있다.
- 스패닝 트리 알고리즘 (Spaning Tree Algorithem) 
  - 스위치나 브리지에서 발생할수 있는 루핑을 미리 막기위해 미리 두 개 이상의 경로가 발생하면 하나를 제외하고 나머지 경로들을 자동으로 막아두었다가 만약 기존경로에 문제가 생가면 막아놓은 경로를 풀어서 데이터를 전송하는 알고리즘
  
- 라우터
  - 라우터가 스위치 보다 필요한 이유 
    1. 브로드캐스트 영역을 나눠주기 위해서 
    2. 스위치가 보장못하는 보안기능 , 즉 패킷 필터링 기능 을 제공합니다.
    3. 로드 분배 (스위치는 제안적이다.)