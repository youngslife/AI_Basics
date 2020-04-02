# Tokenization(토큰화)

 주어진 Corpus(말뭉치, 코퍼스)에서 Token(토큰) 단위로 나누는 작업을 토큰화(Tokenization)라고 한다.

자연어 처리에서 코퍼스 데이터는 사용하고자하는 용도에 맞게 토큰화Tokenization&정제(Cleaning)&정규화(normalization) 하게 된다.

### 1. 단어 토큰화(Word Tokenization)

- 토큰의 기준을 단어(word)로 하는 경우

- 여기서 단어는 단어 단위 외에도 단어구, 의미를 갖는 문자열로 간주되기도 한다.

- 단순히 구두점(punctuation)이나 특수문자를 전부 제거하는 정제 작업은 토큰이 의미를 잃어버리는 경우가 발생하기도한다. 따라서, 이러한 정제 작업을 수행하는 것만으로 토큰호 작업이 해결되는 것은 아니다.

  (띄어쓰기 단위로 자르면 단어 토큰이 구분되는 영어와 달리, 한국어는 띄어쓰기만으로는 단어 토큰을 구분하기 어려움)

### 2. 토큰화 고려사항

1. 구두점이나 특수 문자를 단순 제외해서는 안된다.

   - 코퍼스 정제 작업 시, 구두점도 하나의 토큰으로 분류하기도 함.

     e.x. 온점(.)의 경우, 문장의 경계를 알려주는 역할로 제외하지 않을 수 있다.

     e.x. Ph.D / $31.55 처럼 단어 자체에 구두점이 있는 경우

     e.x. 100,000  숫자 사에이 comma 가 있는 경우

2. 줄임말과 단어 내에 띄어쓰기가 있는 경우

   - I'm, / whar're 처럼 clitic(접어)가 있는 경우
   - New York / Roack n roll 처럼 하나의 단어에 중간 띄어쓰기가 존재하는 경우
   - 토큰호 작업은 이런 단어들도 하나로 인식할 수 있는 능력도 가져야함

