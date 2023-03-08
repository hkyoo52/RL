## MC (Monte-Carlo)
* model free 방식
* raw experience를 통해 learning
* 한 episode 끝난 후에 얻은 return 값으로 각 state에서 얻은 reward를 시간에따라 discount하는 방식
* 실제 세계에서는 episode의 끝이 무한대에 가깝게 기므로 한 episode가 끝나야 값을 얻는 방식은 한계가 있음

## TD Method (temporal difference)
* model free
* raw experience를 통해 learning
* 각 time step이 끝날때마다 업데이트 (episode의 끝을 기다리지 않고 업데이트)
  * $V(S_{t}) \leftarrow V(S_{t}) + a(G_{t}-V(S_{t}))$
  * $V(S_{t}) \leftarrow V(S_{t}) + a(R_{t+1}+rV(S_{t+1})-V(S_{t}))$
  * 
