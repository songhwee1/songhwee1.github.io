---  
layout: post  
title: "Kaggle(캐글) 시작해보기(2)"  
subtitle: "Titanic 생존자 예측"  
categories: dev
tags: 데이터분석 빅데이터 캐글 BigData DataScience Kaggle
comments: true  
---  

> Titanic 생존자 예측

---

# Titanic - Machine Learning from Disaster

+ Kaggle 입문자를 위한 튜토리얼 문제라고 할 수 있는 타이타닉 호 생존자 예측 문제입니다.

+ 타이타닉 호 침몰 사건 당시의 사망자와 생존자를 구분하는 요인 분석을 통해 승객들의 생존 여부를 예측하는 문제입니다.

# 시작을 위한 준비

먼저 Competitions 메뉴에서 'titanic' 이라고 검색하면 아래와 같은 결과가 나올텐데, 이중에서 Titanic - Machine Learning from Disaster 을 클릭해줍니다.

![titanic 검색](https://songhwee1.github.io/assets/img/dev/dataScience/kaggle_titanic_search.png "titanic 검색")

이후, Join Competition 버튼을 클릭하여 참가 신청을 합니다.

![titanic 메인](https://songhwee1.github.io/assets/img/dev/dataScience/kaggle_titanic_main.png "titanic 메인")

이제 본격적으로 시작을 해볼텐데, 먼저 Data탭을 클릭한 후 하단의 Download All 버튼을 클릭하여 csv파일을 다운로드 받아줍니다.

![titanic 다운](https://songhwee1.github.io/assets/img/dev/dataScience/kaggle_titanic_download_csv.png "titanic 다운")

그럼 titanic 이라는 이름의 압축파일이 다운받아 지는데, 압축을 풀고 파일들을 작업할 폴더로 옮겨줍니다.

본격적으로 시작하기 전에, 이후 작업들은 Python으로 진행되기 때문에 개발환경을 미리 세팅해주시기 바랍니다.

## 데이터 불러오기

먼저, numpy와 pandas라이브러리를 import하고, 다운로드받은 csv파일을 불러오고, 잘 불러와졌는지 **train.head()**를 통해 확인해봅니다.

``` python
import pandas as pd
import numpy as np

train = pd.read_csv('train.csv')
test = pd.read_csv('test.csv')
train.head()
```

정상적으로 동작하였다면 다음과 같은 결과가 출력됩니다.

|    |   PassengerId |   Survived |   Pclass | Name                                                | Sex    |   Age |   SibSp |   Parch | Ticket           |    Fare | Cabin   | Embarked   |
|---:|--------------:|-----------:|---------:|:----------------------------------------------------|:-------|------:|--------:|--------:|:-----------------|--------:|:--------|:-----------|
|  0 |             1 |          0 |        3 | Braund, Mr. Owen Harris                             | male   |    22 |       1 |       0 | A/5 21171        |  7.25   | nan     | S          |
|  1 |             2 |          1 |        1 | Cumings, Mrs. John Bradley (Florence Briggs Thayer) | female |    38 |       1 |       0 | PC 17599         | 71.2833 | C85     | C          |
|  2 |             3 |          1 |        3 | Heikkinen, Miss. Laina                              | female |    26 |       0 |       0 | STON/O2. 3101282 |  7.925  | nan     | S          |
|  3 |             4 |          1 |        1 | Futrelle, Mrs. Jacques Heath (Lily May Peel)        | female |    35 |       1 |       0 | 113803           | 53.1    | C123    | S          |
|  4 |             5 |          0 |        3 | Allen, Mr. William Henry                            | male   |    35 |       0 |       0 | 373450           |  8.05   | nan     | S          |

표를 보면 성별, 나이 등등 여러가지 특성이 있는데, 이중 의미를 바로 알기 힘든 것들에 대해서 알아보겠습니다.

**Survivied**: 생존 여부(0은 사망, 1은 생존; train 데이터에서만 제공)  
**Pclass**: 사회경제적 지위(1에 가까울 수록 높음)  
**SipSp**: 배우자나 형제 자매 명 수의 총 합  
**Parch**: 부모 자식 명 수의 총 합  

## Pie Chart

특성별 분포를 보기 위해 Pie Chart를 그려볼텐데, 먼저 matplotlib, seaborn라이브러리를 불러옵니다.
```python
import matplotlib.pyplot as plt
%matplotlib inline
import seaborn as sns
sns.set()
```
그리고, Pie Chart를 그리기 위한 함수를 정의해줍니다.
```python
def pie_chart(feature):
    feature_ratio = train[feature].value_counts(sort=False) 
    feature_size = feature_ratio.size 
    feature_index = feature_ratio.index 
    survived = train[train['Survived'] == 1][feature].value_counts()
    dead = train[train['Survived'] == 0][feature].value_counts()     
    plt.plot(aspect='auto') 
    plt.pie(feature_ratio, labels=feature_index, autopct='%1.1f%%') 
    plt.title(feature + '\'s ratio in total')
    plt.show() 
    for i, index in enumerate(feature_index): 
        plt.subplot(1, feature_size + 1, i + 1, aspect='equal') 
        plt.pie([survived[index], dead[index]], labels=['Survivied', 'Dead'], autopct='%1.1f%%')       
        plt.title(str(index) + '\'s ratio')
    
    plt.show()
```
먼저 성별에 대한 Pie Chart를 그려보겠습니다.
```python
pie_chart('Sex')
```
코드를 실행해보면, 아래와 같이 **남성**이 **여성**보다 배에 많이 탔으며, **남성**보다 **여성**의 생존비율이 높았다는 것을 확인할 수 있습니다.  
![titanic 탑승자성비](https://songhwee1.github.io/assets/img/dev/dataScience/kaggle_titanic_sex_output.png "titanic 탑승자성비")  
![titanic 생존자성비](https://songhwee1.github.io/assets/img/dev/dataScience/kaggle_titanic_sex_output_1.png "titanic 생존자성비")

다음으로 사회경제적 지위에 따른 Pie Chart를 그려보겠습니다.
```python
pie_chart('Pclass')
```
코드를 실행해보면, 사회경제적 지위가 높을수록(pclass 숫자가 작을수록) 생존 비율이 높았다는 것을 알 수 있습니다.
![titanic 탑승자성비](https://songhwee1.github.io/assets/img/dev/dataScience/kaggle_titanic_pclass_output.png "titanic 탑승자성비")  
![titanic 생존자성비](https://songhwee1.github.io/assets/img/dev/dataScience/kaggle_titanic_pclass_output_1.png "titanic 생존자성비")

오늘은 데이터를 시각화 해보는 과정을 알아보았습니다.  
다음 포스팅에서는 앞으로 예측을 진행할 모델에게 학습시킬 특성들을 골라서 학습하기 알맞게 전처리 과정을 진행 해보겠습니다.