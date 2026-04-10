# Arduino Mega 2560 — KiCad 原理圖繪製練習

## 練習目標

對照 `MEGA2560_Rev3e_sch.pdf` 參考圖，使用 KiCad 9.0 繪製 Arduino Mega 2560 Rev3 的完整原理圖。

## 分工架構

原理圖分為 **4 個子頁面**，每人負責一個區塊：

| 頁面 | 檔案 | 負責內容 |
|------|------|---------|
| Page 2 | `Section_01_USB_ATmega16U2.kicad_sch` | USB-C 接頭、ESD 保護、ATmega16U2 USB Bridge、晶振 Y2 |
| Page 3 | `Section_02_ATmega2560_MCU.kicad_sch` | ATmega2560 主控 MCU、去耦電容、Reset 電路、晶振 Y1 |
| Page 4 | `Section_03_Power_Supply.kicad_sch` | DC 電源座、NCP1117 5V、LP2985 3.3V、PMOS、LMV358 |
| Page 5 | `Section_04_Arduino_Headers.kicad_sch` | 所有 Arduino 腳位排針（數位/類比/電源） |

## 符號庫

專案已內建 `Arduino_Mega2560_Lib`，包含所有需要的元件符號，每個符號已預先連結好對應的 Footprint。

開啟專案後，在原理圖編輯器 `Place > Add Symbol`，從 `Arduino_Mega2560_Lib` 選取元件即可。

## Git 協作流程

### 初始設定

```bash
# 1. 先 fork 這個 repo 到你們組的帳號
# 2. Clone 到本機
git clone https://github.com/<你的組別>/kicad.git
cd kicad
```

### 每個人的工作流程

```bash
# 建立自己的 branch（以你負責的區塊命名）
git checkout -b section/01-usb-atmega16u2   # 依你的區塊修改

# 繪製原理圖後，只 commit 你負責的那個 .kicad_sch 檔
git add Arduino_Mega2560_Practice/Section_01_USB_ATmega16U2.kicad_sch
git commit -m "feat: complete USB ATmega16U2 section schematic"

# Push 到遠端
git push origin section/01-usb-atmega16u2

# 在 GitHub 發 Pull Request 給你們組的 main branch
```

### 合併注意事項

- 每個人只修改**自己負責的 `.kicad_sch` 檔**，不要動到其他人的檔案
- Root 主頁面 `Arduino_Mega2560_Practice.kicad_sch` 只有 4 個方框，不需要修改
- 合併後在 KiCad 開啟 `Arduino_Mega2560_Practice.kicad_pro` 就能看到完整原理圖

## 開啟方式

1. 開啟 KiCad 9.0
2. `File > Open Project` → 選擇 `Arduino_Mega2560_Practice/Arduino_Mega2560_Practice.kicad_pro`
3. 從 Project Manager 開啟原理圖編輯器
4. 在頁面選擇器切換到你負責的頁面開始繪製

## 參考資料

- 參考原理圖：`MEGA2560_Rev3e_sch.pdf`
- 符號庫：`Arduino_Mega2560_Practice/Arduino_Mega2560_Lib.kicad_sym`
- 自訂 Footprint：`Arduino_Mega2560_Practice/Arduino_Mega2560_FP.pretty/`
