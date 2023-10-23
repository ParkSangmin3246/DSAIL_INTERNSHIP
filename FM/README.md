Brief summary and Implementation of FM

기존의 SVM은 sparse한 data에 대해 좋은 성능을 내지 못하여 이를 발전시키고자 제안된 기법이 FM이다.
주요한 아이디어로는 다음과 같은데, 우선 SVM에서는 interaction parameter w_ij 를 단일항으로써 표현하였다.
그러나 FM에서는 이것을 단일항으로 표현하지 않고 v_i와 v_j의 도트곱으로써 factorize하여 표현한다.
이로써 얻게 되는 결과로, 기존에는 interaction이 존재하지 않으면 w_ij가 단순히 0이었겠지만 이제는 v_i와 v_j가 특정 값을 가지고 그 곱만이 0인 상태가 된다.
그럼 v_i나 v_j는 다른 interaction을 estimate 하는데 도움을 줄 수 있어 svm의 sparsity 문제를 해소한다.
또한 parameter 수에 linear한 time complexity를 가지는 것 또한 장점으로, 이를 수식적으로 위 논문에서는 증명한다.
