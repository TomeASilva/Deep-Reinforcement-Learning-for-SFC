
# Actor Networks Architecture
![Actor Networks Architecture](/actor_nets.png/ "Actor Networks Architechture")
# Critic Networks Architecture
![Critic Networks Architecture](/Critic_Architecture.png/ "Critic Network Architecture")
# Hyperparameters

| Hyperparemter  |  Value | 
|---|---|
| ![Sigma](http://latex.codecogs.com/gif.latex?\sigma "Actor sigma") optimizer|  SGD(learning_rate = 0.0001, momentum=0.9) |
|  ![Mu](http://latex.codecogs.com/gif.latex?\mu "Actor mu") optimizer  | SGD(learning_rate = 0.0001, momentum=0.9)  |
|Critic optimizer| SGD(learning_rate = 0.0001, momentum=0.9)  |
|Reward Discount Factor(![Mu](http://latex.codecogs.com/gif.latex?\gamma "Actor sigma"))|0.99|
|Entropy coefficient (_c_)|from 1 to 0.005|
|Gradient Norm scaling|1|
|![epsilon](http://latex.codecogs.com/gif.latex?\epsilon "epsilon")|0.2|
|Critic target number of step returns |20|
|Number episodes per batch |40|
|Actor number of gradient steps per batch |10|
|Critic number of gradient steps per batch |5|

# PPO Algorithm
![](http://latex.codecogs.com/gif.latex?L_{actor}\left(\theta\right)=\hat{\mathbb{E}}_t&space;\left[\min(r_t(\theta)&space;\widehat{A}_t,&space;clip(r_t(\theta),&space;1&space;-&space;\epsilon&space;,&space;1&space;&plus;&space;\epsilon)\widehat{A}_t)&space;\right&space;]), where ![](http://latex.codecogs.com/gif.latex?r_t(\theta)&space;=&space;\frac{\pi(a_t\mid&space;s_t;&space;\theta&space;)}{\pi(a_t&space;\mid&space;s_t;&space;\theta_{old})})


* __for__ iteration = 1, 2, ... __N__:
  * __for__ actor= 1, 2, ...__N__:
    * Run policy ![sdf](http://latex.codecogs.com/gif.latex?\pi_{\theta&space;old}) for _T_ steps
    * Compute advantages estimates ![](http://latex.codecogs.com/gif.latex?\widehat{A}_1&space;\cdots&space;\widehat{A}_T) with ![](http://latex.codecogs.com/gif.latex?{V_{\phi}}^\pi)
  * Optimize ![](http://latex.codecogs.com/gif.latex?L_{actor})  wrt ![](http://latex.codecogs.com/gif.latex?\theta) for ![](http://latex.codecogs.com/gif.latex?k_1) steps
  * Optimize ![](http://latex.codecogs.com/gif.latex?L_{critic})  wrt ![](http://latex.codecogs.com/gif.latex?\phi) for ![](http://latex.codecogs.com/gif.latex?k_2) steps
  * ![](http://latex.codecogs.com/gif.latex?\theta_{old}\leftarrow\theta)
  * ![](http://latex.codecogs.com/gif.latex?\phi_{old}\leftarrow\phi)
  