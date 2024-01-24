# Brief summary of WD & Implentation

Recommender system에서 목표 중 하나는 memorization과 generalization을 함께 달성하는 것이다.
Memorization은 기존의 historical data의 frequent co-occurrence를 가지고 correlation을 모색한다. 다만 이 접근은 unseen data에 대해선 취약할 수 있다.
Generalization은 latent vector embedding으로 unseen data를 예측하는데 능하다. 그러나 이 방식은 sparse한 data에 대해 over-generalizae할 수 있다.

이 논문에서는 Memoriazation과 Generalization을 접목시켜 상호보완하는 접근을 목표로 한다.

Wide part는 Memoriazation 역할을 담당한다. 기존의 feature vector들 뿐 아니라 그것들끼리 cross product를 진행하여 새로운 feature 역시 생성하여 linear model의 generalized version을 실행한다. 

![image](https://github.com/ParkSangmin3246/2023_DSAIL_INTERNSHIP/assets/68985719/de0e6a16-a1a1-460d-9e8b-62dc8f024f89)

![image](https://github.com/ParkSangmin3246/2023_DSAIL_INTERNSHIP/assets/68985719/54de2b00-4fcb-4249-ae35-18fdae4e9161)


Deep part는 Generalization 역할을 담당한다. categorical feature는 저차원으로 임베딩하고, 이후 Continuous feature와 Concatenate하여서 Layer에Feeding 함으로써 feed-forward neural network를 실행한다.

![image](https://github.com/ParkSangmin3246/2023_DSAIL_INTERNSHIP/assets/68985719/283795be-63ca-4812-ac80-8aa56f542e31)

![image](https://github.com/ParkSangmin3246/2023_DSAIL_INTERNSHIP/assets/68985719/2177b121-7cbd-4d13-b191-fe20d30282e2)


Training 동안, wide component와 deep component는 weighted sum 형태로 combine 되어 sigmoid function에 들어가게 된다. 

![image](https://github.com/ParkSangmin3246/2023_DSAIL_INTERNSHIP/assets/68985719/3b02cfa7-c1a4-493d-bb08-cc85144b1e09)

주의할 점은 앙상블과는 그 절차가 분명히 다르다는 점이다. 앙상블은 각 모델을 개별적으로 돌리다가 이후 inference단계에서 combine되지만, wide deep model 경우에는 train 과 optimize단계가 wide part 와 deep part에 대해 함께 적용된다는 점에 유의해야한다. 즉, back propagation이 동시에 적용된다.

이러한 구조를 이용하여 WideAndDeep은 memorization과 generalization을 병행하면서 성능을 향상시켰다.
