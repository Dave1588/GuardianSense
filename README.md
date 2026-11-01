# GuardianSense 居安衛士

**A Domain AI Agent for In-Home Fall Detection of Older Adults with Wearable Sensing, Two-Way Voice Confirmation, and Knowledge-Grounded Reporting**

結合穿戴式感測、雙向語音確認與領域知識的高齡者居家跌倒偵測代理人。

> 2026 AIIS 課程期末專題 ｜ 目前階段：**Proposal**（尚未實作）

---

## 專題簡介

獨居長者跌倒後，最大的危險往往是「無法起身、無人知道」。傳統緊急按鈕仰賴長者主動按壓，而自動跌倒偵測在真實居家環境中誤報頻繁，造成家屬警報疲勞。

GuardianSense 是一個居家安全 AI Agent，目標是在**不降低真實跌倒偵測率**的前提下，**大幅減少推送給家屬的誤報**：

- **兩階段跌倒偵測**：腰戴 IMU 加速度門檻預篩 + CNN-LSTM 分類，並以跌倒後靜止與姿態驗證。
- **風險分級的雙向語音確認**：中度可信事件先以語音詢問長者，LLM 解讀回覆意圖；無回應一律通報（fail-safe）。
- **主動求救**：語音關鍵字或實體按鍵直接求救。
- **知識增強的照護報告**：以 RAG 檢索 WHO、CDC、國健署防跌指引，將每日活動趨勢轉為家屬可執行的建議。

## 系統架構（規劃）

```
① 使用者 → ② 輸入（IMU / 語音 / 求救鍵 / 家屬 Bot）→ ③ LLM 規劃與推理
→ ④ 資料取得（MQTT / 時序 DB）→ ⑤ 分析引擎（兩階段偵測 / 趨勢分析）
→ ⑥ 領域知識（RAG）→ ⑦ 風險分級決策（確定性規則）→ ⑧ 輸出（語音 / 警報 / Dashboard）
```

## 預計技術

| 類別 | 技術 |
| :--- | :--- |
| 感測硬體 | ESP32 + MPU6050（開發期以 SisFall 資料重播模擬） |
| 即時串流 | MQTT（Mosquitto） |
| 偵測模型 | PyTorch CNN-LSTM |
| 語音 / LLM | STT / TTS API、LLM API（意圖分類、報告生成） |
| 知識庫 | Embedding + Chroma |
| 通知 / 介面 | LINE Messaging API、Streamlit |

## 資料集

- [SisFall](https://doi.org/10.3390/s17010198)：主要訓練與測試
- [UP-Fall](https://doi.org/10.3390/s19091988)：跨資料集驗證

## Installation / How to Run

🚧 實作階段補上。

## 專題進度

- [x] Proposal
- [ ] 偵測模型實作與實驗
- [ ] 語音確認與決策模組
- [ ] RAG 照護報告與 Dashboard
- [ ] Final Handover
