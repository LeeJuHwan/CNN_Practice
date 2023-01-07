# CNN_Practice

### 데이콘과 캐글로 배우는 CNN

### 2023.01.07 
<hr>

> <strong>[EMNIST]<strong>(https://dacon.io/competitions/official/235626/overview/description) : 데이콘 컴퓨터 비전 학습 경진대회

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
        factor = 0.08Cancel changes
    * 콜백함수 선언 시
    --> lr = 0.08
    ```
    - [콜백 함수 참고자료](https://deep-deep-deep.tistory.com/56)
