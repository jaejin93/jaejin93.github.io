---
title: "Meta-Learning:Learning to Learn Fast(1)"
categories: 
  - DeepLearning
last_modified_at: 2021-03-21
toc: false #Table of Contents
comments: true
use_math: true # MathJax On
---

## 들어가며

연구실에서 진행하는 건설 하자데이터 처리 과제에 참여하게 될 것 같고, Few-Shot Learning 부분을 담당하게 될 것 같다. 
Few-Shot Learning은 적은 사진으로 학습하여 좋은 성능을 내는 이미지 처리 방식이다. 일반적인 CNN같은 이미지 처리 방식에서는
한개의 모델을 학습하기 위해 대량의 데이터가 필요하지만 건설 산업은 일회성 산업(한개의 건물을 지으면 끝)이라 데이터를 획득한다
한들 다른 프로젝트에 적용하는게 다른 산업보다는 힘들다. 그렇기에 적은 사진으로도 학습이 가능한 Few-Shot Learning 기술을 
사용하게 되는데 이 때 사용되는 Meta-Learning에 대해서 첫 블로그 글을 쓰고자 한다.

이 글은  GPT를 만든 OpenAI Enigneer인 Lilian Weng의 Meta-Learning:Learning to Learn Fast을 참고했다.

>
> "Learning To Learn"이라고 알려져 있는 Meta-Learning은 몇몇 training 예제를 통해서 모델로 하여금, 새로운 기술을 배우거나, 새로운 환경에 빠르게 적응하는 것을 나타낸다.
> 1. Metric 기반의 **Efficient Distance Metric**을 학습하는 방식
> 2. Model 기반의 **External/Internal Memory를 통한 Recurrent Network을 사용**하는 방식
> 3. Optimization 기반의 **Fast Learning을 위한 Model Parameter를 최적화** 하는 방식
>
>

머신러닝을 통해서 좋은 모델을 만들기 위해서는 일반적으로 수많은 샘플을 활용하여 학습을 시키는 것이 필요하다. 이와 반대로 인간의 경우에는 훨씬 빠르고 효율적으로 새로운 개념이나 기술들을 학습한다. 고양이나 새를 많이 보지 않은 아이들이라고 할지라도 빠르게 그걸 구분할 수 있다. 자전거를 타는 방법을 아는 사람들은 시연 같은 과정 없이도 빠르게 오토바이를 타는 방법을 반견하곤 한다. 머신러닝에서도 이와 같이 적은 샘플만 가지고도 새로운 개념과 기술을 빠르게 학습하는 것이 가능할까? 이것이 바로 본질적으로 Meta-Learning이 풀고자 하는 문제점이다.

보통 좋은 Meta-Learning Model이라고 하면, Training Time동안에 접하지 않았던 새로운 Task나 Environment에 대해서 잘 적응하거나, 일반화가 잘 되는 것을 말한다. Adaptation Process(본질적으로 말하지면 Mini Learning Session)은 Test 과정에서 일어나게 되는데, 사실 이때에는 새로운 Task Configuration에 대해서 제한적으로만 노출되어 있다. 어째뜬, 이렇게 적응된 모델은 새로운 Task를 잘 수행할 수 있다. 이 것이 바로 Meta-Learning이 **Learning to Learn** 이라고 알려져 있는 이유이기도 하다.

여기서 Task란 Supervised Learning이나 Reinforcement LEarning과 같이 Machine Learning으로 정의될 수 있는 모든 문제들이 될 수 있다. 예를 들어 Meta-Learning Task를 나열하면 다음과 같다.
- 고양이가 없는 이미지를 학습시킨 Classifier도 몇개의 고양이 사진을 본 후에는 Test Image상에 고양이가 있는지 여부를 판단할 수 있다.
- 게임 봇이 새로운 게임에 대해서 빠르게 마스터 할 수 있다.
- 평평한 지면 환경에서만 학습해온 미니 로봇이 경사진 환경에서도 Task를 수행할 수 있다.


REFERENCE
<br>
[1. Meta-Learning:Learning to Learn Fast](https://lilianweng.github.io/lil-log/2018/11/30/meta-learning.html)
<br>
[2. Meta-Learning:Learning to Learn Fast(Korean)](https://talkingaboutme.tistory.com/entry/DL-Meta-Learning-Learning-to-Learn-Fast)

