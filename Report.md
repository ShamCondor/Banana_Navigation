# Report
In this project, the following 5 deep reinforcement learning algorithms have been implemented to solve the navigation problem.
+ DQN
+ Double DQN
+ Prioritized Experience Replay DQN
+ Dueling DQN
+ Mini Rainbow DQN(Double DQN + Prioritized Experience Replay DQN + Dueling DQN)
This report will describe all those learning algorithm, along with the model architectures for neural networks and the chosen hyperparameters.
## DQN
### Neural Network Architecture
+ Input Layer: 37
+ Hidden Layer 1: 256
+ Hidden Layer 2: 128
+ Hidden Layer 3: 64
+ Hidden Layer 4: 32
+ Output Layer: 4
```
DQNetwork(
  (hidden_layers): ModuleList(
    (0): Linear(in_features=37, out_features=256, bias=True)
    (1): Linear(in_features=256, out_features=128, bias=True)
    (2): Linear(in_features=128, out_features=64, bias=True)
    (3): Linear(in_features=64, out_features=32, bias=True)
  )
  (output): Linear(in_features=32, out_features=4, bias=True)
)
```
### Hyper-parameters
+ Replay Memory Size = 2e4
+ Batch Size = 128
+ GAMMA = 0.99
+ TAU = 1e-2
+ LR = 1e-3
+ Target Network Update Interval = 16
### Plot of Rewards
![DQN](https://github.com/ShamCondor/Banana_Navigation/blob/master/picture/DQNetwork.png)

DQN solved the problem in 166 episodes.

## Double DQN
### Neural Network Architecture
+ Input Layer: 37
+ Hidden Layer 1: 256
+ Hidden Layer 2: 128
+ Hidden Layer 3: 64
+ Hidden Layer 4: 32
+ Output Layer: 4
```
DoubleDQNetwork(
  (hidden_layers): ModuleList(
    (0): Linear(in_features=37, out_features=256, bias=True)
    (1): Linear(in_features=256, out_features=128, bias=True)
    (2): Linear(in_features=128, out_features=64, bias=True)
    (3): Linear(in_features=64, out_features=32, bias=True)
  )
  (output): Linear(in_features=32, out_features=4, bias=True)
)
```
### Hyper-parameters
+ Replay Memory Size = 2e4
+ Batch Size = 128
+ GAMMA = 0.99
+ TAU = 1e-2
+ LR = 1e-3
+ Target Network Update Interval = 16
### Plot of Rewards
![DQN](https://github.com/ShamCondor/Banana_Navigation/blob/master/picture/DoubleCQNetwork.png)

Double DQN solved the problem in 200 episodes.

## Prioritized Replay Memory DQN
### Neural Network Architecture
+ Input Layer: 37
+ Hidden Layer 1: 256
+ Hidden Layer 2: 128
+ Hidden Layer 3: 64
+ Hidden Layer 4: 32
+ Output Layer: 4
```
PERDQNetwork(
  (hidden_layers): ModuleList(
    (0): Linear(in_features=37, out_features=256, bias=True)
    (1): Linear(in_features=256, out_features=128, bias=True)
    (2): Linear(in_features=128, out_features=64, bias=True)
    (3): Linear(in_features=64, out_features=32, bias=True)
  )
  (output): Linear(in_features=32, out_features=4, bias=True)
)
```
### Hyper-parameters
+ Replay Memory Size = 2e4
+ Batch Size = 128
+ GAMMA = 0.99
+ TAU = 1e-2
+ LR = 1e-3
+ Target Network Update Interval = 16
### Plot of Rewards
![DQN](https://github.com/ShamCondor/Banana_Navigation/blob/master/picture/PDQNetwork.png)

Prioritized Replay Memory DQN solved the problem in 285 episodes.

## Dueling DQN
### Neural Network Architecture
+ Input Layer: 37
+ Hidden Layer 1: 256
+ Hidden Layer 2: 128
+ Hidden Layer 3: 64
+ Hidden Layer 4: 32
+ Output Layer: 4
```
PERDQNetwork(
  (hidden_layers): ModuleList(
    (0): Linear(in_features=37, out_features=256, bias=True)
    (1): Linear(in_features=256, out_features=128, bias=True)
    (2): Linear(in_features=128, out_features=64, bias=True)
    (3): Linear(in_features=64, out_features=32, bias=True)
  )
  (output): Linear(in_features=32, out_features=4, bias=True)
)
```
### Hyper-parameters
+ Replay Memory Size = 2e4
+ Batch Size = 128
+ GAMMA = 0.99
+ TAU = 1e-2
+ LR = 1e-3
+ Target Network Update Interval = 16
### Plot of Rewards
![DQN](https://github.com/ShamCondor/Banana_Navigation/blob/master/picture/DuelingQNetwork.png)

Dueling DQN solved the problem in 207 episodes.

## Mini Rainbow DQN
### Neural Network Architecture
+ Input Layer: 37
+ Hidden Layer 1: 256
+ Hidden Layer 2: 128
+ Hidden Layer 3: 64
+ Hidden Layer 4: 32
+ Output Layer: 4
```
PERDQNetwork(
  (hidden_layers): ModuleList(
    (0): Linear(in_features=37, out_features=256, bias=True)
    (1): Linear(in_features=256, out_features=128, bias=True)
    (2): Linear(in_features=128, out_features=64, bias=True)
    (3): Linear(in_features=64, out_features=32, bias=True)
  )
  (output): Linear(in_features=32, out_features=4, bias=True)
)
```
### Hyper-parameters
+ Replay Memory Size = 2e4
+ Batch Size = 128
+ GAMMA = 0.99
+ TAU = 1e-2
+ LR = 1e-3
+ Target Network Update Interval = 16
### Plot of Rewards
![DQN](https://github.com/ShamCondor/Banana_Navigation/blob/master/picture/RainbowNetwork.png)

Mini Rainbow DQN solved the problem in 213 episodes.

## Preformance Comparison
It seems all the improved DQN algorithm have no advantange on training time compare with the vanilla DQN. They all solve the probem in around 210 episodes. But when we consider about robustness for each DQN algorithm, dueling DQN methods seems more stable than other DQN. The following table show the variance of scores in the last 100 run for each method.
We can also found that the combined method(Mini Rainbow DQN) has less variance(2nd) and run less episodes(1st) to solve the problem than other methods with the same set of hyper parameters.we can find DQN agent are more likely to "look around" and get stucked at the end, while Mini Rainbow DQN shows more smooth and stable behaviour when collection bananas.

| Algorithm | Solved at episodes | Last 100 run Score Variance |
|:-----|:----:|:----:|
|DQN|166|3.87|
|Double DQN|200|3.94|
|PER DQN|285|3.99|
|Dueling DQN|207|3.74|
|Mini Rainbow DQN|213|3.72|
## Future Improvement
+ Fine tuning hyper parameters to get better performance
+ Policy gradient method
