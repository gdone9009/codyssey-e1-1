📂 dev-workstation-template/
├── 1. 프로젝트 개요 (Overview)
│   ├── 1.1 미션 목적 및 워크스테이션 구축 배경
│   ├── 1.2 핵심 인프라 기술 및 수행 항목 (CLI, Docker, Git)
│   └── 1.3 환경 재현성(Reproducibility) 및 설계 원칙
├── 2. 실행 환경 및 도구 (Environment & Tools)
│   ├── 2.2 하드웨어 및 OS 호스트 명세 (macOS / Windows 런타임)
│   ├── 2.2 OrbStack 기반 비권한(Non-Sudo) Docker 실행 환경 정책
│   └── 2.3 핵심 솔루션 버전 명세 (Shell, Docker CLI, Git Engine)
├── 3. 수행 항목 체크리스트 (Task Checklist)
│   ├── 3.1 단계별 인프라 구축 마일스톤 (Step 1 ~ Step 5)
│   └── 3.2 작업 증적(Evidence) 및 명령어 출처 매핑 테이블
├── 4. 터미널 조작 및 권한 관리 아키텍처 (File System & RBAC)
│   ├── 4.1 CLI 기본 명령 수행 로그 (pwd, ls -la, mkdir, cp, mv, rm)
│   ├── 4.2 파일 콘텐츠 제어 및 탐색 로그 (cat, touch)
│   ├── 4.3 절대 경로(Absolute)와 상대 경로(Relative)의 기술적 차이 분석
│   ├── 4.4 리눅스 표준 파일 권한(r/w/x) 및 8진법(755, 644) 표기법 해석 규칙
│   └── 4.5 파일 및 디렉토리 권한 변경(chmod) 전/후 무결성 검증 로그
├── 5. Docker 인프라 초기화 및 기본 점검 (Docker Core Activation)
│   ├── 5.1 Docker Engine 버전 및 버전 정보 기록 (docker --version)
│   ├── 5.2 Docker 데몬(Daemon) 런타임 활성화 검증 (docker info)
│   └── 5.3 기본 이미지/컨테이너 운영 라이프사이클 로그 (images, ps -a, logs, stats)
├── 6. 격리 환경 실행 및 커스텀 이미지 제작 (Containerization & Custom Images)
│   ├── 6.1 hello-world 격리 컨테이너 실행 및 출력 검증
│   ├── 6.2 ubuntu 컨테이너 런타임 내부 진입 및 대화형 명령(ls, echo) 수행 로그
│   ├── 6.3 컨테이너 수명 주기 제어 분석 (종료 vs 유지: attach와 exec의 아키텍처적 차이)
│   ├── 6.4 커스텀 Dockerfile 아키텍처 설계
│   │   ├── 6.4.1 베이스 이미지(Base Image) 선택 사양 및 선택 근거
│   │   └── 6.4.2 레이어별 커스텀 포인트(환경변수, 파일 복사, 헬스체크) 설정 목적
│   └── 6.5 커스텀 빌드(docker build) 및 백그라운드 구동(docker run -d) 실행 로그
├── 7. 네트워크 및 스토리지 가상화 검증 (Network & Storage Hardening)
│   ├── 7.1 포트 매핑(Port Mapping) 매커니즘 및 호스트-컨테이너 포트 포워딩 필요성 분석
│   ├── 7.2 포트 포워딩 가동 및 다중 포트 브라우저(또는 curl) 네트워크 접속 성공 증적
│   ├── 7.3 바인드 마운트(Bind Mount) 가동 명령 및 호스트 파일 변경 동기화 전/후 비교 검증
│   ├── 7.4 Docker 볼륨(Volume) 독립 생성 및 가상 스토리지 라이프사이클 격리
│   └── 7.5 컨테이너 파괴(docker rm -f) 전/후 볼륨 내부 데이터 지속성(Persistence) 무결성 증명
├── 8. 개발자 프로필 및 Git/GitHub 보안 거버넌스 (Git Config & Security)
│   ├── 8.1 로컬 Git 글로벌 사용자 정보 및 기본 브랜치(main) 구성 로그 (git config --list)
│   ├── 8.2 VSCode 통합 환경 내 GitHub 원격 저장소 인증 및 연동 확인 증적
│   └── 8.3 시큐어 코딩 자산화 정책 (개인 토큰, 인증 코드, 비밀번호 마스킹 및 전처리 탈감작)
├── 9. [보너스 영역] Docker Compose 인프라 및 네트워크 고도화 (Advanced Selection)
│   ├── 9.1 단일 서비스의 문서화 구동을 위한 docker-compose.yml 명세 구조 설계
│   ├── 9.2 멀티 컨테이너(웹 서버 + 보조 서비스) 오케스트레이션 구동 및 격리 네트워크 인젝션
│   ├── 9.3 컨테이너 간 서비스 디스커버리(Service Discovery) 내부 통신 핑 테스트 검증
│   ├── 9.4 Compose 수명주기 제어 명령어 표준 운영 루틴 수립 (up, down, ps, logs)
│   ├── 9.5 환경 변수(.env) 주입을 통한 설정과 코드의 물리적 격리 아키텍처 구현
│   └── 9.6 HTTPS 프로토콜 대체용 GitHub SSH 키 페어(Key-pair) 등록 및 푸시(Push) 무결성 검증
├── 10. 트러블슈팅 리포트 (Troubleshooting)
│   ├── 10.1 [Issue #1] OrbStack 환경 하부 비권한 실행 시 컨테이너 소켓 권한 거부 에러
│   │   └── (상황 및 현상 → 원인 가설 설정 → 디버깅 및 검증 → 최종 해결 조치 및 대체 방안)
│   └── 10.2 [Issue #2] 호스트 가상 스토리지 볼륨 경로 오염으로 인한 데이터 영속성 유실 오류
│       └── (상황 및 현상 → 원인 가설 설정 → 디버깅 및 검증 → 최종 해결 조치 및 대체 방안)
└── 11. 결론 및 향후 과제 (Insights & Conclusion)
    ├── 11.1 인프라 환경 문서화를 통한 개발 효율성 제언
    └── 11.2 CI/CD 자동화 파이프라인 및 클라우드 배포 확장성 연구
