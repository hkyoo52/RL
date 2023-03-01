## Deterministic VS Stochastic(nondeterministic)
* Deterministic : 모델의 output은 파라미터의 값들에 의해 결정됨
* Stochastic : 같은 파라미터값이 다른 output 

Ex. 길찾기에서 무조건 한칸씩 이동 -> deterministic, 옆으로 이동하라고 했는데 아래로 움직이기/옆으로 2칸 움직이기...도 하면 Stochastic

* 최적값으로 갈 확률 줄이고 원래 가려는 방향을 최대한 가보
![image](https://user-images.githubusercontent.com/63588046/222022357-ebcfc3e6-f27d-4dda-bdf1-7c57757283e4.png)


```python
import gym
from gym.envs.registration import register
import sys,tty,termios
import readchar

# 컴퓨터 화살표 인식 코드
class _Getch:
    def __call__(self):
        fd = sys.stdin.fileno()
        old_settings = termios.tcgetattr(fd)
        try:
            tty.setraw(sys.stdin.fileno())
            ch = sys.stdin.read(3)
        finally:
            termios.tcsetattr(fd,termios.TCSADRAIN, old_settings)
        return ch
inkey = _Getch()

Left = 0
Down = 1
Right = 2
Up = 3

arrow_keys = {
    '\xlb[A' :Up,
    '\xlb[B' :Down,
    '\xlb[C' :Right,
    '\xlb[D' :Left,
}
<!-- 
register(
    id="FrozenLake-v3",
    entry_point='gym.envs.toy_text:FrozenLakeEnv',
    kwargs={'map_name':'4*4', 'is_slippery':False}
)
 -->

env = gym.make("FrozenLake-v0")  # 여기 변경!!!
env.render()  # 초기 화면을 보여줘라

while True:
    key = inkey()
    if key not in arrow_keys.kyes():
        print('Game aborted')
        break
    action = arrow_keys[key]
    state, reward, done, info = env.step(action)

    if done:
        print("Finished with reward", reward)
        break
```
