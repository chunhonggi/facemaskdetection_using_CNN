# resnet50_mask_detection
일반적 모델의 학습 목적은 in에서 out으로 mapping하기 위한 적합한 함수를 찾는 방식으로 진행하는것이라고 할 수 있다. 
따라서 image classification의 경우 적합한 함수 H(x)-x가 최소화 되는 방향으로 학습을 진행해야 하는 것이다. 이는 결국 x가 H(x)가 되도록 학습시키는 것과 같은 의미이다. 
하지만 이 과정에서 vanishing gradient와 같은 문제가 발생할 수 있으니 F(x)=H(x)-x로 두고 F(x)+x가 H(x);x 가 되도록 학습 시키는 것이다. +x를 통해 vanishing gradient를 피할 수 있게 된다. 
<img width="644" alt="image" src="https://github.com/chunhonggi/resnet50_mask_detection/assets/83743927/c5ac9f5b-41f6-421b-867d-91d71c84385b">
이때, 그냥 x를 더하는 과정이 identical block, conv 진행 후 더하는 방법이 convolution block이다. 
<img width="674" alt="image" src="https://github.com/chunhonggi/resnet50_mask_detection/assets/83743927/1c002102-16b8-4bf5-a256-c0e18c54be69">
최종적으로 resnet은 위 블록을 번갈아 배열하며 학습을 시키는 과정이다. 
# ! git clone https://github.com/aqeelanwar/MaskTheFace.git
마스크를 쓴 이미지 파일을 구하는 것이 쉽지 않아서 위를 통해 mask를 끼지 않은 파일을, 마스크를 착용하도록 만들 수 있었다. 
이때, MaskTheFace 이용시 random한 mask를 사용하면 train_data, valid_data가 좋지 못할 수 있으니 일상생활에 자주 보이는 마스크 위주로 선별하였다.

트레이닝시 resnet50을 활용하였고, config에 하이퍼파라미터를 설정 해두었다. 

<img width="469" alt="image" src="https://github.com/chunhonggi/resnet50_mask_detection/assets/83743927/6b15f7a4-143d-4925-8775-fb5bb8018ffd">
<img width="465" alt="image" src="https://github.com/chunhonggi/resnet50_mask_detection/assets/83743927/93b2d5ee-b285-4c1a-a0be-ebd354f70bdf">

training과 validation을 한 반복문 내에서 처리하였고, 값을 따롸 wandb와 plot을 이용해 roc curve를 확인하였다. 
