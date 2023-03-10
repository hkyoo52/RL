https://talkingaboutme.tistory.com/entry/RL-Policy-Gradient-Algorithms

## Policy Gradient
* 최적의 행동 $\pi_{\theta}$를 구하고 싶음
* 가장 높은 reward를 갖게 만드는 $\theta$를 구하는게 목표

#### reward function
$$J(\theta) = \sum_{s\in S} d^{\pi}(s) V^{\pi}(s) = \sum_{s\in S} d^{\pi} \sum_{a \in A} \pi_{\theta}(a|s)Q^{\pi}(s,a)$$

* $d^{\pi}(s) : lim_{t \rightarrow \infty}P(s_{t}=s|s_{0},\pi_{\theta})$
  * $\pi_{\theta}$로 움직일때 마지막 state에서의 확률분

$$\mathbf{\nabla}_{\theta} J(\theta) = \sum_{s\in S} d^{\pi} \sum_{a \in A}Q^{\pi}(s,a)\mathbf{\nabla}_{\theta} \pi_{\theta}(a|s)$$
* d,Q는 $\theta$에 관한 함수 X
