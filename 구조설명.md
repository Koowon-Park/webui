# Koowon-Park/webui 저장소 구조 설명

## 1. 최상위 개요

- **WebUI**는 백엔드(여러 언어 지원)와 프론트엔드(웹 기술)를 브라우저 또는 WebView를 통해 연결하는 경량 GUI 라이브러리입니다.
- 대표적 특징: 단일 헤더, 경량, 빠른 통신, 멀티플랫폼, 다양한 언어 래퍼 제공.

## 2. 주요 디렉터리 및 파일

- **README.md**  
  저장소의 전반적인 설명, 빌드/사용법, 특징, 아키텍처 다이어그램, 예제 및 문서 링크 제공.

- **build.zig**  
  Zig 빌드 시스템 스크립트.  
  라이브러리와 예제 빌드, 의존성 설정, 플랫폼별 빌드 옵션 정의.

- **/src/**  
  핵심 라이브러리 소스 코드.
    - `/src/webui.c`, `/src/webui.h`: 주요 WebUI 구현.
    - `/src/civetweb/`: 내장 웹서버 civetweb 관련 코드.
    - 기타 플랫폼 특화 소스(예: macOS용 WKWebView 등).

- **/bridge/**  
  Web 브라우저와 백엔드 앱을 WebSocket으로 연결하는 브리지 코드(TypeScript).
    - `webui.ts`: 브리지 메인 소스.
    - `build.bat`, `build.sh`: 타입스크립트 → 자바스크립트 번들 및 변환 자동화 스크립트.
    - `README.md`: 브리지 빌드 방법 안내.

- **/examples/**  
  다양한 언어 및 기능별 예제 프로젝트.
    - `/C/`, `/C++/`, `/react/` 등 언어별/프레임워크별 예제 폴더.
    - 각 폴더 내 `README.md`, `Makefile`, `main.c/cc` 등 빌드 및 실행 예시 포함.

- **/include/**  
  공개용 헤더 파일(`webui.h`) 등.

## 3. 전체 구조 예시

```
webui/
├── README.md
├── build.zig
├── include/
│   └── webui.h
├── src/
│   ├── webui.c
│   ├── webui.h
│   └── civetweb/
├── bridge/
│   ├── webui.ts
│   ├── build.bat
│   ├── build.sh
│   └── README.md
└── examples/
    ├── C/
    ├── C++/
    └── react/
```

## 4. 동작 구조(간략)

- **Web 브라우저(또는 WebView)**가 UI를 렌더링.
- **WebUI 라이브러리**가 앱 백엔드(예: C/C++)와 브라우저 간 통신 담당.
- **bridge**가 WebSocket 통해 UI와 백엔드 연결.
- 예제 및 래퍼를 통해 Python, Go, Zig 등 다양한 언어 환경 지원.

---

더 세부적인 폴더/파일 구조나 특정 부분 설명이 필요하면 말씀해 주세요!
