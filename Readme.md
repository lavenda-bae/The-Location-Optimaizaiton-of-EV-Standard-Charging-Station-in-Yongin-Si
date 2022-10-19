# 2022 BIGCONTEST


## 🚘 용인시 전기차  완속 충전소 입지 선정 모델 개발

- 프로젝트 진행기간 : 2022. 09. 22 ~ 2022. 10. 14
- 역할 
    - 여민희
    - 유한솔
    - 윤병윤
    - 이재엽
    - 전은성
- 용인시 지역 특성을 반영한 객관적인 최적의 충전소 입지선정지수 개발 및 이를 통한 충전소 최적화 모델 구축
- 데이터셋
    - 빅콘테스트 데이터셋 : ev_app_resident(2022.6.1~ 2022. 6.30 까지의 용인시 거주자의 전기차 앱실행 고객수),ev_app_activity(2022.6.1~ 2022. 6.30 까지의 용인시 유동인구의 전기차 앱실행 고객수), ev_app_activity_resident(2022.6.1~ 2022. 6.30 까지의 용인시 거주자의 타지역 전기차 앱실행 고객수)
     
- Process
    - 사용 툴 : Python, QGIS
    - EDA
    - Preprocess
    - 지수 추출
    x_score = w1 * x1 + w2 * x2
    >Y  : 격자 당 LG U+ 전기차 앱 실행 수 , x1 : 격자 당 인구 밀도, x2 : 격자 당 전기차 등록 대수(추정)
    
        - 목적 : 데이터를 활용하여 완충형 전기차 충전소 입지 선정을 위한 지수 개발 후, 최적의 입지 추천
        - 방법
            - 수요 요인, 접근성 요인, 부지 적합성 요인을 이용
            - 전기차 충전 어플리케이션 실행 위치를 전기차 충전에 대한 수요라고 가정
            - 100m 격자 당 인구 수와 전기차 등록 대수와의 상관관계를 분석하여 수요 지수를 도출
    - 변수간 상관관계 (주유소 위치, 자동차 등록 대수, 인구 수, 용인시 거주자 기준 app 실행수)
    : 수요에 대해서 얼마나 관계성이 있는지 확인하고 그 비중을 가지고 수요 지수 도출
     (상관관계가 적을 경우 제외(0.2 이하))
    - MCLP(Maximal Covering Location Problem)
    : 주어진 제약조건 하에서 시설물이 커버하는 수요량을 최대화하는 위치를 선정
    
    <p align="center"><img src="https://i.stack.imgur.com/ptOaG.png" width="450" height="600"></p>
    
    참고 자료 : [https://stackoverflow.com/questions/51501074/implementing-mclp-in-pulp](https://stackoverflow.com/questions/51501074/implementing-mclp-in-pulp)
    
    - MCLP로 선정된 후보 지역 중 많이 겹치는 부분을 최적의 충전소 입지라고 판단
    
    <img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/1cfde524-87f4-4d6c-99fb-a491bb2fe7ae/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20221018%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20221018T055740Z&X-Amz-Expires=86400&X-Amz-Signature=6d4ab98fd609d65f3e233373ee640e3587b39c2637dcbe30fec73a08023450bc&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width="400" height="370">
    

