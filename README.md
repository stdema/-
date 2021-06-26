Deep Learning에 대한 기본 지식을 이해하기 위해 MATLAB®에서 제공하는 Deep Learning Toolbox를 사용

# - 딥러닝을 사용하여 웹캠 영상 분류하기

이 예제에서는 사전 훈련된 심층 컨벌루션 신경망 GoogLeNet을 사용하여 웹캠의 영상을 실시간으로 분류하는 방법을 보여줍니다.

MATLAB®과 간단한 웹캠 및 심층 신경망을 사용하여 주변의 사물을 식별합니다. 이 예제에서는 사전 훈련된 심층 컨벌루션 신경망(CNN 또는 ConvNet) GoogLeNet을 사용합니다. 1백만 개가 넘는 영상에 대해 훈련된 GoogLeNet은 영상을 키보드, 커피 머그잔, 연필, 각종 동물 등 1,000가지 사물 범주로 분류할 수 있습니다. GoogLeNet을 다운로드하고 MATLAB을 사용하여 계속해서 카메라 영상을 실시간으로 처리할 수 있습니다.

GoogLeNet은 다양한 영상을 대표하는 다양한 특징을 학습했습니다. 영상을 입력값으로 받아 영상에 포함된 사물의 레이블과 각 사물 범주의 확률을 제공합니다. 주변의 사물을 사용하여 GoogLeNet이 영상을 얼마나 정확히 분류하는지 실험해 볼 수 있습니다. GoogLeNet의 사물 분류에 대해 자세히 알아보기 위해, 최종 결정된 클래스만 표시하는 대신 상위 5개의 클래스에 대한 점수를 실시간으로 표시할 수 있습니다.

# - 카메라와 사전 훈련된 신경망 불러오기
카메라에 연결하고 사전 훈련된 GoogLeNet 신경망을 불러옵니다. 이 단계에서는 임의의 사전 훈련된 신경망을 사용할 수 있습니다. 이 예제를 실행하려면 MATLAB Support Package for USB Webcams와 Deep Learning Toolbox™ Model for GoogLeNet Network가 필요합니다. 필요한 지원 패키지가 설치되어 있지 않으면 이를 다운로드할 수 있는 링크가 제공됩니다.

![image](https://user-images.githubusercontent.com/86040099/123498524-60def000-d66b-11eb-858d-384d6c1cd15a.png)

이 예제를 다시 실행하려면 먼저 clear camera 명령을 실행하십시오. 여기서 camera는 웹캠에 대한 연결입니다. 이렇게 하지 않으면 동일한 웹캠에 대한 또 하나의 연결을 만들 수 없기 때문에 오류가 표시됩니다.

# - 카메라의 스냅샷 분류하기
영상을 분류하려면 신경망의 입력 크기에 맞게 영상의 크기를 조정해야 합니다. 신경망 영상 입력 계층의 InputSize 속성의 처음 2개 요소를 가져옵니다. 영상 입력 계층은 신경망의 첫 번째 계층입니다.

![image](https://user-images.githubusercontent.com/86040099/123498515-4b69c600-d66b-11eb-97c0-ce22529385b3.png)
![image](https://user-images.githubusercontent.com/86040099/123498426-deeec700-d66a-11eb-8327-7f6ce37006a6.png)

카메라의 영상을 예측된 레이블 및 해당 레이블의 확률과 함께 표시합니다. classify를 호출하기 전에 먼저 신경망의 입력 크기에 맞게 영상의 크기를 조정해야 합니다.

![image](https://user-images.githubusercontent.com/86040099/123498485-21180880-d66b-11eb-8a0b-2334eb0267fc.png)

%%가장 높은 확률을 나타내는 score%%

![image](https://user-images.githubusercontent.com/86040099/123498922-dc41a100-d66d-11eb-9809-6b10f9faea70.png)

%%가장 높은 확률을 나타내는 score에 해당되는 열의 숫자와 대응되는 classes 검출%%

![image](https://user-images.githubusercontent.com/86040099/123498973-3f333800-d66e-11eb-850c-6cad3bffc3a2.png)

%%Plot%%

![image](https://user-images.githubusercontent.com/86040099/123498799-fd55c200-d66c-11eb-8101-48208619e070.png)

# - 카메라의 영상을 연속해서 분류하기
카메라의 영상을 연속해서 분류하려면 위 단계들을 루프 내에 포함시키십시오. Figure를 열어 둔 상태로 루프를 실행합니다. 실시간 예측을 중지하려면 Figure를 닫으십시오. 각 반복의 끝에서 drawnow를 사용하여 Figure를 업데이트합니다.

![image](https://user-images.githubusercontent.com/86040099/123499029-b5d03580-d66e-11eb-82ab-b31157745cff.png)

https://user-images.githubusercontent.com/86040099/123499268-7dc9f200-d670-11eb-818a-edcca47b0304.mp4


