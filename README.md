# CNN_Practice

### 데이콘과 캐글로 배우는 CNN

### 2023.01.07 
<hr>

> [EMNIST](https://dacon.io/competitions/official/235626/overview/description) : 데이콘 컴퓨터 비전 학습 경진대회

- [ ] 복습 키워드
- ImageDataGenerator : 학습 데이터가 적은 경우를 대비한 데이터 증강
    - rotation_range : 각도 변경
    - horizontal_flip : 상하 전환
    - [이미지제너레이터 참고자료](https://acdongpgm.tistory.com/169)
- ReduceLROnPlateau : 모델의 개선이 없는 경우 learning rate를 조절하는 함수
    - factor : learning rate의 변하는 값을 정하는 인자 값
    ```
     learning rate * factor
     --> lr = 0.01 
        factor = 0.08
    * 콜백함수 선언 시
    --> lr = 0.08
    ```
    - [콜백 함수 참고자료](https://deep-deep-deep.tistory.com/56)

### 2023.01.10
<hr>

- [ ] Kaggle intel images classifcation 데이터 학습

- flow_from_directory : 이미지 폴더를 데이터프레임 형태로 불러오지 않고 png 본연의 이미지를 불러오는 학습 방법

``` 
class_indices.items()
>> {'buildings': 0,
 'forest': 1,
 'glacier': 2,
 'mountain': 3,
 'sea': 4,
 'street': 5}

item = {val : key for key, val in train_loader.class_indices.items()}
{0: 'buildings',
 1: 'forest',
 2: 'glacier',
 3: 'mountain',
 4: 'sea',
 5: 'street'}

``` 
- 오버피팅을 만났을 때 방지하는 방법 
    1. 데이터의 양을 늘리기
    2. 모델의 복잡도 줄이기
    - Layer층이 많을수록 모델이 많은 학습을 하기 때문에 층을 줄여 과적합을 방지하는 방법이 있다.
    3. 가중치 규제(Regularization) 적용하기
    - W값을 조금 더 작게 규제화 (0은 불가능)
    4. 드롭아웃(Dropout)
    - 드롭아웃 비율 만큼 노드를 비활성화 시킨다.
    ```
        model.add(Dopout(0.2))
        --> 10개의 노드 중 2개를 비활성화 하여, 노드의 영향을 줄이는 과적합 방지 방법이다.
        # 트랜지스터 개념 처럼 스위치를 껐다 켰다 하는 방식으로 이해하면 알기 쉬웠다.
    ```
    5. Batch Normalization
    - 입력의 평균을 0으로 조정
    - 평균이 0으로 조정된 입력을 정규화
    - 연산 결과의 배율 및 위치 조정
    > 학습 초기에 최적의 배율과 오프셋을 찾기 까지 학습 속도가 느리지만, 최적의 값을 찾고 나면 학습이 눈에 띄게 빨라진다.

- 언더피팅을 만났을 때 해결하는 데 도움을 준 방법
    1. 데이터 양 늘리기
    - 학습률이 낮은 데이터는 데이터증강
    2. Layer 늘리기
    - 노드 수를 늘리며 더 정교한 학습을 유도 해야한다.
    
<br>

- 인셉션 모델, 잔차 블록 구현 해보기
    - [인셉션 구현 자료](https://github.com/LeeJuHwan/CNN_Practice/blob/main/1.10_lecture/inception_vgg.ipynb)


### 2023.01.14
### fashion_mnist 
<hr>

- [ ] 복습 키워드

- 전이학습 방법을 이용 하려 했지만, 회색조 이미지인 데이터에는 전혀 맞지 않았다.
    - 모델 구조를 다시 만들어서 2%의 정확도를 높히고, 0.2의 오차률을 낮췄다. 하지만, 다른 데이터셋에서 내가 직접적으로 모델 구조를 0에서 부터 쌓는 일이 있을까 생각이든다. 전이학습을 이용하게 되면 학습 속도에서 큰 장점을 가져 갈  수 있을 것이니 전이학습을 통해 모델을 더  발전 시키는 방법을 공부 해 할 것  같다.
    <p>
- 이제는 단순 데이터셋에서 기본적인 학습을 하는 것이 아니라, ImageDataGenerator를 이용한 증강 또는, 배경색 등 다양한 방법을 통해 학습 할 데이터에 더 많은 노이즈를 거는 것을 공부 해보고 싶다. 예를 들어, 흰색 배경에 깔끔한 데이터를 학습 시키고 실제 테스트 데이터에서는 다른 배경과 각도가 다른 이미지 또는 노이즈가 있는 이미지라면 예측률이 많이 낮을 것이라고 생각이 들기 때문이다.

### 번외
### DACON 4D block AI 경진대회 참여 
- EfficienetV2M 모델 사용
- val_loss 0.00001
- val_acc 99.1

- submission acc 83%

- 중요한건 학습 하는 데이터!
