# 🤖 ROS2 기반 라인트레이싱 및 ArUco 인식 서비스 로봇 시스템

> ROS2 기반 자율주행(라인트레이싱)과 ArUco 마커 인식을 통해 로봇팔의 Pick & Place 작업을 수행하는 **서비스 로봇 시스템**입니다.  
> 본 프로젝트는 시나리오보다는 **핵심 기능 구현 및 코드 최적화**에 중점을 두었습니다.

---

### 🔹 주제 선정 배경

자율주행 기술이 급속히 발전함에 따라, **카메라 기반 시각 인식 기술**의 중요성이 증가하고 있습니다. 본 프로젝트는 **영상 처리 기술을 이용한 차선 인식 및 주행 제어 기능**을 구현하는 것을 목표로 시작되었습니다.


### 🔹 프로젝트 목표

- **TurtleBot3**와 **ROS2**를 기반으로 실제 도로 환경을 시뮬레이션
- 차선 인식, 속도 제어, 장애물 회피, 조명 변화에 대한 적응 등 **자율주행의 핵심 기능**을 구현

### 🔹 사용 장비 및 기술 스택

- **하드웨어**:  
  - TurtleBot3 Waffle Pi  
  - DRGO 웹캠  
  - 다이나믹셀 매니퓰레이터  
  - Nvidia Jetson Nano  
  - ArUco 마커  

- **소프트웨어/라이브러리**:  
  - ROS2 Humble  
  - OpenCV  
  - Python  


### 🔹 기대 효과

- **물류**, **안내**, **감시 로봇** 등에 적용 가능한 자율주행 주행 기술 확보  
- **영상 처리 및 자율주행 알고리즘**에 대한 실질적인 구현 및 이해도 향상  
- ROS2 기반 실시간 로봇 제어 및 시각 센서 융합 기술 습득
- 
---

## 🎥 데모 영상

