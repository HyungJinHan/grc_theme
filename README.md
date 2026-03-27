# 🎨 GRC One Dark Pro Darker Theme for Python/FastAPI Logs

이 저장소는 `grc` (Generic Colouriser)를 사용하여 터미널 로그를 **VS Code의 One Dark Pro Darker** 테마 스타일로 시각화하는 설정 파일을 담고 있습니다. 특히 Python, FastAPI, SQLAlchemy 로그 분석에 최적화되어 있습니다.

## ✨ 주요 특징
* **One Dark Pro Darker** 색상 팔레트 적용 (`#181a1f` 배경 권장)
* **HTTP 메소드별 색상 구분**: `GET`(Blue), `POST`(Green), `PUT`(Orange), `DELETE`(Red)
* **SQL 쿼리 강조**: `UPDATE`, `SELECT` 등 주요 키워드 및 파라미터(`$1`) 강조
* **에러 핸들링**: `ERROR`, `500` 등의 치명적 요소를 강렬한 레드 배경으로 표시

---

## 🚀 설치 및 설정 방법 (macOS 기준)

### 1. GRC 설치
Homebrew를 통해 `grc`를 설치합니다.
```bash
brew install grc
```

### 2. 색상 규칙 파일 생성 (`.onedark_pro_darker`)
`grc`의 규칙 파일들이 모여 있는 경로에 새로운 설정 파일을 생성합니다.
```bash
sudo nano /opt/homebrew/share/grc/conf.onedark_pro_darker
```
생성된 파일에 이 저장소의 `conf.onedark_pro_darker` 내용을 모두 복사하여 붙여넣고 저장하세요.

### 3. GRC 메인 설정 연결 (`grc.conf`)
특정 로그 파일(`.log`)을 읽을 때 방금 만든 규칙을 사용하도록 연결합니다.
```bash
sudo nano /opt/homebrew/etc/grc.conf
```
파일의 맨 아래에 다음 **두 줄**을 추가합니다. (주의: 색상 규칙을 여기에 직접 적으면 에러가 발생합니다.)
```ini
# Python & FastAPI Log Mapping
^.*\.log$
conf.onedark_pro_darker
```

---

## 🎨 권장 터미널 설정
테마의 완성도를 위해 터미널(iTerm2, Terminal.app 등)의 배경색을 아래 코드로 설정하는 것을 권장합니다.

* **Background Color**: `#181a1f` (One Dark Pro Darker 공식 배경색)
* **Font**: `Cascadia Code` 또는 `Fira Code` (LIGATURE 지원 폰트 권장)

---

## 🔍 사용 방법
터미널에서 로그를 확인할 때 `grc` 커맨드를 앞에 붙여서 실행하세요.

```bash
# 실시간 로그 확인 시
grc tail -f server.log

# 로그 파일 전체 출력 시
grc cat server.log
```

---

## 🛠️ 문제 해결 (Troubleshooting)
만약 주황색(Orange)이 제대로 표시되지 않는다면, 사용 중인 셸 설정 파일(`~/.zshrc` 등)에 아래 내용을 추가하여 256색 모드를 활성화하세요.
```bash
export TERM="xterm-256color"
```
