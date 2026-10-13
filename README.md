# korea-city-builder

한국의 시·자치구를 도시 모형으로 띄우고, 공공 건물만 남긴 빈 땅에 아파트·주택·상가·학교·공원·여가·생활·직장·배송 시설을 직접 지어 보는 웹 페이지예요.

- 페이지: https://yurmung.github.io/korea-city-builder/
- 지금 열 수 있는 지역: 경상남도 내 시, 자치구 (다른 시·자치구는 순차 추가 예정)

## 폴더 구조

```
docs/                 웹 페이지 (GitHub Pages로 공개되는 폴더)
  index.html
data/                 지역 데이터 (페이지가 raw.githubusercontent.com에서 불러옴)
  regions.json        시·자치구 목록과 준비 여부(ready)
  <시군구코드>/        예: 48170 = 진주시
    meta.json         지형 높이, 행정동 경계, 공공 건물, 산 정상, 건물 크기 카탈로그
    class.png         12.5m 격자 토지 분류 (빈 땅, 농지, 숲, 물, 도로 등)
    dist.png          도로 가장자리까지 거리(m, 0~255) — 설치 가능 구역 계산용
    roads.bin         도로·철도 선 데이터
    buildings.bin     실제 도시 보기용 건물 외곽선과 높이
```

## 데이터 출처

- 행정동 경계: [vuski/admdongkor](https://github.com/vuski/admdongkor) ver20260701 (통계청·행정안전부 행정동 경계 기반)
- 도로·녹지·하천·공공기관·산 정상: © [OpenStreetMap](https://www.openstreetmap.org/copyright) 기여자 (ODbL), Overpass API
- 지형: AWS Terrain Tiles (Mapzen terrarium, SRTM 등)
- 실제 건물: 국토교통부 GIS건물통합정보 (공공데이터포털, 2026-10-09 전체분)
- 3D 렌더링: [three.js](https://threejs.org/) r160

건물 크기는 같은 종류 실제 건물들의 평균(상하위 10% 제외, 반올림)으로 정했어요. 자세한 출처는 페이지의 "데이터 출처"에서 볼 수 있어요.
