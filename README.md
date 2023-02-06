## Blood pressure and heart rate measurement using smartphone video camera  
#### 스마트폰 비디오 카메라를 활용한 혈압, 심박수 측정
---

광적용맥파(Photoplethysmogram, 이하 PPG)의 원리를 이용하여 스마트폰으로 심박수와 혈압을 측정할 수 있는  
방법에 대해서 연구를 진행했었습니다. 연구 목표로는 애플워치나 갤럭시 워치 등 고가의 웨어러블 디바이스를  
구매해야한다는 단점에서 벗어나 누구나 손쉽게 헬스케어 서비스를 받을 수 있게하자는 목표로 진행하였습니다.  
본 연구에서는 PPG 신호의 원리를 스마트폰 카메라에 적용하여 알고리즘을 구현하였으며  
보다 높은 정확도 향상을 목적으로 직접 다양한 실험을 통해 최적의 BPF(Band-Pass Filter)를 설계하였습니다.  

WHAT IS PPG?
---

![image](https://user-images.githubusercontent.com/75806377/216873529-fbdedfb0-c9c1-4efd-9d7f-36f510878c63.png)

PPG 신호는 웨어러블 기기, 병원용 맥박 측정기 등 다양하게 사용되고 있는데요.  
피부에 빛을 쏠 때 혈류량에 따라 흡수되는 빛의 양이 달라지는 원리에 기반하고 있습니다.  

신체는 심장박동에 의하여 생성된 압력에 의해 혈관 내에서 혈액의 흐름이 생기게되며    
심장박동이 발생할 때마다 압력은 신체의 말단 모세혈관까지 작용하여 이는 손가락 끝의 혈관까지도 압력이 작용합니다.  
손가락 끝 모세혈관의 동맥 혈액은 세포조직으로 혈액을 공급하고, 정맥으로 들어가서 다시 심장으로 돌아가는데요.  
결국, 심장박동에 동기되어 손가락 끝 혈관에서의 동맥혈량이 증가하고 줄어드는 것이 계속 반복됩니다.

동맥에 피가 많이 흐를 때는 동맥혈에서 더 많은 빛을 흡수하고 동맥에 적게 흐를 때에는 혈관에서 상대적으로 빛이 덜 흡수되는  
흡수량의 추이를 통해 심박수와 혈압을 측정하는 방식입니다.

SMARTPHONE VIDEO CAMERA
---
<p align="center"><img src="https://user-images.githubusercontent.com/75806377/216887119-1d05ac22-de7b-4eed-a57b-7bdd782993f6.gif" height="300px" width="1000px"></p>  

위의 영상이 스마트폰 비디오 카메라로 촬영한 동영상입니다.  
촬영하는 원리는 스마트폰의 플래시를 활성화한채로 플래시부분과 카메라 센서를 동시에 손가락으로 감싸 영상을 촬영합니다.  
영상을 보시면 빨간 배경에 반복적으로 살짝 어두워졌다가 밝아지기를 반복하는 패턴이 보입니다!

HEART RATE MEASUREMENT
---
심박수를 측정하는 원리는 크게 4단계로 이루어집니다.  

<p align="center"><img src="https://user-images.githubusercontent.com/75806377/216889541-5676187d-087c-4361-8367-f6479a9e9bb8.png" height="300px" width="500px"></p>

1. Average red intensity per frame - frame 당 평균 R값(Red)을 계산합니다.  
2. Peak detection algorithm - 주기적으로 나타나는 뾰족한 peak를 찾아냅니다.  
3. R-R interval(RRI) - Peak 사이의 시간 간격을 의미하는 RRI를 계산합니다.  
4. 60/RRI - 구한 RRI를 사용하여 60/RRI를 하게되면 심박수를 계산할 수 있습니다.  


