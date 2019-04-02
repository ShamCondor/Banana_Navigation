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
