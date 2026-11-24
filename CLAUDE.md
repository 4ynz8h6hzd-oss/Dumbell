# Dumbell

- 앱: 루트 `index.html` 한 파일(빌드 없음). `main` 브랜치 / (root)로 GitHub Pages 배포 → https://4ynz8h6hzd-oss.github.io/Dumbell/
- 수정 요청 시: `index.html` 수정 → `main`에 푸시하면 바로 배포.
- 운동 기록: 앱이 GitHub 토큰으로 `data` 브랜치의 `data.json`에 자동 커밋(세트 1개 = 1줄).
  기록 분석 요청 시 `git fetch origin data && git show FETCH_HEAD:data.json` 로 읽기.
  필드: ex(운동 키), date, ts(완료 시각 epoch ms, 사용자 시간대는 timeZone), w(kg), r(회), T(첫 세트 목표 추정10RM), P(그 세트의 예상 추정10RM — 오늘 피로 판단용), u(수정 시각). `deleted`는 삭제된 세트 id.
  추정10RM = w×(30+r)÷40. `data` 브랜치는 Pages 빌드를 유발하지 않도록 main과 분리.
  세트 구성: 1세트 = 탑세트(진도 판단), 2·3세트 = 백오프(직전 세트 실제 결과 × 실제 휴식 시간 반영 피로 모델, 고립 운동은 무게 낮춰 MMC).
  그날 앞선 운동이 예상(P)보다 못하면 다음 운동 첫 세트 목표를 낮춤(같은 근육 100%, 그 외 50%, 최대 −6%).
