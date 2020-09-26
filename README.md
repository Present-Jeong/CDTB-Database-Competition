# CDTB-Database 데이터 정리
웨어러블 디바이스를 이용한 파킨슨 병 조기 진단 솔루션 Feature Engineering
최근 업데이트 : 2020년 09월 26일

이 Repository는 고려대학교 CDTB 데이터 경진대회용 데이터 입니다.
먼저, 파킨슨 병의 조기 진단 및 예측에 필요한 데이터 수집하였습니다.
데이터는 설문용 데이터(설문조사)와 측정용 데이터(디바이스)로 나누었습니다.
1. 설문조사 데이터는 질문에 대한 증상 Severity에 따라 0~5의 class로 나누어져 있고
2. 측정용 데이터는 어플, 웨어러블 디바이스, TAP-PD(OPDM) 등의 기기로 측정한 데이터로 양,음 유리수로 이루어져있습니다. (ex. -4.1928, 3.7154 .. )
데이터 수는 가지고 있는 csv file을 기준으로 130 ~ 14000개의 데이터로 주제, 파일에따라 상이합니다.

웨어러블 디바이스로 측정 가능한 의심 증상으로,
1. Digitor Sensors (tap, Eligibility 등 ..) csv file 6개
2. Motor Assessments (Arm Swing, MDS_UPDRS 1~4, Questionnarie, TAP-PD 등..) csv file 11개
3. Sleep Disorders (Sleepniss scale, REM Sleep Disorder Questionnarie) csv file 2개
로 이루어져 있고, 이 중 Dirty CSV file는 사용하기 않기로 결정 했습니다.

데이터의 전처리 과정으로,
1. Useless Column 제거
2. NaN 값 전부 제거 (한가지의 Column에라도 NaN값이 있다면, 전부 제거)
3. 데이터 갯수 확인 , data describe (.value_counts, .describe)
4. Label Column 분리 (Train data, Target data 분리)
5. Simple data visualization (Matplotlib, Mean describe, Data counts)
6. Train Validation Test split (6:2:2 split 예정)
이는 기본적인 전처리 과정이며, 이후 추가적으로 데이터를 분석할 예정

논의 필요 상황
1. 현재 수집한 데이터 중, 일부 Dirty CSV file은 제거한 상황입니다. 제거한 CSV file에 대하여 다시한번 점검하고, 확인하는것이 필요함.
2. Motor Assessment 중에서 MDS_UPDRS는 Patient가 거의 상의하고, Questionnarie에서 데이터 유사성을 발견하였습니다. 데이터 결합에 대해 논의 필요
3. MDS_UPDRS의 3,4번은 Lenodopa라는 약물 복용 전 후 데이터이며, 프로젝트 방향성을 생각했을 때, 확인할 필요가 있습니다.
4. Label 데이터를 정확히 발견할 필요가 있음 
  4-1. COHORT가 Label 값인가? 무슨 Column이 Label 값인가.
  4-2. Label 값이 존재하지 않거나, Patient Status라는 csv 파일에 Label이 있는 경우가 있음.
  4-3. Label을 뜻하는 Classification 자체가 Feature값에 들어가있는경우가 있음
5. 자세하고 구체적인 전처리 및 분석과정이 필요함.
6. 모델 수립, CSV 데이터 모델 융합등을 생각해보아야함.

+) 뇌 영상 사진 추가 업데이트 예정
