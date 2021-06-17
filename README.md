## Catpole 환경에서 DQN 및 DDQN, Dueling network 적용 
+ source code -  ipynb (colab) 

### Cartpole 환경 설명 

CartPole-v1 환경은 이름 그대로 어떤 Cart에 Pole이 연결되어 있습니다. 위의 그림에서 보라색 사각형은 피벗 포인트를 나타냅니다. 빨간색 및 녹색은 이 피벗 포인트에 적용될 수 있는 수평적 힘을 나타냅니다. Agent의 목표는 Cart를 왼쪽 오른쪽으로 힘을 주면서, 최대한 쓰러트리지 않고 평형을 유지하는게 목표입니다.  

밑의 자료는 MDP 정의를 위한 , Action, reward , state들을 요약 정리한 자료입니다. 


 Source:
        This environment corresponds to the version of the cart-pole problem
        described by Barto, Sutton, and Anderson
        
    Observation:
        Type: Box(4)
        Num     Observation               Min                     Max
        0       Cart Position             -4.8                    4.8
        1       Cart Velocity             -Inf                    Inf
        2       Pole Angle                -0.418 rad (-24 deg)    0.418 rad (24 deg)
        3       Pole Angular Velocity     -Inf                    Inf
        
    Actions:
        Type: Discrete(2)
        Num   Action
        0     Push cart to the left
        1     Push cart to the right
        Note: The amount the velocity that is reduced or increased is not
        fixed; it depends on the angle the pole is pointing. This is because
        the center of gravity of the pole increases the amount of energy needed
        to move the cart underneath it
        
    Reward:
        Reward is 1 for every step taken, including the termination step
  
  
    Starting State:
        All observations are assigned a uniform random value in [-0.05..0.05]
        
    Episode Termination:
        Pole Angle is more than 12 degrees.
        Cart Position is more than 2.4 (center of the cart reaches the edge of
        the display).
        Episode length is greater than 200.
        Solved Requirements:
        Considered solved when the average return is greater than or equal to
        195.0 over 100 consecutive trials.
        
 ## Result 
알고리즘 별 비교 시각화¶
일반적인 DQN에 비해서 다른 알고리즘들을 적용했을 때, 드라마틱 하게 달라지는 결과는 관찰되지 못했습니다. 이유는 카트폴 환경이 action이 2가지 밖에 없는 비교적 단순한 환경이기 때문일 것이라 생각됩니다.

모델의 실질적인 성능의 비교는 무의미 할 정도로 비슷합니다.\ 세가지 알고리즘 모두 성능이 우수한 것을 확인할 수 있고 다만 관찰되는 알고리즘 별 특징은 다음과 같습니다.

+ DQN은 우선 편차가 매우 심합니다. 주황색 선을 보면 급격하게 낮아졌다가 높아지는 구간을 많이 관찰할 수 있습니다.
+ 이에 비해 DDQN은 편차의 폭이 조금 줄은 것을 확인 할 수 있습니다.
+ DDQN-Dueling network은 대체로 큰 편차 없이 서서히 우 상향하는 그림을 보여줍니다.

Cartpole v0 환경기준 195점을 세 알고리즘 모두 다 episode 초반부에서 모두 넘어 버렸습니다(max 200) 그렇기 때문에 Cartpole v1 환경을 다시 돌렸습니다(동일한 환경이지만 max 500까지 갈수 있습니다). Cartpole v1 기준의 max값인 500을 DDQN-Dueling network, DQN는 도달한 결과를 관찰 할 수 있습니다.


 <img src="https://github.com/bongseokkim/DQN-DDQN-Cartpole-/blob/main/image/Comparing_result.png"  width="50%">
 
 
 ## DQN 
 <img src="https://github.com/bongseokkim/DQN-DDQN-Cartpole-/blob/main/image/DQN.png"  width="50%">
 
 ### DDQN
  <img src="https://github.com/bongseokkim/DQN-DDQN-Cartpole-/blob/main/image/DDQN.png"  width="50%">
 
 ### DDQN with Dueling network 
  <img src="https://github.com/bongseokkim/DQN-DDQN-Cartpole-/blob/main/image/DDQN_Dueling_network.png"  width="50%">
 
 
 