3. 표준 토큰화 예제

   - Penn Treebank Tokenization

     규칙 1. - (hypen)으로 구성된 단어는 하나로 유지

     ​		 2. apostrophe(')로  접어가 함께있는 단어는 분리해줌

     ```python
     from nltk.tokenize import TreebankWordTokenizer
     
     tokenizer=TreebankWordTokenizer()
     text="Starting a home-based restaurant may be an ideal. it doesn't have a food chain or restaurant of their own."
     print(tokenizer.tokenize(text))
     ```

     ```markdown
       ['Starting', 'a', 'home-based', 'restaurant', 'may', 'be', 'an', 'ideal.', 'it', 'does', "n't", 'have', 'a', 'food', 'chain', 'or', 'restaurant', 'of', 'their', 'own', '.']
     ```

     

### 3. 문장 토큰화(Sentence Tokenization)

- 토큰 단위가 문장인 경우

- 코퍼스 내에서 문장 단위로 구분하는 작업으로, 문장 분류(sentence segmentation) 라고도 부름

- 코퍼스가 정제되지 않은 상태면, 코퍼스는 문장 단위로 구분되어있지 않을 가능성이 높으므로, 사용 용도에 맞추기 위해 문장 토큰화가 필요할 수 있음

- 단순히 문장 구분자(., ?, !)로 토큰화를 하는게 아니라. 코퍼스 언어의 종류, 해당 코퍼스 내 특수문자들이 어떻게 사용되고 있는지에 따라서 직접 규칙들을 정의하여 사용할 수 있다.

  (100% 정확도를 얻는 일은 쉬운 일은 아니다. 데이터에 오타 나 문장구성이 엉망이면 규칙이 소용 없을 수 있기 때문이다)

- 예제 ( NLTK sent_tokenize)

  ```python
  from nltk.tokenize import sent_tokenize
    
  text="I am actively looking for Ph.D. students. and you are a Ph.D student."
  print(sent_tokenize(text))
  ```

  ```markdown
    ['I am actively looking for Ph.D. students.', 'and you are a Ph.D student.']
  ```

  

  - NLTK 는 단순히 온점을 구분자로 묹ㅇ을 구분하지 않기 때문에, Ph.D.를 문장내의 단어로 인식한다.

- 문장 토큰화 수행 오픈소스

  - NLTK
  - OpenNLP
  - 스탠포드 CoreNLP
  - splitta
  - LingPipe 등

  (문장 토큰화 규칙 짤때 발생하는 여러가지 예외사항 을 검색하여 참고할 것)

- Binary Classifier (이진분류기)

### 4. 한국어 토큰화

- 한국어 토큰화가 어려운 이유

### 5. 품사 태깅 (Part-of-speech tagging)

fly, 못 등 단어의 표기는 같지만 품사에 따라 의미가 다른 경우가 있다.

따라서 단어의 의미를 제대로 파악하기 위해서는 해당 단어가 어떤 품사로 쓰였는지 보여주는 것이 주요 지표가 될 수 있다.

토큰호 과정에서 각 단어가 어떤 품사로 쓰였는지 구분하는 작업을 `품사태깅(part-of-speech tagging)` 이라고 한다.

- NLTK - 영어 품사 태깅

  품사의 명명과 태깅 기준에는 여러가지가 있는데, NLTK 는 Penn Treebank POS Tags라는 기준을 사용한다.

  ```python
  from nltk.tag import pos_tag
    
  x = word_tokenize(text)
  pos_tag(x)
  ```

  ```markdown
    [('I', 'PRP'), ('am', 'VBP'), ('actively', 'RB'), ('looking', 'VBG'), ('for', 'IN'), ('Ph.D.', 'NNP'), ('students', 'NNS'), ('.', '.'), ('and', 'CC'), ('you', 'PRP'), ('are', 'VBP'), ('a', 'DT'), ('Ph.D.', 'NNP'), ('student', 'NN'), ('.', '.')]
  ```

  

  Penn Treebank POG Tags에서의 품사 명명

  PRP: 인칭대명사,  VBP: 동사,  RB: 부사,  VBG: 현재부사,  IN: 전치사,  NNP: 고유명사,  NNS: 복수형 명사,  CC: 접속사,  DT: 관사

- KoNLPy (한국어 형태소 분석기 파이썬 패키지 - http://kkma.snu.ac.kr/)

  - 형태소 분석기를 사용한다는 것은 단어 토큰화가 아닌 형태소 단위의 형태소 토큰화(morpheme tokenization)을 수행한다는 의미이다.

  - 형태소 분석기 종류

    - Okt(Open Korea Text)
    - Mecab(메캅) - 속도 good, 사용자 사전 이용가능 (신한 )
    - Komoran(코모란)
    - Hannanum (한나눔)
    - Kkma(꼬꼬마) - 형태소 분석 good, 문장 or 데이터가 많은 경우 속도 down(다량의 데이터 사용 시 부적절)

    각 형태소 분석기는 성능과 결고가 다르기 때문에, 사용하고자 하는 필요 용도에 어떤 형태소 분석기가 가장 적절한지 판단하고 사용해야한다.

  - KoNLPy 형태소 분석

    ```python
      from konlpy.tag import Kkna
      kkma = Kkma()
      
      print(kkma.morphs("열심히 코딩한 당신, 연휴에는 여행을 가봐요"))
    ```

    ```markdown
      ['열심히', '코딩', '하', 'ㄴ', '당신', ',', '연휴', '에', '는', '여행', '을', '가보', '아요'] 
    ```

    

  - KoNLPy 품사 태깅 해보기

    ```python
      print(kkma.pos("열심히 코딩한 당신"))
    ```

    ```markdown
      [('열심히', 'MAG'), ('코딩', 'NNG'), ('하', 'XSV'), ('ㄴ', 'ETD'), ('당신', 'NP')]
    ```

    

  - KoNLPy 명사 추출 해보기

    ```python
      print(kkma.nouns("열심히 코딩한 당신"))
    ```

    ```markdown
      ['코딩', '당신']
    ```

    