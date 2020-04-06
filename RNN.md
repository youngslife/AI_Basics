# RNN

# Recurrent Neural Network(순환신경망)

자연어나 음성신호, 주식과 ㄱㅌ은 연속적인 시계열(time series)데이터에 적합한 모델

## Recurretn Neurons (순환 뉴런)

RNN은 입력층 ⇒ 츨력층 방향으로만 흐르는 피드포워드(feedforword) 신경망고 비슷하지만 출력이 다시 입력으로 받는 부분이 있다.

### Memory cell

타임 스텝 t에서 순환 뉴런의 출력은 이전 ㅌ임 스텝의 모든 입력에 대한 함수이기 때문에 `메모리`라고 볼 수 있다.

따라서, `Memory Cell` 또는 `Cell`은 타임 스텝에 걸쳐 어떠한 상태를 보존하는 신경망의 구성요소를 말한다.

$$h_t = f(h_{t-1}, x_t)$$

일반적으로 타임 스텝(t) 에서 셀의 상태(hx, h=hidden)는 t에서의 입력과 이전 t-1의 상태에 대한 함수이다.

일반적으로 많이 사용되는 RNN은 출력 y_t 와 히든 상태 h_t가 구분되며, 입력으로는 h_t가 들어간다.

RNN에서 activation function으로는 `tanh`가 주로 사용된다.