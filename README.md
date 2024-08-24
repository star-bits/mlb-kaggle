# 구글머신러닝부트캠프 캐글 기록

## RSNA 2024 LSDC

1. 직접 만든 dcm2png conversion, 나머지는 itk8191 그대로 (Public Score 0.65, CV Score 0.67)
- [rsna24lsdc_0815_eda_dcm2png.ipynb](https://github.com/star-bits/mlb-kaggle/blob/main/rsna24lsdc_0815_eda_dcm2png.ipynb): 좌표 있는 이미지는 반드시 포함, Sagittal T1 10개 Sagittal T2/STIR 10개 Axial T2 20개씩
- [rsna24lsdc-0816-train.ipynb](https://github.com/star-bits/mlb-kaggle/blob/main/rsna24lsdc-0816-train.ipynb)
- [rsna24lsdc-0817-submission.ipynb](https://github.com/star-bits/mlb-kaggle/blob/main/rsna24lsdc-0817-submission.ipynb)

2. edgenext_base.in21k_ft_in1k 모델을 사용 (Public Score 0.60, CV Score 0.63)
- [rsna24lsdc-0816-train (edgenext).ipynb](https://github.com/star-bits/mlb-kaggle/blob/main/rsna24lsdc-0816-train%20(edgenext).ipynb)

3. Base model을 그대로 사용하지 않고 base model의 아웃풋 feature map에다 conv+fc의 classification module을 추가함. (Classification module을 추가했을 때 CV Score가 0.01정도 좋아짐. Base model을 freeze하고 classification module만 train했을 때는 점수가 확 나빠짐.) Augmentation을 수정함. (인풋 이미지 사이즈를 512x512에서 224x224로 줄이면 CV Score가 0.01정도 나빠지지만 1 epoch당 시간이 약 3분에서 약 1분 30초로 줄음 - Colab L4 기준.) (Public Score 0.60, CV Score 0.61)
- [rsna24lsdc0823train.ipynb](https://github.com/star-bits/mlb-kaggle/blob/main/rsna24lsdc0823train.ipynb)
- [rsna24lsdc0823submission.ipynb](https://github.com/star-bits/mlb-kaggle/blob/main/rsna24lsdc0823submission.ipynb)

4. Base model을 edgenext_base.in21k_ft_in1k와 크기가 비슷한 convnextv2_tiny.fcmae_ft_in22k_in1k나 10배 가량 큰 convnextv2_large.fcmae_ft_in22k_in1k를 사용했을 때 점수가 더 나쁘게 나옴. Learning rate 문제인가 싶어 graidient accumulation 파트를 걷어내고 learning rate를 조정함.

