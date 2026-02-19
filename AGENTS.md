# AGENTS.md - 에이전트 코딩 가이드라인

## 빌드 / 린트 / 테스트 명령어

### Python 명령어
- **모든 테스트 실행**: `python -m pytest` 또는 `pytest`
- **단일 테스트 실행**: `python -m pytest path/to/test_file.py::test_function_name`
- **커버리지 포함 테스트 실행**: `pytest --cov=. --cov-report=html`
- **코드 린트**: `flake8 .` 또는 `pylint .`
- **코드 포맷**: `black .` 및 `isort .`
- **타입 검사**: `mypy .`
- **전체 검사**: `python -m py_compile` (문법 검사만)

### JavaScript/TypeScript 명령어
- **의존성 설치**: `npm install`
- **개발 서버 실행**: `npm run dev`
- **빌드**: `npm run build`
- **테스트 실행**: `npm test` 또는 `npm run test:watch`
- **단일 테스트 실행**: `npm test -- --testPathPattern=test_name`
- **린트**: `npm run lint`
- **포맷**: `npm run format`

### Docker 명령어
- **빌드**: `docker build -t image_name .`
- **실행**: `docker run -p 8080:8080 image_name`
- **Docker Compose**: `docker-compose up`

### 일반
- **가상 환경**: `python -m venv venv && source venv/bin/activate` (Unix) 또는 `python -m venv venv && venv\Scripts\activate` (Windows)

---

## 코딩 스타일 가이드라인

### 일반 원칙
- 깔끔하고 읽기 쉽고 유지보수 가능한 코드 작성
- 함수는 작고 단일 책임 원칙을 유지
- 의미 있는 변수명과 함수명 사용
- 복잡한 로직만 주석 처리 (명확한 코드는 불필요)

### 임포트
- 표준 라이브러리 임포트를 먼저
- 서드파티 임포트其次
- 로컬 애플리케이션 임포트를 세 번째
- 가능한 절대 경로 임포트 사용
- 각 그룹 내에서 알파벳 순으로 정렬

### 포맷팅
- 들여쓰기는 4칸 공백 사용 (탭不使用)
- 최대 줄 길이: 100-120자
- 여러 줄 구조에는 후행 쉼표 추가
- 논리적 섹션 구분에는 빈 줄 사용

### 타입
- 함수 인자와 반환값에 타입 힌트 사용
- `Any`보다 명시적 타입 선호
- 컬렉션에는 제네릭 (`List[T]`, `Dict[K, V]`) 사용

###命名 규칙
- **변수/함수**: snake_case (예: `get_user_name`)
- **클래스**: PascalCase (예: `UserService`)
- **상수**: UPPER_SNAKE_CASE (예: `MAX_RETRIES`)
- **비공개 메서드**: 밑줄 접두사 (예: `_internal_method`)

### 오류 처리
-裸 `except:` 대신 구체적인 예외 사용
- 재발생 전 오류 로깅
- 예외를 조용히 무시하지 않음
- 리소스 관리에는 컨텍스트 매니저 (`with`) 사용

### 테스트
- 버그 수정 전 테스트 작성 (가능하면 TDD)
- 설명적인 테스트 이름 사용: `test_should_return_user_when_valid_id`
- AAA 패턴 준수: Arrange, Act, Assert
- 외부 의존성 모킹
- 높은 코드 커버리지 목표

---

## 프로젝트 구조

```
/src              # 소스 코드
/tests            # 테스트 파일
/docs             # 문서
/scripts          # 유틸리티 스크립트
/config           # 설정 파일
```

---

## Git 컨벤션

- 커밋 컨벤션 사용: `feat:`, `fix:`, `docs:`, `refactor:`, `test:`
- 커밋은 작고 집중적으로 유지
- 설명적인 커밋 메시지 작성
- 시크릿이나 자격 증명 커밋 금지
