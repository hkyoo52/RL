### Q 방식에 문제점
* 실제 게임처럼 너무 많은 step이 있을때 너무 느리다.

## Q Network
![image](https://user-images.githubusercontent.com/63588046/222029244-6b8f1209-512b-406d-bfe0-8838139790ba.png)

#### Q Network 방식들
1. state, action -> Q value
2. state -> Q value1, Q value2,,,

![image](https://user-images.githubusercontent.com/63588046/222029509-1c904ced-06c9-4e12-8f9f-3b833507b3ff.png)

#### 학습 방식
![image](https://user-images.githubusercontent.com/63588046/222029695-40b8c2c6-577e-4309-b521-00854c961277.png)

![image](https://user-images.githubusercontent.com/63588046/222030539-5c3edb1b-0c63-417d-ba3f-c23a796e88a8.png)


#### 알고리즘
![image](https://user-images.githubusercontent.com/63588046/222034946-74455559-0782-4c7b-9ba4-ed768d1fb073.png)


## 구조
#### X,W
![image](https://user-images.githubusercontent.com/63588046/222035600-42cef138-370d-45c8-a91b-497a58f999c8.png)

#### loss 값 계산, output 
![image](https://user-images.githubusercontent.com/63588046/222035759-dba37bc8-8d6e-41cd-8206-f15da4297939.png)

#### 확률에 따라 다르게 움직이기
![image](https://user-images.githubusercontent.com/63588046/222035864-ca6c31ff-e971-434f-b430-735a76a4aa2a.png)


#### 학습 분
![image](https://user-images.githubusercontent.com/63588046/222035897-ca1c912e-0c8f-410b-96bd-99ce080b9561.png)
