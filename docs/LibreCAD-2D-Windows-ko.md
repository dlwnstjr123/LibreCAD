# LibreCAD 2D — Windows 빌드 시작하기

이 문서는 개인용 LibreCAD 포크에서 **Windows x64 설치 파일**을 만드는 방법을 설명합니다.

## 1. 빌드 및 다운로드

1. GitHub 저장소 **Actions** 탭을 엽니다.
2. **LibreCAD 2D - Windows installer**를 선택합니다.
3. `feature/2d-windows-baseline` 브랜치의 실행이 **Success**로 끝났는지 확인합니다.
4. 해당 실행 하단의 **Artifacts → librecad-2d-win-x64**를 눌러 ZIP을 다운로드합니다.
5. ZIP을 압축 해제한 뒤 포함된 `LibreCAD-...-win-x64.exe` **설치 파일**을 실행합니다.

워크플로가 처음 등장할 때 GitHub에서 Actions 허용을 요구하면 사용자 계정에서 직접 활성화해야 합니다. 이 문서를 작성한 시점에는 실행 결과가 확인되지 않았습니다. 빌드가 실패하면 Actions의 실패 단계 로그를 확인해야 합니다.

## 2. 구성

- LibreCAD 공식 `.github/workflows/build-all.yml`의 `BuildWindows64` 과정을 바탕으로 합니다.
- Qt 6.9, MSVC 2022, Boost, CMake로 컴파일하고 기존 NSIS 스크립트로 Windows x64 설치 파일을 만듭니다.
- **Windows 빌드만** 실행하며 다른 운영체제 빌드 작업을 실행하지 않습니다.
- `master` 브랜치의 기존 설정과 프로그램 소스코드는 건드리지 않습니다.
- 결과물은 성공한 Actions 실행에서 14일간 보관됩니다.
- 배포 전 실제 도면 열기/저장/출력 테스트가 필요합니다. 소스코드 수정 기능이 추가된 버전이 아니라 **기본 빌드 검증용**입니다.
- 실행 파일은 개인 개발용으로 디지털 서명되지 않았을 수 있습니다.

## 3. 2D 기능 개발 우선순위

1. **작동 기준선**: 선/원, 스냅, 레이어, DXF 도면 열기·저장, 기본 치수
2. **학교 도면 작업**: 중심선(선 종류·레이어)과 중심 표시 및 치수 사용성 개선
3. **명령어**: AutoCAD에 익숙한 축약 명령어와 TRIM / OFFSET / MIRROR 동작 개선
4. **호환성**: DXF 및 DWG 도면 왕복 검증(지원 범위에 주의), PDF 출력 점검

LibreCAD는 GPL 라이선스로 배포됩니다. 재배포할 때 원 저작권 및 라이선스 조건을 준수해야 합니다.
