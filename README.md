# Precision-and-Recall

본 게시글은 인식, 분류, 검출, 검색 등의 작업 성능 평가 시 활용되는 척도인 **Precision(정밀도)** 과 **Recall(재현율)** 에 대한 이해를 돕고자 작성되었습니다. 

**정확한 개념보다는 이러한 느낌이다! 임을 설명하기 위한 글입니다.**

우선 **Precision** 과 **Recall** 을 설명하기에 앞서 우리가 해결해야 할 문제를 정의하고 문제를 해결하기 위한 방법에 대한 성능 평가 척도로 **Precision** 과 **Recall** 을 활용하여 설명을 하겠습니다.

## 문제: 틀린 그림 찾기

우리가 해결해야 할 문제를 **틀린 그림 찾기** 라고 정의하도록 하겠습니다.

**틀린 그림 찾기** 란 2개의 유사한 그림을 비교해서 서로 다른 부분을 찾는 문제입니다.

(심심하시면 한 번 서로 다른 부분을 찾아보시길 바랍니다. 정답은 아래에 있습니다.)

<img src="./figures/sponge.jpg" width="50%">

정답은 총 3개 (소스, 모자, 접시)로 우측 그림에서 검은색 원으로 강조된 부분입니다.

<img src="./figures/answer.png" width="50%">

이제 우리가 **틀린 그림 찾기** 문제에 대한 해결 방법으로 A 방법과 B 방법을 개발했다고 가정하겠습니다.

아래의 그림은 A 방법 및 B 방법을 이용했을 때의 결과를 정답과 비교한 그림입니다. 

보라색 원으로 강조된 부분은 각 방법이 서로 다른 부분 이라고 판단하여 찾아낸 부분입니다.

![results](./figures/results.png)

결과를 비교해보면 A 방법은 모자와 접시는 잘 찾아냈지만, 소스는 찾아내지 못했습니다. 

그리고 B 방법은 모자, 접시, 소스를 잘 찾아냈지만, 뒤집개와 햄버거 부분을 서로 다른 부분으로 잘못 판단하였습니다.

그렇다면 정답을 모두 못찾았지만 변하지 않은 부분은 제대로 판단한 A 방법과 

정답은 모두 찾았지만 변하지 않은 부분을 제대로 판단하지 못한 B 방법 중 

어느 방법이 더 좋다고 판단할 수 있을까요?

이에 대한 성능 평가를 위해 **Precision** 과 **Recall** 이라는 척도가 활용됩니다.

우선 **Precision** 과 **Recall** 의 측정 방식에 대해 설명드리고 비교를 통해 차이점을 설명드리도록 하겠습니다.

## Precision

**Precision** 은 해당 방법이 서로 다른 부분이라고 판단한 부분들 중에서 실제로 서로 다른 부분(정답)의 비율을 의미합니다.

따라서,

A 는 2개의 부분을 서로 다른 부분으로 판단했고 그 중 정답은 2개 이므로 **Precision** 은 2/2 = 1.0 으로 100% 입니다. 

B 는 5개의 부분을 서로 다른 부분으로 판단했고 그 중 정답은 3개 이므로 **Precision** 은 3/5 = 0.75 로 75% 입니다.

## Recall

Recall 은 실제로 서로 다른 부분들(정답: 소스, 모자, 접시) 중에서 해당 방법이 몇 개의 정답을 맞추었는지에 대한 비율을 의미합니다.

따라서, 정답이 3개 일 때

A 는 2개의 부분을 서로 다른 부분으로 판단했고 그 중 정답은 2개 이므로 **Recall** 은 2/3 = 0.67 로 67% 입니다. 

B 는 5개의 부분을 서로 다른 부분으로 판단했고 그 중 정답은 3개 이므로 **Recall** 은 3/3 = 1.00 으로 100% 입니다.

## 정리

앞서 측정한 각 방법의 **Precision** 과 **Recall** 의 수치를 살펴보면 

**Precision** 을 측정했을때는 A 가 더 좋은 방법이라고 생각될 수 있으나, 

**Recall** 을 측정했을때는 B 가 더 좋은 방법이라고 생각될 수 있습니다.

그렇다면 **Precision** 이 높다는 의미와 **Recall** 이 높다는 의미는 무슨 차이가 있을까요?

A 방법과 B 방법이 내놓은 결과물(보라색 원)에 대하여 "문제를 풀어서 나온 답" 이라고 표현해 보겠습니다.

**Precision** 은 문제를 풀었을때 **오답(정답이 아닌데 정답으로 보는 경우, 정답을 못맞춘 경우가 아님!)** 이 존재하면 낮은 점수(페널티)를 주는 척도이며 또한 정답을 모두 못 맞췄더라도 **오답이 적다면** 높은 점수를 주는 척도입니다.

따라서 A 방법은 정답을 모두 못 맞췄지만 구해낸 답 중에서 오답이 없었고 B 방법은 정답을 맞추었지만 구해낸 답이 오답을 포함하고 있으므로 **Precision** 관점에서는 A 방법이 더 좋은 방법입니다. 

**Recall** 은 문제를 풀었을때 **오답이 존재하든 말든 정답을 많이 맞춘다면** 높은 점수를 주는 척도입니다.

따라서 B 방법은 3개의 답을 모두 맞췄고 A 방법은 2개의 답만 맞췄으므로 **Recall** 관점에서는 B 방법이 더 좋은 방법입니다.

따라서 어떠한 문제에 대한 해결 방법들을 평가할때,

정답을 모두 못맞추더라도 오답을 내지 않는 것이 중요하다면 **Precision** 의 수치가 높은 방법을 선택하는 것이 좋고, 

오답을 내더라도 정답을 맞추는 게 중요하다면 **Recall** 의 수치가 높은 방법을 선택하는 것이 좋습니다.

이번 게시글에서는 **Precision** 과 **Recall** 에 대한 **느낌** 을 알아보았습니다. 

보다 정확한 개념을 이해하고 싶으시다면 [precision, recall의 이해](https://darkpgmr.tistory.com/162) 를 읽어보시는 것을 추천해 드립니다.

