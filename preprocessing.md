>## 분절 (segmentation) 
>#### 여러 기본 문법과 지정 문자를 이용해서 전처리에 사용한다.   

<br>


>### 정규 표현식   

<br>

- 지정 문자

|지정문자|설명|
|:---|:---|
|`\s`|공백 문자|
|`\S`|공백 문자를 제외한 모든 문자|
|`\w`|alphanumeric(알파벳+숫자) + '_'|
|`\W`|non-alphanumeric 및 '_' 제외|
|`\d`|숫자|
|`\D`|숫자를 제외한 모든 문자|

<br>

- 예시

정규표현식 : `r"([\w]+\s*:?\s*)?\(?\+?([0-9]{1,3})?\-?[0-9]{2,3}(\)|\-)?[0-9]{3,4}\-?[0-9]{4}"`

<br>

*그룹별 해석*   

`([\w]+\s*:?\s*)?` : 이 그룹은 alphanumeric이 나올수도 있고, ':'이 있을수도 있고, 그 앞뒤로 공백이 다수 있을 수 있다. 또한 이 그룹 자체가 있을수도 있고, 없을 수 있다.    


`\(?\+?([0-9]{1,3})?\-?` : '(' 가 있을수도 있고, '+'가 있을 수 있다. 또, 숫자가 1번에서 3번 반복되고 이러한 그룹이 있을수도 있고, 없을 수 있다. 마지막으로 '-'도 있을수도 없을수도 있다.   

`[0-9]{2,3}(\)|\-)?` : 숫자가 2번에서 3번까지 반복되며, ')' 또는 '-' 둘중 하나가 존재할 수도 있다.   

`[0-9]{3,4}\-?[0-9]{4}` : 숫자가 3번에서 4번 반복되며 '-'가 있을수도 있으며, 다음에 숫자가 4번 반복된다.   
 


<img src="https://user-images.githubusercontent.com/52434993/107135604-6a2b2280-693f-11eb-82d8-ec949ab8fb2f.png">   

<br>


>## 분절(segmentation)   
>#### 문장 단위의 입력값들을 한 라인에 한 문장만 있게하는 분절을 하거나, 합쳐야 하는 경우에는 합쳐서 분절한다.   


<br>

- 문장 단위 분절   

<br>

*예시 문장*   

```
자연어처리는 인공지능의 한 줄기 입니다. 시퀀스 투 시퀀스의 등장 이후로 딥러닝을 활용한 자연어처리는 
새로운 전기를 맞이하게 되었습니다. 문장을 받아 단순히 수치로 나타내던 시절을 넘어, 원하는대로 문장을
만들어낼 수 있게 된 것입니다.

```   

```python
import sys, fileinput, re
from nltk.tokenize import sent_tokenize
import nltk
nltk.download('punkt')

# sent_tokenize
# 전체 문서를 문장 단위로 분리.

with fileinput.input('./sen.txt', inplace = True, backup = '.bak') as x:
    
    for line in x:
        if line.strip() != "":
            
            # 밑의 정규표현식이 기본적으로 nltk의 sent_tokenize가 해주는 기능이다.
            
            # line = re.sub(r'([a-z])\.([A-Z])', r'\1. \2', line.strip())
            
            # '.'을 기준으로 문장을 나눈다.
            sentences = sent_tokenize(line.strip())

            for s in sentences:
                if s != "":
                    sys.stdout.write(s+"\n")
                    
    fileinput.close()
```

<br>

- 문장 합친 후 분절   

*예시 문장*   

```
자연어처리는 인공지능의 한 줄기 입니다. 시퀀스 투 시퀀스의 등장 이후로
딥러닝을 활용한 자연어처리는 새로운 전기를 맞이하게 되었습니다. 문장을
받아 단순히 수치로 나타내던 시절을 넘어, 원하는대로 문장을 만들어낼 수 
있게 된 것입니다.

```   

```python
with fileinput.input('./sen2.txt', inplace = True, backup = '.bak') as y:
    buf = []
    for line in y:
        if line.strip() != "":
            
            # buf에 한 라인의 문장을 저장한다.
            buf += [line.strip()]

            # buf 문자열을 하나로 합친 후, '.'으로 구분 짓는다.
            sentences = sent_tokenize(" ".join(buf))

            # sentences의 요소가 2개 이상이면, buf에는 마지막 개체를 넣어주고,
            # 이외의 문장을 출력한다.
            if len(sentences) > 1:
                buf = sentences[-1:]
                
                sys.stdout.write('\n'.join(sentences[:-1]) + '\n')
    sys.stdout.write(' '.join(buf) + '\n')
    
    
    

```