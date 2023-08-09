Brief summary of PMF and its implementation

R을 latent feature vector를 이용하여 User matrix (U) 와 Item matrix (V)로 분해하는 것은 기존의 basic matrix factorization 방식과 동일하다.
다만 여기에서 이제 R을 estimate 하는데 있어 conditional probability를 이용한다. 
U와 T의 곱이 mean인 gaussian distribution이 주어질 때 R의 확률을 통해 접근.
또한 User 와 Item feature vector의 prior 에 대해 mean이 0인 spherical gaussian prior로 가정한다.
그리하여 map 방식으로 접근하고, negative logarithm으로 loss function을 도출하고 이를 optimize한다.

Constrained PMF라는 variation도 소개된다. 
ratings을 많이 남기지 않은 user에 대해 이와 같은 기법을 적용시킨다.
같은 영화를 많이 본 user들은 그 (user feature vector) prior도 비슷할 것이라는 가정을 하여 User feature vector 수식을 조금 변형한다.
위와 같은 방식으로 기존의 MF에서 보다 확률적인 시각으로 접근한 방식이 이 PMF이다.
