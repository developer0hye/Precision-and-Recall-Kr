# Precision-and-Recall

본 게시글은 인식, 분류, 검출 등의 작업의 성능 평가시 사용되는 척도인 **Precision(정밀도)** 과 **Recall(재현율)** 에 대한 이해를 돕고자 작성되었습니다.

우선 **Precision** 과 **Recall** 을 설명하기에 앞서 우리가 해결해야할 문제를 정의하고 문제 해결 방법에 대한 성능 평가 척도로 **Precision** 과 **Recall** 을 사용함을 가정하겠습니다.

## Problem: Spot the difference!

우리가 해결해야할 문제를 **틀린 그림 찾기** 라고 정의하도록 하겠습니다.

**틀린 그림 찾기** 란 아래의 그림에서 좌측 그림과 우측 그림을 비교하여 서로 다른 부분을 찾는 문제입니다.

(심심하면 한 번 찾아보세요. 정답은 아래에 있습니다.)

![sponge](./figures/sponge.jpg)

## Answer

정답은 총 3 개로 우측 그림에서 검은색 원으로 강조된 부분입니다.

![answer](./figures/answer.png)


## Our Results
