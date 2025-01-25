# 삽관 및 발관 데이터 전처리 및 머신러닝 데이터셋 생성
## 프로젝트 설명
MIMIC-IV 데이터셋을 활용하여 발관 실패 예측 연구를 위해 머신러닝에 적용 가능한 데이터셋을 구축하는 과정을 담고 있습니다. MIMIC-IV는 하버드 의과대학과 MIT에서 개발한 중환자실(ICU) 데이터셋으로, 약 40,000명 이상의 중환자 데이터를 포함합니다.

본 프로젝트에서는 MIMIC-IV 데이터셋에서 삽관(Intubation) 및 발관(Extubation) 이벤트를 중심으로 데이터를 전처리하여 환자별로 정리된 머신러닝 학습용 데이터셋을 생성하였습니다. 또한, 원본 데이터뿐만 아니라 추가적인 변수(Unable)를 포함하여 데이터셋을 확장하고 이를 통해 발관 실패 예측 연구에 활용 가능한 데이터셋을 구축하는 데 초점을 맞췄습니다.

-------------
- **`before_00_alignment_delete_row_withflag_before.ipynb`**  
원본 데이터를 병합하고 중복 오류(ex.삽관-삽관-발관이 나타남)를 해결한 뒤 삽관/발관 이벤트를 페어링하고, 중환자실 입·퇴실 정보를 활용해 결측 데이터를 보완합니다.
- **`before_01_coulmn_creat.ipynb`**  
특정 기간 동안(삽관 시점~발관 시점)에 기록된 vital signs, ventilator settings, GCS(Glasgow Coma Scale), ABGA(arterial blood gas analysis) 데이터를 통합하여 이후 머신러닝 모델 학습에 사용할 수 있는 정제된 형태의 테이블을 구축하였습니다.

- **`after_00_unable_add_intu_extu_stay_id.ipynb`**  
Unable 데이터를 활용해 삽관과 발관 데이터를 생성하고 이를 원본 삽/발관 데이터와 결합합니다. Unable은 환자가 GCS 점수의 Verbal 영역을 측정할 수 없는 상태를 나타내며 이 정보를 이용해 삽관 시작 시간과 발관 종료 시간을 추정합니다. 만들어진 데이터는 환자별 시계열 정보로 정리되어 기존 데이터와 합쳐집니다.
- **`after_01_alignment_delete_row_withflag.ipynb`**  
삽관 발관이 중복되는 데이터 오류(ex.삽관-삽관-발관이 나타남)를 flag를 사용해 식별하고 해결합니다. 이후에도 비어 있는 데이터가 남아 있는 경우, 중환자실 입·퇴실 정보를 활용해 결측 데이터를 보완합니다.
- **`after_02_coulmn_creat.ipynb`**  
특정 기간 동안(삽관 시점~발관 시점)에 기록된 vital signs, ventilator settings, GCS, ABGA 데이터를 통합하여이후 머신러닝 모델 학습에 사용할 수 있는 정제된 형태의 테이블을 구축하였습니다.
