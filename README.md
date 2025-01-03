# 관심영역(Region of Interest, ROI) 설정 및 추출 기능 구현
- 이미지에서 관심 영역을 설정하고 이를 추출하는 기능

## 🚩 입력 영상 조건
- 해상도는 **640x480**으로 조정하여 사용한다.

## 🚩 관심영역(ROI) 정의 방식
### 타원(Ellipse) 방식
- **설정 방법**:
  1. 마우스 왼쪽 버튼을 눌러 시작 위치를 지정한다.
  2. 드래그하여 끝 위치를 설정한 뒤, 마우스 버튼을 떼면 타원 영역이 설정된다.
- **동작 조건**:
  - 드래그 중에 타원이 실시간으로 표시되어야 한다.

### 다각형(Polygon) 방식
- **설정 방법**:
  1. 시계 반대 방향으로 최소 3개의 점을 찍어 다각형을 정의한다.
  2. 첫 번째 점과의 거리가 20 이하일 경우 다각형을 닫고 마지막 점은 무시한다.
- **동작 조건**:
  - 점을 클릭하면 연속된 두 점을 잇는 선이 그려져야 한다.
  - 다각형 내각은 시계 반대 방향으로 180도 이하여야 한다.
  - 180도를 초과하는 각이 발생하면 해당 점은 반영하지 않는다.

## 🚩 이미지 추출 및 저장
- 관심영역 내부의 이미지를 원래 크기로 추출하여 저장한다.

## 🚩 프로그램 초기 상태 및 모드 전환
- **초기 상태**: NULL 모드로 시작
- **모드 전환**:
  - 타원(Ellipse) 모드: 키보드 숫자 `1`을 눌러 선택 (다시 누르면 해제)
  - 다각형(Polygon) 모드: 키보드 숫자 `2`를 눌러 선택 (다시 누르면 해제)
  - 타원 모드에서 `2`를 누르면 다각형 모드로 전환, 다각형 모드에서 `1`을 누르면 타원 모드로 전환
- **모드 표시**: 현재 모드를 이미지 왼쪽 상단에 표시 (`NULL`, `Ellipse`, `Polygon`)
