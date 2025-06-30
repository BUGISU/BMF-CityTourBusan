# 🚴‍♀️ 보자마자 피트니스 – 시티투어 부산  
**BOJAMAJA FITNESS: CITY TOUR BUSAN**

![Hero](https://github.com/JISUSAMA/UnityStudy/assets/38304918/af82dfde-007c-42e4-ba8c-84c29caeea51)

실내 자전거·러닝머신·밸런스보드 등에 장착 가능한 **BLE 센서(FIT-TAG)** 와 Unity3D를 결합해  
현실 속 운동 데이터를 바탕으로 부산 시티투어 코스를 따라 주행하는 **실감형 피트니스 게임**입니다.

---

## 📅 개발 기간
| 기간 | 역할 |
|------|------|
| **2023.01 ~ 2023.07** (7 개월) | 기획/아트 협업, **개발 100% 담당** |

---

## 🛠️ 기술 스택
| 영역 | 사용 기술 | 비고 |
|------|-----------|------|
| 게임 엔진 | **Unity3D (C#)** | URP 미사용 |
| 카메라 연출 | **Cinemachine** | 다이내믹 시티 투어 시점 |
| 센서 연동 | **ESP32 BLE** | 속도·거리 실시간 수신 |
| UI 시스템 | Unity UI + DOTween | 다국어/애니메이션 팝업 |
| 서버·웹 | WebView + REST | 상점·공지·랭킹 등 연동 |

---

## 🧭 기능 구조

```

메인 로비
├─ 닉네임/캐릭터 선택
├─ 센서 연결 상태 표시
├─ 맵 선택 (Green/Red Line 등)
├─ 상점 / 우편함 / 설정

맵 진입
├─ 실시간 속도 → 캐릭터 전진
├─ Cinemachine 경로 카메라
├─ 거리·속도·칼로리 HUD
└─ 주행 완료 → 결과·통계 출력

```

---

## 🗂 디렉터리 개요

```

CYCLING\_TOUR/
├─ Sensor/          # BLE 데이터 수신·해석
├─ AsiaMap/         # 메인 맵·카메라·플레이어
├─ MapChoice/       # 맵 선택·아이템 사용
├─ Popup/           # 상점·설정·우편함 WebView
├─ Lobby/, Join/    # 진입·가입·로비 UI
├─ Loading/         # 로딩 씬 매니저
├─ CharacterChoice/ # 캐릭터 커스터마이징
└─ Server/          # 랭킹·닉네임 서버 통신

```

---

## 🧠 주요 스크립트 설명

| 스크립트 | 핵심 역할 |
|----------|-----------|
| **`L_ESP32BLEApp.cs`** | BLE 센서 패킷 수신 → 속도·거리·칼로리 계산 후 전역 이벤트로 브로드캐스트 |
| **`Man_Move.cs` / `Woman_Move.cs`** | 실시간 속도 값으로 캐릭터 이동·애니메이션 속도 제어 (`Translate`+`Animator.speed`) |
| **`CM_VCamCtrl.cs`** | Cinemachine 가상 카메라를 맵 구간별로 스위치, 회전·줌 값 동적 조정 |
| **`AsiaMap_UIManager.cs`** | 주행 HUD(속도·거리·시간·칼로리) 업데이트, 체크포인트 도착 팝업 표시 |
| **`MapChoice_UIManager.cs`** | 맵 리스트·난이도·아이템 사용 팝업 처리 및 `SceneManager.LoadScene()` 호출 |
| **`StoreBuyPopupCtrl.cs`** | WebView 내 상점 페이지 띄우기, JSON 응답 파싱 → 구매 결과 적용 |
| **`MailBoxPopupCtrl.cs` / `NoticeCtrl.cs`** | 우편함·공지사항 팝업 열기/닫기, 서버 메시지 목록 로드 |
| **`Join_AppManager.cs`** | 최초 실행 시 사용자 설정·닉네임·센서 페어링 흐름 관리 |
| **`OBJCtrl.cs`** *(Sensor/)* | BLE 센서 객체 풀 관리, 실시간 값 smoothing 처리 |
| **`GameTime.cs`** | 주행 시간·거리 계산 로직, 완료 조건 및 결과 씬 전환 트리거 |

---

## 🌱 주요 기여 내용

| 기간 | 작업 |
|------|------|
| **2023.01 ~** | **영문 버전 전체 로컬라이징**<br>텍스트 CSV 테이블·거리/단위 변환·다국어 UI |
| **2023.04 ~** | **부산역 Green Line 신규 맵 개발**<br>레벨 디자인·오브젝트 최적화·Cinemachine 경로 |
| **2023.06 ~** | **WebView 상점 시스템**<br>상품 JSON 파싱·결제 결과 처리·UX 설계 |

---

## 📸 센서(FIT-TAG) 소개

<details>
<summary>이미지 보기</summary>

<p align="center">
  <img src="https://github.com/JISUSAMA/JISUSAMA/assets/38304918/4b84d9a0-569c-4027-810c-6f1f1b34545c" width="50%"><br>
  <img src="https://github.com/JISUSAMA/JISUSAMA/assets/38304918/f4bcd9c6-b792-4473-a7ad-4d5238edf4ea" width="50%"><br>
  <img src="https://github.com/JISUSAMA/JISUSAMA/assets/38304918/94416305-db7d-4df0-9d3b-84c33f463936" width="50%"><br>
  <img src="https://github.com/JISUSAMA/JISUSAMA/assets/38304918/c04f962c-05e9-474a-b15e-67cdce735753" width="50%">
</p>

</details>

---
## 🎥 홍보 영상
| 시티투어 부산 소개 영상 |
|------------------------|
| [![Video](http://img.youtube.com/vi/791rWW2YYak/0.jpg)](https://www.youtube.com/watch?v=791rWW2YYak) |

