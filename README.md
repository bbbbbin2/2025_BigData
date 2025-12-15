# 🚗 🚦 교통사고 통계 분석 및 향후 사고 건수 예측

---

## 📌 프로젝트 개요

본 프로젝트는 **최근 10년간(2015~2024) 교통사고 통계 데이터**를 기반으로
교통사고 발생 추세와 구조적 위험 요인을 다각도로 분석하고,

> **“교통사고는 실제로 줄어들고 있는가?”**
> **“어떤 집단과 조건에서 사고 위험이 집중되는가?”**
> **“현재 추세가 유지된다면 향후 사고 건수는 어떻게 변화할 것인가?”**

를 데이터 기반으로 검증·예측하는 것을 목표로 합니다.

단순 통계 요약에 그치지 않고,
**연령·지역·위반 유형·사고 유형·기상 상태·시간 흐름**을 종합적으로 분석하였으며,
**Prophet / LSTM 기반 시계열 모델**을 활용하여 **향후 5년간 교통사고 추세를 예측**했습니다.

---

## 📁 프로젝트 폴더 구성

```
2025_BigData/
├─ data/
│   ├─ 교통사고통계(연도별).xlsx
│   ├─ 교통사고통계(월별).xlsx
│   ├─ 교통사고통계(기상상태별).xlsx
│   ├─ 사고유형별_교통사고.xls
│   ├─ 위반유형별_교통사고.xls
│   ├─ 연령대별_교통사고.xls
│   ├─ 지역별_교통사고.xls
│   ├─ 음주운전(지역)교통사고통계.xlsx
│   ├─ 교통사고통계(음주 3년간).xlsx
│   └─ 화물차.csv
│
├─ notebook/
│   ├─ 전처리.ipynb
│   ├─ 교통사고_통계_및_예측_시각화.ipynb
│   ├─ 음주교통사고_시각화.ipynb
│   └─ 화물차_교통사고_시각화.ipynb
│
├─ README.md
└─ 빅데이터_예측_이혜빈_202344100.pdf
```

---

## 📦 사용 데이터

| 구분       | 설명                   |
| -------- | -------------------- |
| 연도별 교통사고 | 사고·사망자·부상자 연도별 추이    |
| 월별 교통사고  | 계절성 및 월별 사고 패턴       |
| 사고 유형별   | 차대차, 차대사람 등          |
| 위반 유형별   | 안전운전의무위반, 신호위반, 과속 등 |
| 연령대별     | 10대~65세 이상 사고 분포     |
| 지역별      | 시·도별 사고 집중도          |
| 기상 상태별   | 맑음·비·눈·안개            |
| 음주운전     | 연령·지역·시간대별 음주사고      |
| 화물차 사고   | 사고 다발 지역 분석          |

---

## 🔧 기술 스택

* **Python**
* **Pandas / NumPy** : 데이터 처리 및 전처리
* **Matplotlib / Seaborn / Folium** : 시각화
* **Prophet** : 단기 시계열 예측
* **LSTM (TensorFlow / Keras)** : 장기 추세 예측
* **scikit-learn**
* **MySQL / CSV** (저장 및 관리)

---

## 🔍 분석 절차 요약

### 1️⃣ 데이터 전처리

* 병합 셀(Merged Cells)로 인한 `Unnamed` 컬럼 제거
* 다중 헤더 정규화
* 결측치(NaN) 제거
* 문자형 숫자 → 정수형 변환
* 합계/알 수 없음 행 제거
* 지역명 불일치 통합 (예: 서울특별시 → 서울)
* Wide → Long 형태 변환(Unpivot)
* 공통 전처리 함수화 적용

---

### 2️⃣ 주요 시각화 항목

* 최근 10년 교통사고 사망자·부상자 추이
<img width="1565" height="547" alt="image" src="https://github.com/user-attachments/assets/414980d5-5d97-4856-9787-1b622c382edd" />

* 최근 5년 월별 평균 사고 건수
<img width="1266" height="466" alt="image" src="https://github.com/user-attachments/assets/1c61d14c-325b-4506-98b0-4b63981b55d9" />
<img width="1266" height="466" alt="image" src="https://github.com/user-attachments/assets/0a10b36f-116a-4ef5-8170-0014c685ebde" />

* 월별 교통사고 치명도 Top 3
<img width="1166" height="466" alt="image" src="https://github.com/user-attachments/assets/4ddc0c93-99d1-4c39-aec0-1e4d54d67027" />
<img width="1166" height="466" alt="image" src="https://github.com/user-attachments/assets/3dc2a883-abb7-4a59-804a-b89d93acae4f" />

* 기상 상태별 사고 비중 및 치명도
<img width="966" height="566" alt="image" src="https://github.com/user-attachments/assets/f1bcfd9f-06be-44bf-a9be-156169a2a814" />
<img width="766" height="466" alt="image" src="https://github.com/user-attachments/assets/93309f2e-fa28-4b9b-9f4b-17123d199262" />
<img width="1366" height="566" alt="image" src="https://github.com/user-attachments/assets/774850b6-6d42-40ba-9aa1-fbd6bea52388" />

* 연령대 사고 집중도
  <img width="966" height="766" alt="image" src="https://github.com/user-attachments/assets/53bb2aca-1c5e-4d0e-ba66-a51fd970c225" />
  <img width="966" height="566" alt="image" src="https://github.com/user-attachments/assets/fbb900b9-ed48-45b4-a045-4fc953746f43" />

