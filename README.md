# 🚢 PortStructureObject_SemiSupervised_Segmentation

준지도학습 기반의 항만 구조물 객체 분할 문제 (2022/06/07~2022/06/21)

### Description

항만에서 촬영된 구조물에 대한 객체를 분할(segmentation)하는 문제

segmentation 태스크를 위한 데이터 구축에 많은 비용이 발생함에 따라 <br/>
비교적 저렴한 레이블만 가진 데이터를 추가로 활용하여 <br/>
동일 태스크를 수행할 수 있는 semi-supervised 학습 모델 개발의 필요성이 대두됨에 따라 진행하였습니다.

즉, 일부 이미지만 label이 있고, 남은 이미지들을 AI 모델을 통하여 라벨링하는 task입니다.

평가지표 mIoU 기준으로 최대 0.8520 정도의 성능을 보였습니다.

- mIoU (Mean Intersection over Union): 각 클래스의 IoU의 평균

### What did I do

이미지 데이터 처리 및 모델 개발

해당 문제에서 사전학습모델을 사용할 수 있어서 Detectron2를 사용하였습니다. <br />
Self - Training을 시켜 일정 기준 이상으로 labeling 된 데이터를 <br/>
다음 round의 학습에서 추가하는 방식으로 문제를 해결했습니다. <br />

현 시점에서 아쉬운건 준지도학습과 셀프 트레이닝에 대한 자료조사를 <br/>
깊게 진행한 후, MMSegmentation 등의 더 좋은 사전학습 모델과 방법을 채택 했어야 하는 점입니다. <br/>
데이터 증강에 있어 Mixcut 등의 방식도 이용하였으나, 성능 하락이 있었기에 제외했습니다. <br/>
최대한 정확히 마스킹된 픽셀 영역을 얻는 것이 목표였음으로 다른 클래스끼리 섞이는 것이 오히려 악영향을 주었다고 판단합니다. <br/>
