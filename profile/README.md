<h1 align="center">
  
  ![image](https://github.com/user-attachments/assets/0888af51-a82c-439e-a5c1-4f85326e6a35)
  
</h1>

# SABU (Sell And BUy)

**SABU**는 ETF 및 주식 기반 포트폴리오 전략을 추천하고, 시뮬레이션 및 백테스트를 통해 투자 전략을 분석할 수 있는 **웹 기반 투자 분석 플랫폼**입니다.

---

## 📦 레포지토리 구성

| 레포지토리 | 설명 |
|------------|------|
| [`SABU-Frontend`](https://github.com/DKUOpenSource-SABU/Frontend) | 사용자 UI 대시보드 (React 기반) |
| [`SABU-Backend`](https://github.com/DKUOpenSource-SABU/Backend)  | 백엔드 서버 및 투자 시뮬레이션 API (FastAPI) |
| [`SABU-Docs`](https://github.com/DKUOpenSource-SABU/Docs) | 각종 문서화 레포지토리 |

---

## ✅ 실행 전 사전 준비 사항

- 백엔드 실행 전, `./data/stock` 디렉토리에 **주식 정보 CSV 파일**을 넣어야 합니다.
- 데이터는 **Tiingo API**에서 받은 형식을 따라야 하며, 아래는 예시입니다:

```
# {ticker}.csv
date,close,high,low,open,volume,adjClose,adjHigh,adjLow,adjOpen,adjVolume,divCash,splitFactor
2020-09-09,25.0699,25.119,25.0699,25.1,17327,20.8985,20.9395,20.8985,20.9236,17327,0.0,1.0
...
```

- 해당 주식 데이터는 `./collect/tiingo_api` 경로의 스크립트를 이용해 자동 수집할 수 있습니다.  
  → 위치: `SABU-Backend/collect/tiingo_api.py`

- `.env` 또는 환경변수에 [**Tiingo API 토큰**](https://www.tiingo.com/)을 지정해야 합니다:
```
TIINGO_TOKEN=your_actual_token_here
```


## 💻 프론트엔드 실행 방법 (React)

```bash
# 1. 레포지토리 클론
git clone https://github.com/DKUOpenSource-SABU/Frontend.git
cd SABU-Frontend

# 2. 의존성 설치
npm install

# 3. 로컬 실행
npm run dev
# 또는
npm start
```

## 🐍 백엔드 실행 방법 (FastAPI)
```bash
# 1. 레포지토리 클론
git clone https://github.com/DKUOpenSource-SABU/Backend.git
cd SABU-Backend

# 2. 가상환경 생성 및 활성화
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate

# 3. 의존성 설치
pip install -r requirements.txt

# 4. 환경변수 설정 (.env 또는 export)
export TIINGO_TOKEN=your_actual_token_here

# 5. API 서버 실행
uvicorn main:app --host 0.0.0.0 --port 8000

```

> Swagger UI는 http://localhost:8000/docs 에서 확인할 수 있습니다.
