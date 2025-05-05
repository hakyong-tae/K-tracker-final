# K-Tracker Final

🏃‍♂️ **K-Tracker**는 마라톤 대회 기록을 실시간으로 조회하고 응원하는 프로젝트입니다.  
`SmartChip`과 `MyResult` 두 데이터 소스 기반의 프록시 백엔드와 프론트엔드로 구성됩니다.

## 📁 프로젝트 구조

k-tracker-final/
├── frontend/ # 사용자 인터페이스 (HTML 기반)
│ ├── index.html
│ ├── group_viewer.html
│ ├── group_register.html
│ └── event.html
├── myresult-proxy/ # MyResult 대회 기록 크롤링 및 API 프록시 (Node.js 기반)
│ ├── index.js
│ ├── package.json
│ ├── fly.toml
│ └── ...
├── smartchip-proxy/ # SmartChip 대회 기록 크롤링 및 API 프록시 (Python 기반)
│ ├── smartchip_proxy.py
│ ├── runner_parser.py
│ ├── Dockerfile
│ ├── fly.toml
│ └── ...
└── .gitignore # 불필요한 파일 무시 설정 (node_modules, pycache, 등)

## 🚀 구성 요소

### 프론트엔드 (frontend/)
- 유저가 대회를 선택하고 선수 그룹을 만들어 실시간 기록을 볼 수 있는 HTML 페이지들
- 그룹 뷰어: `/group_viewer.html`
- 그룹 등록기: `/group_register.html`
- 대회 목록 보기: `/event.html`

### 스마트칩 API 프록시 (smartchip-proxy/)
- SmartChip 기록 페이지를 파싱하여 JSON API로 변환
- Docker 기반으로 Fly.io에 배포됨

### 마이리절트 API 프록시 (myresult-proxy/)
- MyResult 기록 페이지를 파싱하여 JSON API로 제공
- Node.js 기반으로 Render에 배포됨

## 📡 배포 환경

- SmartChip Proxy → **Fly.io**
- MyResult Proxy → **Render**
- Frontend → **GitHub Pages 또는 정적 웹 호스팅**

## 🛠️ 개발 및 실행

### 1. 프론트엔드
로컬 테스트:
cd frontend
open index.html


### 2. Smartchip Proxy
도커 빌드 및 실행:
cd smartchip-proxy
docker build -t smartchip-proxy .
docker run -it --rm -p 8080:8080 smartchip-proxy


### 3. MyResult Proxy
Node.js 실행:
cd myresult-proxy
npm install
npm start


## 📦 .gitignore

이미 다음과 같이 설정되어 있어 불필요한 파일은 깃에 올라가지 않습니다.

node_modules/
pycache/
*.pyc

## 📌 TODO

- SmartChip & MyResult 공통 파싱 로직 고도화 (optional)
- 프론트엔드 UI 개선
- 응원 메시지 기능 추가 (optional)

---

# 📢 Special Thanks

- 데이터 제공: SmartChip, MyResult
- 개발 및 운영: @hakyong (Planetarium / 개인 프로젝트)
