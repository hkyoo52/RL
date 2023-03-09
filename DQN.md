### Q-learning 문제점
* Q-learning에서 Value Function Approximation 사용 시, Weight Update 할때 Non-stationary Target으로 인해 수렴하지 않을 가능성 있음
  * non-stationary : pred와 target이 같은 network 공유 -> pred를 최적화시킬시 target도 변
* State, Action을 Q Table로 정의하기에 많을 때 성능이 안 졷다.
  * Q Table : 각 state에 있는 Q 


### 해결 방법 -> DQN
#### Experience Replay
* Experience Replay Buffer에 stage, action, Q-Value에 대한 값들, 즉 Experience를 저장
* 저장된 Experience 중에서 mini-batch만큼 선택해서 Weight를 update함
  * 현재에 데이터보다 연관성이 적음 -> correlation 감소

#### Fixed Q-Targets
* Target Weight 고정 
* Target Update 할때 일부만 실제 Update
