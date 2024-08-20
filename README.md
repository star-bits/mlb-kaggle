# 구글머신러닝부트캠프 캐글 기록

## RSNA 2024 LSDC

1. 직접 만든 dcm2png conversion, 나머지는 itk8191 그대로 (Pulbic Score 0.65)
- [rsna24lsdc_0815_eda_dcm2png.ipynb](https://github.com/star-bits/mlb-kaggle/blob/main/rsna24lsdc_0815_eda_dcm2png.ipynb): 좌표 있는 이미지는 반드시 포함, Sagittal T1 10개 Sagittal T2/STIR 10개 Axial T2 20개씩
- [rsna24lsdc-0816-train.ipynb](https://github.com/star-bits/mlb-kaggle/blob/main/rsna24lsdc-0816-train.ipynb)
- [rsna24lsdc-0817-submission.ipynb](https://github.com/star-bits/mlb-kaggle/blob/main/rsna24lsdc-0817-submission.ipynb)

2. edgenext_base.in21k_ft_in1k 모델을 사용 (Pulic Score 0.60)
- [rsna24lsdc-0816-train (edgenext).ipynb](https://github.com/star-bits/mlb-kaggle/blob/main/rsna24lsdc-0816-train%20(edgenext).ipynb)

3. Augmentation을 간소화하고 base model은 freeze하되 classification module만 훈련
