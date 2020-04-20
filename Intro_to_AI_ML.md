## Introduction to Artificial Intelligence and Machine Learning

 아래의 5가지 주제에 대하여 학습을 하였다.

- 머신러닝과 비슷한 분야의 비교
- 머신러닝에서 다루는 문제의 형태
- Representation Learning
- Famouse AI systems
- 인공 지능 도메인별 Data set

위의 각각의 소주제에 대하여 학습하고 이해한 내용을 요약 정리하면 다음과 같다.



1. Machine Learning vs Related Areas

   머신 러닝은 다양한 분야의 개념과 상호적으로 비슷하게 이해하는 경우가 많다.

   이번 학습을 통해서 평소에 비슷하게 이해한 분야에 대해, 두 분야의 차이점과 공통점을 확실하게 이해할 수 있었다.

   - Machine Learning vs Big Data

     - 빅데이터를 어떻게 하면 해석, 이해, 분석할 수 있는가에 대한 방법론 중 하나가 머신 러닝이다.
     - 최근에 가장 많이 쓰이는 빅데이터 해석 방법론이 머신러닝이다.

   - Machine Learning vs Data Mining

     - 머신러닝과 데이터 마이닝의 차이는 '데이터' 자체에 대한 차이
     - 데이터 마이닝은 대부분이 정형 데이터(structured data)를 쓰고, 머신러닝에서는 정형 데이터를 쓰기도 하지만 비정형데이터를 쓰는 것을 큰 주로 생각하고 있다.
     - 대표적인 비정형 데이터가 이미지 데이터, 텍스트 데이터이기 때문에 머신러닝의 큰 장점은 이러한 비정형 데이터를 분석할 수 있다는 것이다.

   - Machine Learning vs Artificial Intelligence

     - Machine Learning `develops data-dependent solutions` to the problems in Artificial Intelligence
     - 머신러닝은 AI의 일부분
     - 인공지능은 사람의 지능을 어떻게 컴퓨터도 가지게 하는 것인지라면, 그 지능적 행동의 컴퓨터를 만드는 방법 중 데이터에 의존하는, 데이터를 통계적으로 분석해서 모델을 만드는 방법이 머신러닝이라고 할 수 있다.

   - Machine Learning vs Statistics

     - Machine Learning is `deeply rooted` in, but `expands` the practical limitations of Statistics
     - 통계학자들이 만들어둔 다양한 모델들을 가져다가 실생활에서 볼 수 있는 다양한 데이터에 적용하는 것이 머신러닝
     - practical limitations 를 극복한다는 것은, 통계학에서 다루는 데이터보다 훨씬 더 양이 많고 노이즈도 많고 데이터가 부분적으로 없거나 훼손된 경우가 많은 경우머신러닝의 다양한 기법들이 들어가서 통계학의 한계를 극복한다는 의미이다.

     

2. 머신러닝에서 다루는 문제의 형태

   머신러닝에서 기본적으로 다루는 문제들로는 기본적으로 지도학습, 비지도학습, 강화학습 3가지이다. 이 3가지에 더불어 Representation Learning 또한 다루는 문제 중 하나로, 이는 딥러닝이라고도 생각할 수 있는 부분이다.

   - Supervised Learning(지도학습)

     - Training Data(학습 데이터)가 존재하여 학습데이터를 바탕으로 학습을 한다.

     - 라벨이 붙어 있어서 정답을 가지고 있는 학습데이터 이기 때문에 지도학습이라고 한다. 즉, 지도는 라벨이 하는 것으로 이해하면 된다.

     - 컴퓨터가 학습데이터로 학습한 다음에, testing data(컴퓨터가 학습하지 않은 데이터)가 들어왔을 때 이 데이터에 대해 classification(분류)하는 것

     - Classification

       : 분류 모델에는 선형 모델과 비선형 모델이 있다.

       ![img](C:/Users/samsung/ssafy2/특화강의정리/day10/AI_images/linear_vs_nonlinear)

   - Unsupervised Learning(비지도학습)

     - 학습데이터가 따로 없이 학습하는 것이다.
     - 비지도 학습에는 여러가지 알고리즘들이 있다.
       - K-means clustering

         - 어떤 기준이 되는 중간 점을 찾고, 그 기준의 각각의 데이터 포인트의 거리를 계산해서 어떤 기준점에서 그 포인트가 가장 가까운 거리인지 계산하는 방법
         - 몇개의 그룹으로 어떻게 나눌 것이냐는 데이터가 어떻게 생겼느냐에 따라 달라진다.
       - DB Scan
         - 어떤 기준이 되는 점들을 먼저 찾아내고 하는 것이 아니라 어떤 임의의 데이터 포인트 하나에서 시작해서  자신 가까이 있는 점들로 부터 점점 세력을 늘려가는 알고리즘

   - Reinforcement Learning(강화학습)

     이번 강의에서는 강화학습에 대해서는 따로 다루지 않았다.

     인공지능이라고 하면 강화학습이 가장 많이 떠오르기 때문에 개인적으로 개념과 함께 다양한 예에 대해서 찾아봐야 할 것같다.

   - Representation Learning

   

    지도학습이든, 비지도학습이든 내가 가지고 있는 데이터에서 숨겨져 있는 의미를 잘 찾아내는 알고리즘이 무엇일까 고민하며 그러한 알고리즘을 알아내는 것이 머신러닝 연구하는 사람들이 하는 일이라고 할 수 있다.

   

