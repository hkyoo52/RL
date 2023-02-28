## 아는 길도 물어보고 가라
![image](https://user-images.githubusercontent.com/63588046/221782530-92174276-f8e8-4e95-aa8b-a3c055e8e5e6.png)

* Q가 존재
* Q한테는 state와 action을 제공 => 최대의 Q가 나오는 action을 선택
* 아래 예시에서 action을 right를 선택(파이값 = right)

![image](https://user-images.githubusercontent.com/63588046/221783628-414062b6-ed19-48c4-be37-b8d10c42ed23.png)

![image](https://user-images.githubusercontent.com/63588046/221785075-a60486a3-a547-4e3c-9206-d43e681180fb.png)


## Learning Q
* 조건
  - 현재 state : s
  - a로 이동시 state : s'
  - a로 이동시 reward : r
* Q(s,a) = r + max Q(s',a') 


## 기본 구조
```python
# 4 * 4 환경, 1칸당 선택 가능 4개씩(상하좌우)
Q = np.zeros([env.observation_space.n, env.action_space.n])  # 16*4
num_episodes = 2000

# 전체 보상, 각 순간당 step 저장 리스트
rList = []
for i in range(num_episodes):
  state = env.reset()
  rAll = 0
  done = False
  whild not done:
      action = rargmax(Q[state,:]) # Q에서 가장 최대로 가는 방향
      new_state, reward, done, _ = env.step(action)
      Q[state,action] = reward + np.max(Q[new_state,:])  # Q 업데이
      state = new_state
```

## 예시
* https://www.youtube.com/watch?v=yOBKtGU6CG0&list=PLlMkM4tgfjnKsCWav-Z2F-MMFRx-2gMGG&index=5
