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


### 기본 구조
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

### 예시
* https://www.youtube.com/watch?v=yOBKtGU6CG0&list=PLlMkM4tgfjnKsCWav-Z2F-MMFRx-2gMGG&index=5

## Exploit vs Exploration
* Exploit : 현재 있는 값으로 이동
* Exploration : 새로운 길 탐험

![image](https://user-images.githubusercontent.com/63588046/221913385-6d9ef7bd-19c0-40b2-a1f3-8ca8155b01d9.png)


### E-greedy
* 일정 확률로 랜덤하게 이동
#### 기본 구조
```python
e = 0.1
# 10% 확률로는 랜덤하게 이동해라
if rand<e:
    a = random
# 90% 확률로는 최적값으로 이동해라
else:
    a = argmax(Q(s,a))
```
### decaying E-greedy
* 학습 할수록 더 랜덤하게 이동할 확률을 낮춘
#### 기본 구조
for i in range(1000):
    e = 0.1/(i/100+1)
    while not done:
        if np.random.rand(1)<e:
          action = env.random_space.sample()
        else:
          action = np.argmax(Q[state,:])

### add random noise
* 각각에 Q 값에 랜덤하게 값을 부가한 후 가장 높은 값으로 이동
* 이렇게 함으로써 가끔씩 2,3 번째로 큰 값이 가장 큰 값으로 되서 그 방향으로 이동하게 됨

#### 기본 구조
for i in range(1000):
    action = np.argmax(Q[state,:]) + np.random.randn(1,env.action_space.n)/(i+1) 

## discounted reward
* 거리가 긴 방식보다 짧은 방식이 더 좋음 -> discounted reward
* 미래에 받는 보상을 현재가치로 줄여서 받음
#### 기본 구조
* Q(s,a) <- reward + b * max Q(s',a')  b:보상

#### 예시
![image](https://user-images.githubusercontent.com/63588046/221918119-252c2d20-d8ac-4c02-b1fc-9e0956d9b164.png)


## 수식 
![image](https://user-images.githubusercontent.com/63588046/221915886-b1fec45d-94bd-4263-bed6-d6e686f9dbfd.png)
![image](https://user-images.githubusercontent.com/63588046/221916632-254cb752-ce32-437e-a23d-e59e0024ba3e.png)


## 기호
Q' : 확실하지 않는 값, 학습할수록 Q에 근접함
Q : 확실한 값

