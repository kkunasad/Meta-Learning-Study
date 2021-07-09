# Lecture2

- Multi-task learning
    - models & training
    - challenges
    - case study of real-world multi-task learning
- Meta-Learning
    - problem formulation
    - General recipe of meta-learning algorithms
    - Black-box adaptation approaches

## Multi-task Learning

- Data Generating distribution
    - Multi-task classification
    - Multi-label learning

- Single-task Learning

    ![Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled.png](Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled.png)

    - 데이터 분포 D가 존재할 때, 손실 함수 L을 최소화 할 수 있는 파라미터 theta

- Task

    ![Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%201.png](Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%201.png)

    - input x에 대한 분포, output의 분포, loss function 사용 과정

- Multi-Task Learning
    - Task 별 동일 loss function 사용
- Multi-Label Learning
    - Task 별 동일 loss function과 p(x) 사용

- loss function이 같은 경우?
    - 분포 방식이 다를 때
    - 특정 task를 더 중요하게 여길 때

## Task descriptor

- Meaning :
    - one-hot encoding of the task index
    - whatever meta-data
    - z_i

- Model이 해야 하는 일
    1. How should the model be conditioned on z_i? → z_i를 어떻게 conditioning 하냐?
    2. What parameters of the model should be shared? → object를 어떻게 최적화 하냐?

- Conditioning
    - How should you condition on the task in order to share as little as possible?
        - → How & Where to share parameters

![Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%202.png](Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%202.png)

![Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%203.png](Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%203.png)

- Objective

![Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%204.png](Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%204.png)

## Challenges

- Negative Transfer
    - 단일 모델이 더 성능이 좋은 경우
    - Optimization 과정의 문제 또는 파라미터나 output이 모델의 표현 범위보다 부족한 경우
    - 테스크간 share를 줄이면 문제 해결

- Overfitting
    - 각각의 테스크를 별개로 학습한 경우
    - 테스크간 share를 늘리면 문제 해결

# Meta-Learning Basics

- Mechanistic view
    - 알고리즘이 어떻게 실행되는지 알기 수월
    - 데이터셋 기반으로 새 데이터 예측
- Probabilistic view
    - 알고리즘이 어떻게 실행되는지 알기 어려움
    - 적은 양의 데이터에도 적용 가능

## Probabilistic View

- 일반적인 지도학습
    - input x와 파라미터에서 output y가 나올 확률 → 이 확률 최대화
    - 데이터가 적은 경우 오버피팅

        ![Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%205.png](Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%205.png)

- Meta-learning
    - 각 task 별 데이터 분할

        ![Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%206.png](Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%206.png)

    - meta-parameter 학습
    - output의 분포

        ![Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%207.png](Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%207.png)

- 주어진 데이터 셋에서 메타 러닝 파라미터 세타* 학습
    - 메타 학습
    - 이를 가지고 출력이 나올 확률을 최대화 하는 메타러닝 파라미터를 찾는다

        ![Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%208.png](Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%208.png)

        ![Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%209.png](Lecture2%2099bcc297279d41049c50e3176564a8e8/Untitled%209.png)