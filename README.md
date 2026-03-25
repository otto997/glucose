https://otto997.github.io/glucose/

# glu — 葡萄糖數據摘要

一個純前端的連續血糖監測（CGM）數據視覺化工具，支援 LibreLink 匯出的 CSV 檔案，並可透過 LiteLLM 代理呼叫 AI 進行分析。

## 功能

- 解析 LibreLink 匯出的 CSV，支援多個 CGM 裝置期間
- 每日血糖折線圖，依血糖範圍自動著色
- 每日及整體統計：平均血糖、TIR（目標範圍內時間）、預估 HbA1c
- 備註紀錄表格，並與圖表互動高亮
- 透過 LiteLLM 代理呼叫 AI，批次產生每日分析與整體建議

## 快速開始

1. 將 LibreLink 匯出的 CSV 放至專案目錄，命名如 `glucose.csv`
2. 編輯 `config.json`，填入 CSV 檔名與 LiteLLM 設定：

```json
{
  "defaultCsv": "glucose.csv",
  "litellmUrl": "http://localhost:4000",
  "litellmKey": "sk-key",
  "litellmModel": "gpt-4o-mini"
}
```

3. 以任意 HTTP 伺服器啟動（例如：`npx serve .` 或 `python3 -m http.server`）
4. 用瀏覽器開啟 `index.html`

## 設定說明

| 欄位 | 說明 |
|---|---|
| `defaultCsv` | 自動載入的 CSV 檔名 |
| `litellmUrl` | LiteLLM proxy URL |
| `litellmKey` | API 金鑰（選填） |
| `litellmModel` | 使用的模型名稱 |

## 血糖範圍定義

| 範圍 | 數值 |
|---|---|
| 低血糖 | < 80 mg/dL |
| 目標範圍 | 80–130 mg/dL |
| 偏高 | 130–180 mg/dL |
| 過高 | > 180 mg/dL |

## 技術棧

- 純 HTML / CSS / JavaScript（無需打包）
- [Chart.js](https://www.chartjs.org/) 4.x
- LiteLLM（或相容 OpenAI API 的代理）
