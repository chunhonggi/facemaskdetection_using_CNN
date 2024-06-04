# resnet50_mask_detection

# ! git clone https://github.com/aqeelanwar/MaskTheFace.git
마스크를 쓴 이미지 파일을 구하는 것이 쉽지 않아서 위를 통해 mask를 끼지 않은 파일을, 마스크를 착용하도록 만들 수 있었다. 
이때, MaskTheFace 이용시 random한 mask를 사용하면 train_data, valid_data가 좋지 못할 수 있으니 일상생활에 자주 보이는 마스크 위주로 선별하였다.

트레이닝시 resnet50을 활용하였고, config에 하이퍼파라미터를 설정 해두었다. 

<img width="469" alt="image" src="https://github.com/chunhonggi/resnet50_mask_detection/assets/83743927/6b15f7a4-143d-4925-8775-fb5bb8018ffd">
<img width="465" alt="image" src="https://github.com/chunhonggi/resnet50_mask_detection/assets/83743927/93b2d5ee-b285-4c1a-a0be-ebd354f70bdf">

training과 validation을 한 반복문 내에서 처리하였고, 값을 따롸 wandb와 plot을 이용해 roc curve를 확인하였다. 
