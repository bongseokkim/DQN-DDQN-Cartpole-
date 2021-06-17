## Catpole 환경에서 DQN 및 DDQN, Dueling network 적용 



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
