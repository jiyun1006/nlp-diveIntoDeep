>## 기계번역 분야의 역사   
>#### 인공지능의 다른 분야에 비해 자연어 처리나 기계번역 분야는 큰 성과가 없었다.
>#### 기존의 통계 기반 기계번역 `SMT`(statistical machine translation)은 언어 간 확장이 용이했지만, 구조가 매우 복잡했다.   
>#### 이후 `seq2seq` 모델의 등장으로 `NMT`(neural machine translation)의 시대가 열렸다. (feat. attention mechanism)   

<br><br>

>## 생성 모델 학습    
>#### 기존의 단순한 분류문제(discriminator) 말고도 생성 모델 학습에 관심을 가지기 시작했다. 
>#### 타겟 레이블을 찾아내는 것 뿐만이 아닌 input데이터의 분포 자체에 집중하기 시작했다.      


- discriminator   

    <img src ="https://latex.codecogs.com/gif.latex?%5Coverset%7B%5Chat%7B%7D%7D%20%5Ctheta%20%3D%20arg%5Cunderset%7B%5Ctheta%7Dmax%20P%28Y%7CX%3B%5Ctheta%29">   

- generator   

    <img src ="https://latex.codecogs.com/gif.latex?%5Coverset%7B%5Chat%7B%7D%7D%20%5Ctheta%20%3D%20arg%5Cunderset%7B%5Ctheta%7Dmax%20P%28X%3B%5Ctheta%29">  

<br><br>

>## 자연어 처리의 패러다임

<br>

- 딥러닝 이전, 이후의 차이   

|전통적인 심볼릭 기반 접근 방법||딥러닝 기반 접근 방법|
|:------|:---|:---|
|이산적, 심볼릭 공간||연속적, 신경망 공간|
|연산 속도 느림||연산 속도 빠름|
|여러 서브 모듈이 폭포수 형태를 취함. 특징 추출에 노력이 필요||end-to-end 모델을 통한 성능 개선과 시스템 간소화|   

<br><br>


>## 자연어 처리 장애요소   

<br>

- 다양한 포현   
    `어떤 상황을 표현할 수 있는 문장은 수십 개일 수 있다. 이러한 점이 자연어 처리의 어려움을 가중 시킨다.`   

<br>
   
-  불연속적 데이터   
    - 차원의 저주   
        `불연속적인 데이터이기 때문에 많은 종류의 데이터를 표현하기위해 많은 차원이 필요하다.`   
        `현재는 적절한 embedding을 통해 차원 축소를 하여 문제를 해소할 수 있다.`   
    
    - 노이즈와 정규화   
        `단어는 불연속적인 심벌이기 때문에, 약간의 변화가 크게 다가온다.`   


<br>

- 교착어    
    `한국어는 어근에 접사가 붙어 의미와 문법적 기능이 부여되는 교착어에 속한다.`   

<br><br> 




