# KIOSK_PAGE
키오스크 홈페이지 - 이미지 슬라이드쇼 시스템

GitHub Pages를 통해 배포되는 키오스크용 이미지 포스터 슬라이드쇼입니다.

## 📁 이미지 업로드 규칙

### img 폴더에 이미지 업로드 방법

1. **파일명 규칙**
   - 파일명은 **2자리 숫자**로 시작해야 합니다
   - 형식: `01.png`, `02.jpg`, `03.jpeg` 등
   - 예시: `01.png`, `02.jpg`, `03.JPG`, `10.png`

2. **지원하는 확장자**
   - `.png` / `.PNG`
   - `.jpg` / `.JPG`
   - `.jpeg` / `.JPEG`

3. **업로드 순서**
   - 이미지는 파일명의 숫자 순서대로 표시됩니다
   - `01.png` → `02.jpg` → `03.png` 순서로 슬라이드됩니다

4. **주의사항**
   - 최대 20개까지 이미지를 검사합니다 (01~20)
   - 같은 번호에 여러 확장자 파일이 있으면 먼저 찾은 파일을 사용합니다
   - 파일명이 `01`, `02` 형식이 아니면 인식되지 않습니다

### 예시
```
img/
  ├── 01.png
  ├── 02.jpg
  ├── 03.png
  └── 04.JPG
```

## ⚙️ setup.json 설정 방법

`setup.json` 파일을 수정하여 Swiper 슬라이드쇼의 동작을 커스터마이징할 수 있습니다.

### 기본 설정 파일 구조

```json
{
  "effect": "fade",
  "speed": 1500,
  "autoplay": {
    "delay": 5000,
    "disableOnInteraction": false
  },
  "loop": true,
  "pagination": {
    "clickable": true
  },
  "fadeEffect": {
    "crossFade": true
  }
}
```

### 설정 옵션 설명

#### `effect` (전환 효과)
- **값**: `"slide"` 또는 `"fade"`
- **설명**: 슬라이드 전환 효과 선택
  - `"slide"`: 좌우 슬라이드 효과
  - `"fade"`: 페이드 인/아웃 효과
- **기본값**: `"fade"`

#### `speed` (전환 속도)
- **값**: 숫자 (밀리초)
- **설명**: 슬라이드 전환 애니메이션 속도
- **예시**: `1000` = 1초, `1500` = 1.5초, `2000` = 2초
- **기본값**: `1500`

#### `autoplay.delay` (자동재생 간격)
- **값**: 숫자 (밀리초)
- **설명**: 다음 슬라이드로 자동 전환되는 시간 간격
- **예시**: `3000` = 3초, `5000` = 5초, `10000` = 10초
- **기본값**: `5000`

#### `autoplay.disableOnInteraction` (터치 후 자동재생 유지)
- **값**: `true` 또는 `false`
- **설명**: 사용자가 터치/클릭 후에도 자동재생을 계속할지 여부
  - `false`: 터치 후에도 자동재생 계속 (키오스크 권장)
  - `true`: 터치 후 자동재생 중지
- **기본값**: `false`

#### `loop` (무한 루프)
- **값**: `true` 또는 `false`
- **설명**: 마지막 슬라이드 후 첫 슬라이드로 돌아가는지 여부
- **기본값**: `true`

#### `pagination.clickable` (페이지네이션 클릭 가능)
- **값**: `true` 또는 `false`
- **설명**: 하단 점(페이지네이션)을 클릭하여 슬라이드 이동 가능 여부
- **기본값**: `true`

#### `fadeEffect.crossFade` (페이드 교차 효과)
- **값**: `true` 또는 `false`
- **설명**: `effect`가 `"fade"`일 때만 적용되는 옵션
  - `true`: 부드러운 교차 페이드 효과
  - `false`: 일반 페이드 효과
- **기본값**: `true`

### 설정 예시

#### 빠른 슬라이드 전환 (3초 간격, slide 효과)
```json
{
  "effect": "slide",
  "speed": 800,
  "autoplay": {
    "delay": 3000,
    "disableOnInteraction": false
  },
  "loop": true,
  "pagination": {
    "clickable": true
  }
}
```

#### 느린 페이드 전환 (10초 간격)
```json
{
  "effect": "fade",
  "speed": 2000,
  "autoplay": {
    "delay": 10000,
    "disableOnInteraction": false
  },
  "loop": true,
  "pagination": {
    "clickable": true
  },
  "fadeEffect": {
    "crossFade": true
  }
}
```

## 🚀 GitHub Pages 배포 방법

1. **저장소 생성 및 파일 업로드**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/사용자명/저장소명.git
   git push -u origin main
   ```

2. **GitHub Pages 활성화**
   - GitHub 저장소 페이지로 이동
   - Settings → Pages 메뉴 선택
   - Source에서 `main` 브랜치 선택
   - Save 클릭

3. **배포 확인**
   - 배포 완료 후 `https://사용자명.github.io/저장소명/` 주소로 접속
   - 이미지와 설정이 정상적으로 로드되는지 확인

## 📝 주의사항

- `setup.json` 파일이 없거나 오류가 있으면 기본 설정값이 사용됩니다
- 이미지 파일은 반드시 `img` 폴더 안에 있어야 합니다
- 파일명은 2자리 숫자로 시작해야 하며, 앞에 0을 붙여야 합니다 (예: `01`, `02`, `10`)
- GitHub Pages는 정적 파일만 호스팅하므로 서버 측 처리가 필요 없습니다