[![시연 영상 보기](https://img.youtube.com/vi/Na-itqUUj6Q/0.jpg)](https://youtube.com/shorts/Na-itqUUj6Q?feature=share)


---

## 📅 개발 일정

| 날짜 | 작업 내용 |
|------|-----------|
| 2025.06.16 | 주제 선정 및 기획안 작성 |
| 2025.06.17 | 로봇팔 초기 포즈 설정, 카메라 캘리브레이션, 차선 인식 1차 |
| 2025.06.18 | 차선 인식 개선, ArUco 마커 인식 구현 |
| 2025.06.19 | Pick & Place 시나리오 구성, 발표자료 제작 |

> **총 개발 기간**: 4일

---

## ⚙️ 주요 기능

- `detect_lane.py`: HSV + 밝기 기반 차선 마스킹 및 라인트레이싱
- `control_lane.py`: PD 제어 기반 Steering 및 속도 조절
- `aruco_detector.py`: ArUco 마커 기반 좌표 추출 및 TF 변환
- `pick_n_place.py`: 전달 받은 좌표까지 이동 및 로봇팔 Pick & Place 시나리오 구현

---

## 💡 도전 과제 & 해결

| 문제 | 해결 방법 |
|------|-----------|
| 카메라 포지셔닝 오류 | 매니퓰레이터 포즈 변경 + Calibration.yaml 보정 + `image_raw` 토픽 사용 |
| poltfit의 이상치 발생 | poltfit 결과에 곡률 기반 필터링 적용|
| 바닥 반사로 인한 차선 오인식 | 밝기 보정(`equalizeHist`) + HSV 자동 범위 설정 |
| 차선 인식 불안정 | Morphology 연산 + Sliding Window 보완 |
| ArUco 위치 인식 정확도 | 카메라 캘리브레이션 및 거리 기반 추정 적용 |
<img width="1000" height="700" alt="image" src="https://github.com/user-attachments/assets/7b22b65f-b0fc-4972-9cb2-d3ec7571973f" />


---

## 👥 팀원 역할

| 역할 | 이름 | 담당 |
|------|------|------|
| 팀장 | 정민섭 | 전체 목표 설정, 결과 진행 회의, 차선 인식 및 PD 제어 |
| 팀원 | 문준웅 | 전체 주행 로직 및 코드 통합 |
| 팀원 | 이경민 | 하드웨어 세팅, ArUco 인식, 발표 자료 |
| 팀원 | 최정호 | 카메라 캘리브레이션, 로봇팔 제어 |

---

## 🎯 프로젝트 성과

- 밝기 보정 + HSV 마스킹 + Morphology 연산을 통한 차선 검출 정확도 향상
- PD 제어 기반 자율주행 구현
- ArUco 마커 기반 위치 인식 및 Pick & Place 동작 성공
- ROS2 기반 다중 노드 통신 구조 설계 및 실행
- 결과적으로 basic 코드 대비 **완주 시간이 약 34.8% 단축**
  
---

## 📸 주요 장면

### 📍 카메라 캘리브레이션
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/83d650a5-d619-4b9d-8f90-146457df4916" />

### 📍 차선 인식 개선 과정
- 밝기 보정 (equalizeHist)
- Morphology 연산
- HSV 마스킹 자동화

| 빛 반사 보정 | Morphology | HSV 마스킹 | 최종 결과 |
|--------------|-------------|--------------|--------------|
| ![](https://github.com/user-attachments/assets/61782e78-f2cd-46a4-8063-a3bf40bf2eb0) | ![](https://github.com/user-attachments/assets/ec91b4d6-87ea-488b-bc7b-905d2645cc85) | ![](https://github.com/user-attachments/assets/72a95b0c-c514-49d5-85a0-09f791f3fe6b) | ![](https://github.com/user-attachments/assets/0d01514d-5cbb-412c-9e0c-894d3a3c083e) |

### 📍 ArUco 마커 인식
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/70e2ed7d-4cc9-4a78-bd89-35cf77824f41" />
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/1ea9c2e4-35a1-47fe-b5b1-8fa3ebda65c9" />


### 📍 Pick & Place 동작
![Image](https://github.com/user-attachments/assets/8521991f-8dd9-471e-9cdf-ada4cd7dbc5d)
![Image](https://github.com/user-attachments/assets/a7fb8dc0-b51e-4790-bdc5-2736c9a87b5f)

### 📍 Speed control
- **PD 제어**: 중심 오차를 기반으로 회전 각속도(`angular.z`) 계산
- **속도 감소**: 중심 오차가 클수록 속도 감소
- **회전 제한**: 회전값은 ±1.0 rad/s로 제한
- **조향 강도 기반 속도 보정**: 회전이 클수록 속도 감속
  
📈 기대 효과
- 부드러운 조향: P + D 항을 통해 급격한 회전 방지
- 안정적인 속도 제어: 코너 구간에서 자동 감속
- 중앙선 기준 주행: 카메라 기준 320 픽셀 중심 유지

| Basic Code | Optimized Code |
|------------|----------------|
| <img src="https://github.com/user-attachments/assets/810cc764-d638-452f-9bf7-fe2e830b4144" width="400"/> | <img src="https://github.com/user-attachments/assets/9ab32888-f1c4-4095-b9c4-a668f06d0e66" width="400"/> |


---

## ✍ 개선 사항 및 회고

- PD 제어 민감도 조정 및 주행 안정성 향상 필요
- HSV 마스킹 실시간 처리 성능 개선 과제 도출
- ArUco 인식 후처리 보정 로직 개발 예정
- Manipulation 트리거 구조를 서비스 or GUI 기반으로 확장 예정

---

## 🧠 배운 점

- ROS2의 퍼블리셔/서브스크라이버 구조 이해
- HSV 마스킹, equalizeHist, Morphology 등 영상 처리 실습
- ArUco 마커 인식 및 TF 프레임 변환 로직 적용
- 로봇팔 제어와 인식 알고리즘의 실시간 통합 경험

---

## 🚀 향후 확장 아이디어

- Manipulator 동작을 ROS2 서비스로 모듈화
- ArUco 마커 위치 신뢰도 향상을 위한 필터링 보완
- 거리 기반 좌표 정밀도 보정 알고리즘 추가
- GUI 및 CLI 제어 인터페이스 개발
- LiDAR 기반 장애물 회피 기능 확장

---

> 이 프로젝트는 ROS2 기반 기술을 활용하여 자율주행, 인식, 로봇팔 제어를 통합한 **실시간 서비스 로봇 시스템 구현**을 목표로 하였습니다.
