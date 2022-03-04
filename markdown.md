죄의 삯은 사망이요 하나님의 은사는 그리스도 예수 우리 주 안에 있는 영생이니라 (롬6:23)

----
<center><img src="https://github.com/idebtor/DSpy/blob/cab9662b5ff01661ef8034289c92287d02b8e1ed/images/chap2/markdown_tutorial.jpg?raw=true" width=800></center>

# [퍼셉트론](https://en.wikipedia.org/wiki/Perceptron) 알고리즘

## 알고리즘$^{algorithm}$

우리가 구하고자 하는 것은 입력값 $x$들을 분류해 낼 수 있는 가중치 $w$인데, [로젠블라트](https://en.wikipedia.org/wiki/Frank_Rosenblatt)가 처음 제안한 학습 알고리즘은 다음과 같이 요약할 수 있습니다.  
1. 가중치를 0 혹은 무작위 작은 수로 초기화 한다. 
2. 각 학습 자료$^{Training \ Sample}$  $x^{(i)}$에 대해 다음을 실행한다. 
   - 출력 $\hat{y}$를 계산한다.    즉 $\hat{y} = h(\mathbf{w^Tx})$
   - 가중치$w_j$를 조정한다. 즉 $w_j := w_j + \Delta w_j$
   
<center><img src="https://github.com/idebtor/KMOOC-ML/blob/master/ipynb/images/joyai/person.png?raw=true" width=100></center>
<center>그림 4: 마크다운 문서 작성하기 </center>

<br>

아달라인에서는 활성화 함수의 반환하는 값(사실상 z와 같음)과 클래스 레이블과의 오차가 최소가 되도록 가중치를 조정합니다.  이를 위하여 최소제곱법$^{Sum \ of \ Squared \ Errors(SSE)}$을 이용한 비용함수$^{Cost \ Function} J(w)$를 다음과 같이 정의합니다.  이 값을 최소가 되도록 가중치를 조정하는 것이 아달라인 알고리즘의 핵심입니다. 

$$
 SSE = \frac{1}{2} \sum_{i=1}^{m}(target^{(i)} - output^{(i)})^2 \\
 J(w) = \frac{1}{2} \sum_{i=1}^{m}(y^{(i)} - \hat{y}^{(i)})^2  \tag{1} 
$$

식(1)에 있는 $\frac{1}{2}$은 곧 우리가 하게 될 미분을 편하게 하기 위하여 첨가한 것인데, 실제적인 계산에는 영향을 미치지 않습니다. m은 훈련자료의 총 갯수입니다. $y^{(i)}$는 i 번째 훈련자료의 클래스 레이블이며 이 값은 이미 우리에게 알려진 값입니다. $\hat{y}^{(i)}$는 i번째 훈련자료에 대해 아달라인 알고리즘이 예측한 값입니다.  그러므로 비용함수 식(1)을 다음과 같이 쓸 수 있습니다. 

$$
J(w) = \frac{1}{2} \sum_{i} \big(y^{(i)} - h(z^{(i)})\big)^2 \\
J(w) = \frac{1}{2} \sum_{i} \big(y^{(i)} - \sum_j (w_j x_j^{(i)})\big)^2  \tag{2} 
$$