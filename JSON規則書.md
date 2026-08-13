# 補助資料 JSON 規則書（新版）

本文件說明如何新增、修改各縣市的補助查詢資料。  
所有資料檔案統一放在 `data/` 資料夾，**不需要修改任何程式碼**即可新增內容。

---

## 一、目錄結構與命名規則

```
data/
├── elderly/                          ← 長者補助
│   ├── denture-kaohsiung.json        ← 高雄市老人假牙補助
│   ├── denture-taipei.json           ← 臺北市老人假牙補助
│   ├── living-kaohsiung.json
│   └── ...
├── lowincome/                        ← 中低收入戶補助
│   ├── living-kaohsiung.json
│   └── ...
├── disability/                       ← 身心障礙補助
├── indigenous/                       ← 原住民及新住民補助
└── singleparent/                     ← 單親家庭補助
```

**命名格式**：`{type}-{county}.json`

### 類別（category）對照

| 目錄名稱 | 說明 |
|---|---|
| `elderly` | 長者補助 |
| `lowincome` | 中低收入戶補助 |
| `disability` | 身心障礙補助 |
| `indigenous` | 原住民及新住民補助 |
| `singleparent` | 單親家庭補助 |

### 補助項目（type）對照

**elderly（長者）**

| type | 說明 |
|---|---|
| `living` | 中低收入老人生活津貼 |
| `care` | 長期照顧服務補助 |
| `medical` | 老人醫療費用補助 |
| `transport` | 敬老卡／交通點數補助 |
| `ltc20` | 長照 2.0 服務補助 |
| `denture` | 老人假牙補助 |
| `chongyang` | 重陽敬老禮金 |

**lowincome（中低收入戶）**

| type | 說明 |
|---|---|
| `living` | 低收入戶生活扶助 |
| `edu` | 就學生活補助 |
| `medical` | 醫療補助 |
| `rent` | 中央擴大租金補貼 |
| `emergency` | 急難救助金／馬上關懷 |

**disability（身心障礙）**

| type | 說明 |
|---|---|
| `living` | 身心障礙者生活補助 |
| `care` | 日間照顧及住宿費用補助 |
| `assist` | 輔具費用補助 |
| `home` | 無障礙住宅改善補助 |
| `vehicle` | 專用車輛免稅及租屋補助 |

**indigenous（原住民及新住民）**

| type | 說明 |
|---|---|
| `edu` | 原住民族獎助學金 |
| `employ` | 就業促進補助 |
| `newresident` | 新住民生活適應輔導 |
| `newemergency` | 新住民急難救助與特殊境遇補助 |
| `skill` | 新住民及其子女技能檢定獎勵金 |
| `elderlyplus` | 原住民 55 歲以上長者敬老福利加碼 |

**singleparent（單親家庭）**

| type | 說明 |
|---|---|
| `living` | 單親家庭生活補助 |
| `childcare` | 兒童托育補助 |
| `edu` | 子女就學補助 |
| `childliving` | 特殊境遇家庭子女生活津貼 |
| `emergency` | 特殊境遇家庭緊急生活扶助 |
| `legal` | 法律訴訟與律師費補助 |

### 縣市 ID（county）對照

**檔名 county 部分必須使用下方 ID（小寫英文、連字號）：**

| 縣市 | county ID | 縣市 | county ID |
|---|---|---|---|
| 臺北市 | `taipei` | 嘉義市 | `chiayi-city` |
| 新北市 | `new-taipei` | 嘉義縣 | `chiayi` |
| 桃園市 | `taoyuan` | 屏東縣 | `pingtung` |
| 臺中市 | `taichung` | 宜蘭縣 | `yilan` |
| 臺南市 | `tainan` | 花蓮縣 | `hualien` |
| 高雄市 | `kaohsiung` ✅ | 臺東縣 | `taitung` |
| 基隆市 | `keelung` | 澎湖縣 | `penghu` |
| 新竹市 | `hsinchu-city` | 金門縣 | `kinmen` |
| 新竹縣 | `hsinchu` | 連江縣 | `lienchiang` |
| 苗栗縣 | `miaoli` | 彰化縣 | `changhua` |
| 南投縣 | `nantou` | 雲林縣 | `yunlin` |

---

## 二、JSON 結構說明

```json
{
  "county": "高雄市",
  "category": "elderly",
  "type": "denture",
  "title": "老人假牙補助",
  "intro": "補助說明文字（一段）",
  "conditions": [
    "申請條件一",
    "申請條件二"
  ],
  "documents": [
    "所需文件一",
    "所需文件二"
  ],
  "steps": [
    "申辦步驟一",
    "申辦步驟二"
  ]
}
```

### 欄位說明

| 欄位 | 必填 | 說明 |
|---|---|---|
| `county` | ✅ | 縣市中文名稱，顯示於結果標題 |
| `category` | ✅ | 身分類別（對應目錄名稱） |
| `type` | ✅ | 補助項目代號（對應 type 對照表） |
| `title` | ✅ | 補助項目中文名稱 |
| `intro` | ❌ 選填 | 補助說明，顯示為簡介段落 |
| `conditions` | ❌ 選填 | 申請條件，顯示為條列清單 |
| `documents` | ❌ 選填 | 所需文件，顯示為可勾選 Checklist |
| `steps` | ❌ 選填 | 申辦流程，顯示為編號步驟 |

---

## 三、完整範例

```json
{
  "county": "高雄市",
  "category": "elderly",
  "type": "denture",
  "title": "老人假牙補助",
  "intro": "65歲以上之低收入戶、中低收入戶老人，因缺牙影響咀嚼功能，可申請假牙製作費用補助，每3年可申請一次。",
  "conditions": [
    "年滿 65 歲以上",
    "設籍高雄市",
    "領有低收入戶或中低收入戶證明",
    "缺牙影響咀嚼功能（需特約牙科診所確認）"
  ],
  "documents": [
    "國民身分證",
    "低（中低）收入戶證明",
    "牙科診斷書或治療計畫書（特約醫療院所開立）",
    "存摺封面影本"
  ],
  "steps": [
    "至特約牙科診所檢查並確認需製作假牙",
    "取得診斷書後向戶籍地公所社會課或社會局申請",
    "審查資格並核定補助金額",
    "至特約牙科完成假牙製作",
    "核定後補助款項退費至帳戶"
  ]
}
```

---

## 四、新增資料完整步驟

### 步驟 1：建立 JSON 檔案

在 `data/{category}/` 資料夾新增 `{type}-{county}.json`，依照上方格式填寫。

### 步驟 2：在 HTML 的 SUBSIDY_MAP 登記

打開主頁面 HTML，找到 `SUBSIDY_MAP` 物件，將縣市 ID 加入對應的 category/type 陣列：

```js
const SUBSIDY_MAP = {
  elderly: {
    denture: ["kaohsiung", "taipei"],   // ← 在此加入新縣市 ID
  }
};
```

### 步驟 3：完成

存檔後重新整理，選擇對應身分與項目後，地圖上該縣市即會亮起可點擊。

---

## 五、注意事項

1. **JSON 格式必須合法** — 最後一個項目後面不能有多餘的逗號，可用 [jsonlint.com](https://jsonlint.com) 驗證
2. **字串用雙引號** — JSON 規定所有字串必須用 `"` 雙引號
3. **必須透過 HTTP server 開啟** — 直接雙擊 HTML 無法讀取 JSON，請使用 VS Code Live Server
4. **檔名全部小寫** — category、type、county 皆為小寫英文加連字號
