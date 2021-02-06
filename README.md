# NLP (pytorch)   

>## 기계번역 분야의 역사   
>#### 인공지능의 다른 분야에 비해 자연어 처리나 기계번역 분야는 큰 성과가 없었다.
>#### 기존의 통계 기반 기계번역 `SMT`(statistical machine translation)은 언어 간 확장이 용이했지만, 구조가 매우 복잡했다.   
>#### 이후 `seq2seq` 모델의 등장으로 `NMT`(neural machine translation)의 시대가 열렸다. (feat. attention mechanism)   

<br>

>## 생성 모델 학습   

- discriminator   

    <img src ="https://latex.codecogs.com/gif.latex?%5Coverset%7B%5Chat%7B%7D%7D%20%5Ctheta%20%3D%20arg%5Cunderset%7B%5Ctheta%7Dmax%20P%28Y%7CX%3B%5Ctheta%29">   

- generator   

    <img src ="https://latex.codecogs.com/gif.latex?%5Coverset%7B%5Chat%7B%7D%7D%20%5Ctheta%20%3D%20arg%5Cunderset%7B%5Ctheta%7Dmax%20P%28X%3B%5Ctheta%29">    



