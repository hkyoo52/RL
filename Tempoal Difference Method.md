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
* MC는 true value를 바탕으로 reward를 구하지만 TD는 다음 step을 value로 reward를 구하므로 정확하지 않을 수 있음(bias가 높음)


## n-step TD
* 한 step 할때마다 업데이트 하는 것이 아니라 n개에 step을 갈때마다 업데이트 함
  * 만약 n = Total step  $\rightarrow$ MC
* $G_{t}^{(n)} = R_{t+1} + rR_{t+2}+...+r^{n-1}R_{t+n}+r^{(n)}V(S_{t+n})$
* $V_{(S_{t})} \leftarrow V(S_{t})+a(G_{t}^{(n)}-V(S_{t}))$


## TD($\lambda$)
* n-step TD는 어떤 n을 선택하냐에 문제가 있다.
* 여러 n-step을 구해서 평균을 취하자
* 이때 평균은 산술평균이 아닌 geometrically weighted average이다.
* $G_{t}^{\lambda} = (1-\lambda) \displaystyle\sum_{n=1}^{\infty} \lambda^{n-1}G_{t}^{(n)}$
* $V_{(S_{t})} \leftarrow V(S_{t})+a(G_{\lambda}^{(n)}-V(S_{t}))$
