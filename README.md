# 🎵 Strudel 中文教學

用程式碼寫音樂，探索 Live Coding 的魅力！

## 📖 專案簡介

這是一個 **Strudel** 的中文教學網站，Strudel 是一個強大的 live coding 音樂創作工具，讓你可以用程式碼即時創作音樂。本專案提供：

- 🎯 完整的中文基礎教學
- 🎵 豐富的音色介紹  
- 🎨 Pattern 編寫技巧
- ✨ 效果器使用指南
- 🎹 互動式編輯器
- 🌊 經典作品展示

## 🚀 快速開始

### 線上體驗
- **Vue 版本**：開啟 `vue-demo.html` 體驗現代化的 Vue.js 介面 (推薦)
- **原始版本**：開啟 `demo.html` 體驗基礎版本

### 本地運行
```bash
# 克隆專案
git clone [your-repo-url]
cd strudel-tutorial-zh

# 安裝依賴（如果需要）
npm install

# 開啟網頁
open demo.html
# 或使用 Live Server 等工具
```

## 📚 教學內容

### 🎯 基礎語法
- 鼓聲播放：`s("bd sd hh cp")`
- 旋律創作：`note("c4 e4 g4 b4")`
- Pattern 重複：`s("bd*4")`
- 聲部疊加：`stack()`

### 🎵 音色庫
- **鼓組**：bd (大鼓)、sd (小鼓)、hh (踩鈸)、cp (拍手)
- **合成器**：sawtooth、square、triangle、sine
- **真實樂器**：piano、bass、guitar、violin

### 🎨 Pattern 技巧
- 輪替播放：`<bd sd>`
- 群組編排：`[bd sd] hh`
- 休止符：`bd ~ sd ~`
- Pattern 反轉：`.jux(rev)`

### ✨ 效果器
- 低通濾波：`.lpf(800)` - 過濾高頻，營造溫暖感
- 動態音量：`.gain("[.25 1]*2")` - 創造節奏律動
- 母音濾波：`.vowel("a e i o")` - 模擬人聲質感
- 延遲效果：`.delay(".5:.125:.8")` - 回音與空間感
- 空間殘響：`.room(2)` - 模擬真實空間
- 聲道平移：`.pan("0 1")` - 立體聲定位
- 播放速度：`.speed("1 2 -1")` - 變速與倒播
- ADSR 包絡：`.adsr(".1:.1:.5:.2")` - 聲音包絡塑形
- 波形調制：`.lpf(sine.range(200, 2000))` - 自動化控制

## 🛠️ 技術架構

### Vue 版本 (推薦)
- **前端框架**：Vue.js 3 (CDN)
- **音樂引擎**：Strudel Web (`@strudel/web@1.2.3`)
- **編輯器**：Strudel REPL (`@strudel/repl@latest`)
- **UI 設計**：響應式設計，組件化架構，更好的互動性

### 原始版本
- **前端框架**：原生 HTML/CSS/JavaScript
- **音樂引擎**：Strudel Web (`@strudel/web@1.0.3`)
- **編輯器**：Strudel REPL (`@strudel/repl@latest`)
- **UI 設計**：響應式設計，支援桌面和行動裝置

## 📁 檔案結構

```
strudel-tutorial-zh/
├── vue-demo.html      # Vue.js 版本教學頁面 (推薦)
├── demo.html          # 原始版本教學頁面
├── demo.js            # JavaScript 初始化腳本
├── music.html         # 簡單音樂範例頁面
├── DJ_Dave.str        # 進階 Strudel 作品範例
├── package.json       # 專案配置
└── README.md          # 專案說明文件
```

## 🎵 範例程式碼

### 基礎節拍
```javascript
// 簡單的鼓組 pattern
s("bd sd hh cp")
```

### 旋律創作
```javascript
// C大調音階配上鋼琴音色
note("c4 e4 g4 b4").s("piano")
```

### 複合編排
```javascript
// 多聲部音樂
stack(
  s("bd*2 sd*2"),           // 鼓組
  s("hh*8").gain(0.4),      // 踩鈸
  note("c4 e4 g4 b4")       // 旋律
    .s("piano")
    .gain(0.6)
)
```

### 進階效果
```javascript
// 帶效果器的複雜 pattern
note("<c4 e4 g4 b4>*2")
  .scale('C4 minor')
  .s("sawtooth")
  .clip(sine.range(.2,.8).slow(8))
  .jux(rev)
  .room(0.5)
  .lpf(perlin.range(200,2000).slow(4))
```

### 完整 Dub 音樂範例
```javascript
// 四聲部 Dub 風格編排
stack(
  // 悶音電吉他和弦
  note("[~ [<[d3,a3,f4]!2 [d3,bb3,g4]!2> ~]]*2")
    .sound("gm_electric_guitar_muted")
    .delay(.5),
  
  // 經典鼓組節奏
  sound("bd rim")
    .bank("RolandTR707")
    .delay(.5),
  
  // 手風琴主旋律
  n("<4 [3@3 4] [<2 0> ~@16] ~>")
    .scale("D4:minor")
    .sound("gm_accordion:2")
    .room(2)
    .gain(.4),
  
  // 雙波形貝斯線
  n("[0 [~ 0] 4 [3 2] [0 ~] [0 ~] <0 2> ~]/2")
    .scale("D2:minor")
    .sound("sawtooth,triangle")
    .lpf(800)
)
```

## 🌟 特色功能

### Vue 版本新特色
- **現代化介面**：Vue.js 3 組件化架構，更流暢的使用體驗
- **即時狀態顯示**：播放/停止狀態指示器
- **載入狀態管理**：防止重複點擊，提供視覺回饋
- **智能按鈕控制**：自動禁用/啟用按鈕，避免操作衝突
- **分頁式學習**：清晰的分頁切換，動畫效果更佳

### 共同特色
- **互動式學習**：每個範例都可以直接點擊試聽
- **雙編輯器**：提供簡單和進階兩種編輯器
- **即時預覽**：修改程式碼後立即聽到效果
- **中文化介面**：完全繁體中文的學習環境
- **響應式設計**：支援各種螢幕尺寸

## 🤝 貢獻指南

歡迎提交 Issue 和 Pull Request！

### 貢獻方式
1. Fork 本專案
2. 創建新的功能分支 (`git checkout -b feature/新功能`)
3. 提交變更 (`git commit -m 'feat: 新增某某功能'`)
4. 推送到分支 (`git push origin feature/新功能`)
5. 開啟 Pull Request

### Commit 規範
請遵循以下 commit 格式：
- `feat`: 新功能
- `fix`: 修復問題  
- `docs`: 文件更新
- `style`: 格式調整
- `refactor`: 重構

## 📄 授權條款

本專案採用 MIT 授權條款 - 詳見 [LICENSE](LICENSE) 檔案

## 🔗 相關連結

- [Strudel 官方網站](https://strudel.cc/)
- [Strudel GitHub](https://github.com/tidalcycles/strudel)
- [Live Coding 社群](https://toplap.org/)

## 📞 聯絡方式

如有任何問題或建議，歡迎：
- 開啟 GitHub Issue
- 發送 Pull Request
- 加入 Live Coding 社群討論

---

**讓我們一起用程式碼創作美妙的音樂！** 🎵✨ 