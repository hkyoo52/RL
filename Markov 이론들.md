### First-order Markov assumption
* 시간 t에서의 상태는 t−1에서의 상태에만 영향을 받는다

### Markov Chain (=Markov process)
* 확률 프로세스 : 확률 분포를 가진 랜덤 변수(random variable)가 일정한 시간 간격(time interval)으로 값을 발생시키는 것을 모델링
* Markov Chani : 현재의 상태가 오로지 이전 상태에만 영향을 받는 확률 프로세스
  * X : 상태공간의 집합
  * P : 전이 확률, 

![image](https://user-images.githubusercontent.com/63588046/223064354-37bcec64-e5d1-49fc-9ee9-c74a7c3b75c4.png)

### Markov Property
![image](https://user-images.githubusercontent.com/63588046/223064642-84ee1a25-bc14-4b10-937f-ed1400680fa9.png)
* 상태 i를 방문했을 때, 그 이전에 어떤 상태에 방문했는지 상관 없이 상태 i에서의 다음 상태 j로의 전이 확률 값은 언제나 동일

#### n-step 전이확률
* 현재 상태
![image](https://user-images.githubusercontent.com/63588046/223066238-2da71ec8-3c21-43ff-b131-753d323982b1.png)

* 베이지룰 적용 (n-step 전이확률)
![image](https://user-images.githubusercontent.com/63588046/223066386-6694067b-fccb-486f-9a1f-1d8f64af2fee.png)


### Markov reward process
  * S : state
  * P : $p(s'|s) = Pr(S_{t+1} = s'| S_{t} = s)\$   
      * s에서 s'으로 이동할 확률
  * R : $r(s) = E[R_{t+1}|S_{t}=s]\$    
      * state s에서 얻는 reward
  * r : 할인율 

![image](https://user-images.githubusercontent.com/63588046/223590620-6e0fff0d-36bd-4a4c-a996-f548088879d5.png)


#### Return
* $G_{t}\$는 시간 t 이후부터 얻을 수 있는 reward의 합
* $G_{t} = R_{t+1} + rR_{t+2} + ...=\sum\limits_{k=0}^\infty r^{k}R_{t+k+1}$
  * Ex. r=0.5, $S_{1}$ = Room1이고 Room1, Room2, Outside로 이동할 경우 
  * $G_{1} = -1 + (-2) \times 0.5 + 1 \times 0.5^{2}$ 

#### State-value fumction
* $v(s)$는 state s에서 시작할 때 얻을 수 있는 return의 기댓값
* $v(s) = E[G_{t}|S_{t} = s]$
* $v(s) = E[R_{t+1} + rR_{t+2} + ...|S_{t}=s] = E[R_{t+1}+rv(S_{t+1}|S_{t}=s]$
* $v(s) = R_{t+1}+r\sum\limits_{s' \in S}p(s'|s)v(s')$
  ![image](https://user-images.githubusercontent.com/63588046/223594422-d6a4451c-fe3c-4ba1-b3da-78dccfb57751.png)


### Markov decision process (MDP)
* Markov reward process + action
* action : $\Pi(a|s) = Pr(A_{t}=a|S_{t}=s)$
* $p_{\Pi}(s'|s) = \sum\limits_{a\in A}\Pi(a|s)p(s'|s,a)$
* $r_{\Pi}(s) = \sum\limits_{a\in A}\Pi(a|s)r(s,a)$
