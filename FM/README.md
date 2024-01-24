# Brief summary & Implementation of FM

기존의 SVM은 sparse한 data에 대해 좋은 성능을 내지 못하는데, 이는 interaction parameter를 w_ij라는 단일항으로써 표현하기 때문이다. FM에서는 이러한 문제를 다음과 같은 형태로 해결한다. 기존에 SVM에서 단일항으로 표현하던 w_ij를 v_i와 v_j의 도트곱으로써 factorize하여 표현하는 방식이다.

![image](https://github.com/ParkSangmin3246/2023_DSAIL_INTERNSHIP/assets/68985719/6bc9d46b-a9fe-4352-b189-a721fd702d10)

이로써 얻게 되는 결과로, 기존에는 interaction이 존재하지 않으면 w_ij가 단순히 0이었겠지만 이제는 v_i와 v_j가 특정 값을 가지고 그 곱만이 0인 상태가 된다.
그럼 v_i나 v_j는 다른 interaction을 estimate 하는데 도움을 줄 수 있어 svm의 sparsity 문제를 해소한다.

또 하나의 장점으로, FM은 Regression, Binary Classification, Ranking 등 범용성이 넓게 적용될 수 있다.

마지막으로, parameter 수에 linear time complexity를 가지는 것 역시 강점으로, 이를 수식적으로 위 논문에서는 증명한다.
![image](https://github.com/ParkSangmin3246/2023_DSAIL_INTERNSHIP/assets/68985719/74feba6b-4572-4f9b-b8a0-63866e4dea56)
