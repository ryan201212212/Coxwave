
**State-Machine 기반 동적 트레이스 검증을 통한 멀티 에이전트 시스템 오류 탐지 및 신뢰성 평가 프레임워크**
 
본 저장소는 엔터프라이즈 멀티 에이전트 프로덕션 환경에서 정답셋(Ground Truth)이 부재한 상황에서도 런타임 추적 로그를 분석하여 환각(Hallucination), 도구 사용 무한 재시도 루프, Handoff 제어권 정체 현상을 실시간 정량화 및 선제 차단(Early Stopping)하는 하이브리드 검증 인터셉터의 공식 PoC 프로토타입 소스코드입니다.

---

## 1. Method Overview

본 프레임워크는 특정 개발 환경(LangGraph, CrewAI 등)의 종속성을 완벽히 탈피하여, 멀티 에이전트 시스템 내부에서 가공된 텔레메트리 스트림을 3단계 필터링 아키텍처를 통해 검증하는 '선 규칙 검증, 후 모델 심사' 체계를 채택합니다.


## 2. Quick Start

### Install packages
본 PoC 프로토타입 엔진은 타 사상 외부 패키지 라이브러리 설치 의존성을 완전히 차단하여, Python 3.8+ 환경에서 별도의 라이브러리 설치 없이 구동되도록 컴파일 설계되었습니다.


Step 1. 가상 런타임 스트레스 데이터셋 빌드
아래 스크립트를 실행하여 테스트용 모의 추적 로그 데이터셋인 telemetry_log.json 파일을 로컬 디렉토리에 생성합니다.

'''python generate_mock_trace.py'''

Step 2. FSM 런타임 검증 파이프라인 가동 및 차단 제어 리포팅
생성된 로그 시퀀스를 파싱하여 문맥적 지표를 동적 연산하고, 인터셉트 판정 결과 대시보드를 리포팅합니다. (실행 시 콘솔 출력과 동시에 evaluation_report.txt 파일로 보관됩니다.)

'''python verify_trace.py'''

Step 3.Console Execution Output (Expected Results)
verify_trace.py 엔진 가동 시 출력되는 실제 PoC 정량 검증 지표 보고서입니다.