* 65세 이상 운전자 연도별 교통사고 증가율 

  <img width="966" height="466" alt="image" src="https://github.com/user-attachments/assets/d90a342b-7442-4970-9820-8beb674ce060" />

·지역별 사고 집중도
  <img width="966" height="765" alt="image" src="https://github.com/user-attachments/assets/d9b8f59a-bebd-455c-bece-6780ac67efc6" />

* 사고 유형별 / 위반 유형별 통계
* <img width="966" height="766" alt="image" src="https://github.com/user-attachments/assets/bfa66e64-1b80-477a-8b9e-b23a106a0289" />
<img width="966" height="766" alt="image" src="https://github.com/user-attachments/assets/81498eb7-d528-450d-ac5b-27695ef0a62d" />

* 음주운전 사고 시간대·연령대 분석
<img width="995" height="814" alt="image" src="https://github.com/user-attachments/assets/f352073c-0fe7-4461-a7a7-819b792e1488" />
<img width="908" height="583" alt="image" src="https://github.com/user-attachments/assets/bbf48986-dc76-45b2-98a3-ea9873e2ae13" />
<img width="965" height="566" alt="image" src="https://github.com/user-attachments/assets/825031d2-ba56-45c2-bc24-ebadb71288e0" />
<img width="965" height="765" alt="image" src="https://github.com/user-attachments/assets/2bdd07ce-f10d-48f7-b0d0-b1c75abaab8f" />
<img width="1276" height="765" alt="image" src="https://github.com/user-attachments/assets/6fa37c07-7710-4747-982f-61b4d82bc66d" />



* 화물차 사고 다발 지역 지도 시각화
<img width="1266" height="766" alt="image" src="https://github.com/user-attachments/assets/fa084a6e-e49d-4e91-8d03-0bb907cf927a" />
<img width="966" height="766" alt="image" src="https://github.com/user-attachments/assets/6f597ce5-109b-42ea-9805-6954fb71359d" />
 Make this Notebook Trusted to load map: File -> Trust Notebook
<img width="1184" height="1178" alt="image" src="https://github.com/user-attachments/assets/9801b3b5-80df-48fc-9e85-21494a3c547e" />
<img width="1641" height="1232" alt="image" src="https://github.com/user-attachments/assets/1fe4063a-149f-403e-9100-a522c5b0a392" />
* 확대시 정확한 위치 및 건수 확인 가능
<img width="888" height="604" alt="image" src="https://github.com/user-attachments/assets/469bdf71-fe94-4736-906a-556718a35401" />



---

## 📊 주요 분석 결과

### 🔹 1) 연령대별 사고 특징

* **65세 이상**에서 사고 비중이 높음
* 고령 운전자(65세 이상)는 **최근 5년간 사고 증가율이 지속 상승**

---

### 🔹 2) 위반 유형별 영향

* 모든 연령대에서 **안전운전의무 불이행**이 가장 큰 사고 원인
* 20~40대는 **신호위반·중앙선 침범** 등 복합 위반 비중이 큼

---

### 🔹 3) 기상 상태 영향

* 사고 발생 비중: **비·흐림 날씨**에서 사고 다수 발생
* 사고 치명도: **눈길 사고**는 발생 빈도는 낮지만 치명도 최고

---

### 🔹 4) 지역별 사고 집중

* 최근 5년간 사고의 **절반 이상이 수도권(경기·서울)** 집중
* 교통량·도시 구조와 밀접한 상관관계 확인

---

## 🔮 예측 모델 설계

### 📈 예측 모델 ① — Prophet 기반 시계열 예측

* **Input**: 연도별 사고 건수
* **Output**: 향후 5년 사고 발생량
* **결과**

  * 사고 건수·사망자 수 모두 **완만한 감소 추세 지속**
  * 급격한 반등 가능성은 낮음

---

### 📈 예측 모델 ② — LSTM 기반 장기 예측

* 비선형 구조 학습
* 정책·고령화·교통 환경 변화 반영 가능
* **장기적으로 구조적 감소 흐름 유지** 시사

---

## 🧪 프로젝트 의미 및 시사점

* 교통사고는 **단일 요인이 아닌 복합적 구조 문제**
* 고위험군(연령·시간대·위반 유형) 중심 정책 필요
* 기상 조건을 고려한 **사전 경고·예방 시스템** 활용 가능
* 데이터 기반 사고 예측은 **지자체 교통 정책 수립에 실질적 기여 가능**

---

## 📁 산출물

* 전처리 및 분석 노트북 (`.ipynb`)
* 정제된 교통사고 통계 데이터
* 시각화 결과 이미지
* 프로젝트 발표 자료 (PDF)

---

## 🔚 종합 결론

교통사고는 전반적으로 감소 추세에 있으나,
**특정 연령대·시간대·기상 조건·사고 유형에 집중되는 구조적 특성**을 보입니다.

따라서 향후 교통안전 정책은
단순 사고 건수 감소를 넘어,

* 고위험군 맞춤형 관리
* 보행자 보호 중심 도시 교통 환경 개선
* 데이터 기반 예측·선제 대응

으로 확장될 필요가 있습니다.

---

