# 베이커리 구매 데이터 분석 및 마케팅 전략 수립

## 프로젝트 개요
이 프로젝트는 베이커리 매장의 구매 데이터를 분석하여 고객의 소비 패턴을 파악하고, 시계열 분석 및 장바구니 분석을 통해 효과적인 마케팅 전략을 수립하는 것을 목표로 합니다.

**배경**  
- 베이커리 매출 증대를 위한 데이터 기반 마케팅 전략 필요  
- 매출 뿐만 아니라 고객 만족도까지 향상시켜 장기적인 발전 추구가 요구됨
<br>

**목표**  
1. 구매량 및 시계열 분석을 통해 인기 상품과 시간대별 소비 패턴 도출  
2. 장바구니 분석을 통해 연관성이 높은 상품 조합 파악  
3. 분석 결과를 바탕으로 최적의 마케팅 전략 제안  
<br>

## 사용한 기술 & 도구  
- **언어:** Python  
- **데이터 처리:** Pandas, NumPy  
- **시각화:** Matplotlib, Seaborn  
- **시계열 분석:** Time Series Analysis  
- **장바구니 분석:** FP-Growth Algorithm (연관규칙 마이닝)  
<br>

## 프로젝트 진행 과정  

### 1) 데이터 탐색 및 전처리  
- 총 20,507개의 거래 데이터 활용  
- 주요 컬럼: `거래 ID`, `구매 상품명`, `거래 일시`, `구매 시간대`, `주중/주말 여부`  
- 결측치는 존재하지 않으며, 모든 변수가 명목형이므로 이상값 처리 불필요  
- 동일한 거래 ID 내에서 같은 상품이 반복될 경우 **구매 수량(Quantity) 컬럼 추가**  
<br>

### 2) 구매량 및 시계열 데이터 분석  
- **구매량 TOP 5 상품 분석**  
  - 커피의 구매량이 압도적으로 높음  
  - 빵, 패스트리, 케이크, 차가 그 뒤를 이음  
  - 모든 상품에서 **오전 구매량이 높고, 16시 이후 급감**  

- **시간대별 구매 패턴 분석**  
  - 커피, 빵, 패스트리는 오전에 구매량이 높음  
  - 케이크, 차는 오후에 더 많이 판매됨  
  - 점심 이후 (13시~15시) 케이크 및 차의 구매량 증가  
<br>

### 3) 장바구니 분석 (FP-Growth Algorithm)  
- 고객 ID가 존재하지 않아 **Prefix 알고리즘 대신 FP-Growth 적용**  
- 신뢰도를 0.2로 조정하여 다양한 연관 규칙 도출  
- **상위 5개 연관 규칙:**  

| Antecedents (구매 상품) | Consequents (연관 상품) | Support | Confidence | Lift |
|-----------------|-----------------|---------|------------|------|
| Tea, Coffee     | Cake            | 0.01    | 0.20       | 1.94 |
| Cake           | Tea             | 0.02    | 0.23       | 1.60 |
| Toast          | Coffee          | 0.02    | 0.70       | 1.47 |
| Sandwich       | Tea             | 0.01    | 0.20       | 1.40 |
| Spanish Brunch | Coffee          | 0.01    | 0.60       | 1.25 |
<br>

## 마케팅 전략 제안  

| 전략 | 내용 | 기대 효과 |
|------|------|----------|
| **세트 상품 출시** | 스페인식 브런치 + 케이크 + 커피 세트 출시 (오후 시간대 한정 할인) | 구매 연관성이 높은 상품 조합으로 매출 증대 |
| **오전 프로모션** | 커피, 빵, 패스트리 구매 시 할인 이벤트 진행 | 오전 피크타임 매출 극대화 |
| **케이크 & 차 프로모션** | 케이크 또는 샌드위치 2개 이상 구매 시 티백 증정 이벤트 | 차 상품에 대한 바이럴 효과 창출 |
| **런치 디저트 세트 출시** | 13시~15시 점심 직후 케이크 + 차 세트 할인 제공 | 점심 직후 구매 증가 유도 |
<br>

## 결과 및 성과  
✔ 구매 패턴 분석을 통해 최적의 마케팅 전략 수립  
✔ 세트 상품 및 프로모션을 통해 추가적인 매출 상승 기대  
✔ FP-Growth 기반의 장바구니 분석을 활용하여 연관 상품 조합 발굴  
<br>

## 배운 점 & 회고
- 베이커리 매장의 구매 패턴을 분석하며 **시간대별 소비 트렌드의 중요성**을 체감  
- FP-Growth 알고리즘을 활용한 연관 분석의 효과적인 적용 가능성 확인  
- 향후 **고객 세그먼트 분석을 추가하여 개인화 마케팅 전략 강화 가능**

---
- 코드 확인 : [코드 보러가기](https://github.com/harrym8n/Proj_Bakery_DA/blob/main/Bakery_data_analysis.ipynb)
- PDF 보고서 확인 : [PDF 보고서 보러가기](https://github.com/harrym8n/Proj_Bakery_DA/blob/main/Bakery_data_analysis_report.pdf)
 
