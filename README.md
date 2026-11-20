# LET'S SYNC! 메인 인터랙션 (추출본)

출처: https://www.digital-media.kr/degreeshow/2026/ (계원예술대학교 디지털미디어디자인과 2026 졸업전시)
사이트의 빌드된 번들(index-DB1SSUYu.js)에서 메인 히어로 인터랙션 부분만 떼어낸 것입니다.

## 실행
index.html 더블클릭 (서버 없이 file:// 로도 동작). 데스크톱(가로 768px 이상, 마우스) 환경 기준.

## 파일
- index.html          히어로 마크업 (힌트 문구, 타이틀, 하단 전시 정보)
- style.css           히어로/커서 스타일 (원본 CSS에서 해당 부분만 발췌)
- type-interaction.js 엔진. 원본 minified 코드 그대로 + mountTypeInteraction() 래퍼
    - Vw  : SVG 글자를 캔버스로 샘플링해 픽셀 포인트/외곽선 생성 (충돌 판정용)
    - Hw  : 글자끼리 픽셀 단위 충돌 검사
    - Gw  : 배경 점 네트워크
    - Kw  : 메인 엔진 (글자 배치·물리, 점 hover/클릭, 두 점 연결 시 글자 SYNC 모션, 커서)
    - 주요 상수 (Kw 안): 강조색 d='#FD00A0', 선색 u='#EBEBEB', 커서 색 배열, 글자 크기 k=[358,...], 기울기 A=[...]
- type-assets.js      글자 SVG 89개를 data URI로 담은 맵 (window.TYPE_ASSETS)
- assets/type/        같은 SVG 원본 파일들 (수정용). 파일명 규칙: X_default.svg = 기본 글자,
                      AB_A.svg / AB_B.svg = A와 B가 연결됐을 때 각 글자가 바뀌는 모양
- assets/heroTitle.svg 가운데 LET'S SYNC! 타이틀

## SVG를 바꾸고 싶으면
assets/type/ 의 파일을 수정한 뒤, type-assets.js 대신 경로 맵을 쓰면 됩니다. 단 이 경우
캔버스 getImageData 때문에 반드시 로컬 서버(npx serve 등)로 열어야 합니다:
  window.TYPE_ASSETS = { "L_default.svg": "assets/type/L_default.svg", "L/LE_L.svg": "assets/type/L/LE_L.svg", ... }

※ 원작자(전시 웹 제작팀)의 코드·디자인이니 개인 학습/참고용으로만 쓰고, 외부 공개 시에는 출처를 밝히거나 허락을 받으세요.
