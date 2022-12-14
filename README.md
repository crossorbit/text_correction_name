# Text Correction - fastText 활용한 OCR 오인식 보안 
  
[목적]
- 주민등록증, 가족관계증명서 등 행정서류에서 이름 추출하여 OCR 변환 시, 오인식으로 잘못된 정보 처리될 수 있음(e.g. 홍길동 -> 홈길동 등)
- 대한민국 성씨 기준으로 99.7%를 차지하는 111개 성을 기준으로 fastText 통해 학습하여 **사전에 등록된 단어(성)로 변환**하여 정확도 향상  
  &rarr; 2자리 성씨의 경우(제갈, 사공, 선우, 남궁, 서문, 황보 등) ROI Detection 된 글자에서 **2자리 성 대상을 알수 없어 첫번째 자리만 비교할 수 있는 제한적 적용**

[적용 결과]
- 1글자 비교이다 보니, 정확도 낮음
    > 깁 -> 백, 깉 -> 탁 처럼 초성+중성 비슷한 것 보다 초성+종성 비슷한게 더 score 높음
<img width="535" alt="스크린샷 2022-09-01 오후 8 32 02" src="https://user-images.githubusercontent.com/54519026/187904301-8ab0fe1d-4005-4160-bd9c-6071db838a51.png">