3. Representation Learning

   Representation Learning의 대표적인 것이 Deep Neural Network라고 할 수 있다. 그 중, Facial recognition이 가장 유명하며 이는 다양한 레이어에서 픽셀로 부터 선을, 선으로부터 눈과 코 등 신체부위를, 그리고 그 부위들을 모아 얼굴을 조합하는 알고리즘이다.

   

   Deep Neural Network는 모델의 표현이 풍부하다는 장점이 있는데, 이는 반대로 모델들이 복잡하다는 뜻이다. 따라서 계산함에 있어 시간이 오래 걸리고 데이터 양도 많아야한다. 1980년대에는 뉴럴 네트웍을 계산할만한 데이터 양이 부족했고 컴퓨터 성능도 부족했는데, 2000년대 되면서 데이터 양도 늘어나고 컴퓨터 성능이 늘어나면서 다시 주목받는 분야중 하나이다.

   

    Deep Neural Network의 단점은
    
    전체적인 디테일보다 하나의 작은 디테일을 보고 결정을 하기 때문에, 작은 디테일의 핏팅을 오버해서 나타나는 over fitting이 일어난다는 단점이 있다. 또한 팔라미터 측정이 어렵다는 단점이 있다.

   



4. Famouse AI systems

   인공 지능 시스템 중 대표적인 시스템에 대해 알수 있었다. 알파고와 같이 익숙한 인공지능들도 있었지만, 잘 알지 못하였던 인공지능 시스템에 대해 학습할 수 있었다. 시기별로 개발된 시스템을 알려주셔서, 어떻게 인공지능 시스템들이 더더욱 발전해 나갔는지도 알 수 있었다.

   대표적인 시스템들은 다음과 같다.

   - IBM Chess Machine Beats Humanity's Champ
   - DARPA Urban Challenge 2007(자율주행)

   - IBM Research Watson 2011(IBM Watson Jeopardy 퀴즈 쇼)

   - DeepMind AlphaGo 2016 vs. Lee Sedol

   - DeepMind AlphaGo Zero(알파고 2016과 달리, 학습데이터 없이, 0에서부터 스스로 대결하며 학습. 즉 비지도학습을 한 것이다.)

   - Google Duplex 2018(다른 회사들의 서비스와 다르게, 범용적이기 보다 비지니스 플랫폼을 바탕으로 한다.)

5. 인공 지능 도메인별 Data set

   인공지능에는 

   - Visual Intelligence
   - Language Intelligence 

   등 다양한 Domain들이 존재한다.

    각 도메인 별로 적합한 Data set의 종류는 다름을 알 수 있었고, 다양한 데이터 셋의 종류에 대해 학습할 수 있었다. 각 도메인 별 데이터 셋의 종류는 아래와 같다.

   - Visual Intelligence에 적합한 데이터셋

     - MNIST

       : 숫자 필기 인식

     - ImageNet

       : 몇천개 클래스의 이미지들이 

       - 클래스들이 엄청나게 많고 이미지들이 hierarchy(계층)을 이루고 있기 때문에 이미지 넷에 대해서는 아직도 계속 정확도를 올리는 것에 대한 연구가 계속 되고 있고, 정확도가 어느정도 올라가도 데이터가 적은 것에 대해서도 정확도를 높일 수 있는가에 대해 계속해서 연구 진행 중이다.

       - 아직까지 머신러닝에서는 1shot learning , 0shot learning이 어렵다는 문제점이 있다.

   - Language Intelligence

     - SQUAD Dataset

       (Stanford Question Answer Dataset, Rajpurkar, et al. 2018)

       : 질문을 읽고 질의응답이 가능한 데이터 셋이다.

     - Machine Traslation 에서 사용하는 데이터 셋 종류

       예전에는 번역 시 문법적인걸 많이 따졌는데, 요즘은 어떤 문서에 대해 똑같은 문서가 한국어, 영어로 적힌게 있으면 기계 번역을 쉽계 할 수 있다.

       - Europarl Corpus

         : Machine Traslation에서 많이 쓰는 데이터 셋으로, 단점은 유럽 언어만 있다는 것이다.

       - UN Parallel Corpus

         : United Nations Parallel Corpus ( Europarl Corpus 보다 조금 더 다양한 언어가 있음)

     - GLUE Benchmark

       : 가장 최근에 생긴 데이터셋으로, 가장 많이 쓰인다.

       알파고를 만든 deepMind, UWNLP, NYU에서 만든 것으로 구체적인 언어에 대한 테스트를 하는 것이다.



 한시간에 가까운 강의였지만, 짧은 시간동안 인공지능 분야에서 많이 사용하는 용어와, 학습분야, 데이터 셋에 대해서 전반적이 이해를 할 수 있는 강의였다.

앞으로 학습 내용을 바탕으로 특화프로젝트 시 좀 더 폭넓게 이해하고 적용해서 조금 더 완성도 있는 프로젝트를 완성할 것으로 예상된다.

