<div align="center">

# 🕹️ KeyAxis

**キーボード／マウスを「滑らかなジョイスティック軸」に変換して DCS World を操作するツール**
*Fly DCS World with your keyboard & mouse — as smooth analog joystick axes.*

[![Release](https://img.shields.io/github/v/release/kimuti-takuya/KeyAxis?label=download&color=0a84ff)](https://github.com/kimuti-takuya/KeyAxis/releases/latest)
[![Platform](https://img.shields.io/badge/platform-Windows%2010%20%2F%2011-blue)](#)
[![Downloads](https://img.shields.io/github/downloads/kimuti-takuya/KeyAxis/total)](https://github.com/kimuti-takuya/KeyAxis/releases)

**[⬇️ 最新版をダウンロード / Download latest](https://github.com/kimuti-takuya/KeyAxis/releases/latest)**

[日本語](#-日本語) ・ [English](#-english)

</div>

```
キーボード/マウス ──(KeyAxis)──▶ vJoy 仮想スティック ──▶ DCS が「ジョイスティック軸」として認識
keyboard/mouse  ──(KeyAxis)──▶ vJoy virtual stick   ──▶ DCS sees real "joystick axes"
```

> 🌐 **対応言語 / Languages:** 日本語 ・ English ・ 繁體中文 ・ 简体中文 ・ Русский ・ 한국어
> （アプリの Status タブで切替 / switch on the **Status** tab）

---

## 🇯🇵 日本語

DCS World はキーボードを *ボタン* としてしか扱えず、操縦桿やスロットルの **軸（アナログ入力）** として直接認識できません。**KeyAxis** はキー入力を **vJoy 仮想スティック**の滑らかな軸出力に変換し、DCS に本物の HOTAS の軸として認識させます。速度・最大入力・カーブ・トリムなどはすべてアプリ側で細かく制御できます。

> ⚠️ 本ソフトは**非公式ツール**です。DCS World / Eagle Dynamics とは一切関係ありません。**無保証・自己責任**でご利用ください。

### ✨ 主な機能
- **8軸対応** — ロール / ピッチ / ラダー / 左右スロットル / TDC(X·Y) / レーダー仰角
- **軸ごとの細かな調整** — 速度・最大入力・カーブ・イーズ（端での減速／戻り時の減速／効き始め位置）・「離すと中央へ戻る／位置を保持」・戻り速度・左右同時押しの挙動（相殺／後勝ち／保持）
- **1つの操作に複数キー**を割り当て可能。修飾キー（Ctrl/Shift/Alt/Win・**左右を区別**）／マウス左右・サイド・中ボタン・ホイールにも対応
- **入力キャプチャ＋vJoy出力を “キーひとつでON/OFF”**（無効中はオーバーレイに赤い「×／OFF」を表示）
- **TDCスルーを2プロファイル**（**R=レーダー / T=TGP**）持ち、キーで切替。十字オーバーレイの右上に R/T を表示
- **スロットル** — 左右独立／両方同時（差を保ったまま同量移動）／クイック移動／デテント（OFF→IDLE→60%→MIL→AB）／OFF⇔IDLE／AB境界線／最大入力制限
- **トリム**（ピッチ・ロールの中立点を専用キーで微調整）、**スナップ**（一気に最大／最小）
- **DCS風オーバーレイ** — 十字（操縦桿の点・最大入力の枠・ラダー・トリム）、各軸のメーター（最大入力＝橙／感度＝水色）、スロットルの現在値（L=緑／R=白）。**要素ごとに自由配置**でき、プレイ中は**完全クリック透過**
- **ゲーム中に調整** — `Ctrl+ホイール`＝最大入力 / `Alt+ホイール`＝感度（調整量も設定可）
- **プリセット** — キー配列＋全設定を丸ごと保存・切替
- **6言語対応** — 日本語 / English / 繁體中文 / 简体中文 / Русский / 한국어（Status タブで切替）、**自動アップデート**（追加設定不要）

### 🚀 はじめかた
1. **[最新版をダウンロード](https://github.com/kimuti-takuya/KeyAxis/releases/latest)** して `KeyAxis.exe` を実行（**Python 不要・単一ファイル**）。
2. 初回起動時に**免責事項**へ同意。
3. 仮想ジョイスティックドライバ **vJoy** が必要です。未導入なら起動時に案内が出ます（下記）。
4. DCS の `OPTIONS → CONTROLS` で各軸に `vJoy Device` を割り当て（[軸割り当て表](#-dcs側の軸割り当て)）。

### 🔧 vJoy のセットアップ（ドライバは必須・1回だけ）
DCS に「本物のスティック」として認識される軸を作るには、Windows の**カーネルモードドライバ**が必要です（exe 単体には埋め込めません）。

- **自動（推奨）**：起動時に vJoy を検査し、未導入なら同梱インストーラの実行を、8軸が未設定なら自動設定を提案します。いつでも **Status タブ →「vJoy 自動セットアップ」** から実行可。ドライバ設定変更時は **UAC の確認に「はい」** を押してください。
- **手動**：vJoy をインストール → スタートメニューの **"Configure vJoy"** → **Device 1** の軸を **8個すべて有効**（X, Y, Z, Rx, Ry, Rz, Slider1, Slider2）→ Apply。

### 🎯 DCS側の軸割り当て
`OPTIONS → CONTROLS` で機体の各軸 (Axis) 列に `vJoy Device` の軸を割り当てます。

| DCS のコントロール | vJoy 軸 |
|---|---|
| Pitch | **Y** |
| Roll | **X** |
| Rudder | **Slider 2** |
| Throttle (Left) | **Z** |
| Throttle (Right) | **RX** |
| TDC Horizontal | **RY** |
| TDC Vertical | **RZ** |
| Radar Elevation | **Slider 1** |

> 向きが逆なら DCS の **Axis Tune → Invert**。キーの飲み込み（swallow）を確実にするため、DCS は**ボーダーレス・フルスクリーン**推奨です。

### ⌨️ デフォルトのキー（設定画面で変更可）
| 操作 | 既定キー |
|---|---|
| ピッチ 上 / 下 | ↑ / ↓ |
| ロール 左 / 右 | ← / → |
| ラダー 左 / 右 | , / . |
| スティックを中央へ | C |
| トリム ピッチ上 / 下 | ; / ' |
| トリム ロール左 / 右 | [ / ] |
| トリム リセット | U |
| 最大入力 +/- | Ctrl+ホイール |
| 感度 +/- | Alt+ホイール |
| ★最大入力の対象 / ■感度の対象 | Ctrl+1 / Ctrl+2 |
| スロットル両方 上 / 下 | PageUp / PageDown |
| スロットル両方（速く） | Shift+PageUp / Shift+PageDown |
| デテント 次 / 前 | Num+ / Num- |
| スロットル OFF⇔IDLE | Ctrl+Home |
| TDC 上/下/左/右 | Num8 / Num2 / Num4 / Num6 |
| レーダー仰角 上 / 下 | Home / End |
| オーバーレイ表示切替 | Insert |

**既定では未割り当て**（必要に応じてキー割り当てタブで設定）：入力ON/OFF切替・TDCスルー切替(R/T)・スナップ各種・中央へ戻すON/OFF切替・ピッチ上限方向の切替。

> キー割り当ては Keybinds タブで **「設定」** を押して入力するだけ。**「追加」** で同じ操作に複数キーを登録できます。修飾キー単体（Shift/Ctrl/Alt/Win）も割り当て可能です。

### 🖥️ オーバーレイ
- 対象ウィンドウ（DCS）が前面のときだけ表示。**完全クリック透過**で操作の邪魔をしません。
- 「位置調整…」で**各要素を個別にドラッグ**して好きな場所へ。位置は対象ウィンドウからの相対で保存され、次回も追従します。
- 表示中の TDC プロファイルを**右上に R/T**、入力が無効なら**赤い ×/OFF** を表示。

### 💾 プリセット
複数のプリセット（**キー配列＋全設定**）を作成・複製・改名・削除・切替・保存。機体ごとに使い分けられます。

### 🔄 自動アップデート
起動時に最新リリースを確認し、新しければ更新を提案します（許可すると自動でダウンロード・差し替え・再起動）。追加設定は不要です。

### 🩹 困ったとき
- **軸が動かない** → Status タブの vJoy 表示が `acquired` か確認。Configure vJoy で Device 1 の 8 軸が有効か確認。
- **キーが DCS にも効く** → Status タブの「Swallow bound keys」を ON。漏れるなら DCS をボーダーレス・フルスクリーンに。
- **オーバーレイが見えない／薄い** → オーバーレイタブで「位置調整…」して配置、Opacity を上げる。
- **設定を初期化** → 設定は `%USERPROFILE%\.dcs_keyaxis\config.json`。削除すれば初期化されます。

---

## 🇬🇧 English

DCS World only treats the keyboard as *buttons* — it can't read it as the analog **axes** of a stick or throttle. **KeyAxis** converts your key presses into the smooth axis output of a **vJoy virtual stick**, so DCS sees them as a real HOTAS. Speed, max travel, curvature, trim and more are all shaped inside the app.

> ⚠️ This is **unofficial software**, **not affiliated with** DCS World / Eagle Dynamics. Provided **as-is, no warranty, use at your own risk.**

### ✨ Features
- **8 axes** — roll / pitch / rudder / left & right throttle / TDC (X·Y) / radar elevation
- **Per-axis shaping** — speed, max-input limit, curvature, easing (near the limit / on return / where it starts), return-to-center vs hold, return speed, and L+R-together behavior (cancel / overwrite / hold)
- **Multiple keys per action**; modifiers (Ctrl/Shift/Alt/Win, **left/right distinct**), mouse L/R/middle/side buttons and the wheel
- **Toggle the whole capture + vJoy output with a single key** (a red “×/OFF” shows on the overlay when disabled)
- **Two TDC slew profiles** (**R = radar / T = TGP**) switchable by a key; the active one shows as R/T on the overlay
- **Throttle** — independent L/R, both-together (keeps their offset), quick mode, detents (OFF→IDLE→60%→MIL→AB), OFF⇔IDLE, an afterburner-gate line, max-input cap
- **Trim** (nudge pitch/roll neutral with dedicated keys) and **Snap** (jump straight to max/min)
- **DCS-style overlay** — stick cross (dot, max-input edges, rudder, trim), per-axis meters (max = amber / sensitivity = cyan), live throttle (L = green / R = white). Each element is **freely placeable** and **fully click-through** in flight
- **In-game tuning** — `Ctrl+Wheel` = max input, `Alt+Wheel` = sensitivity (step size configurable)
- **Presets** — save & switch a whole key layout + all settings
- **6 languages** — 日本語 / English / 繁體中文 / 简体中文 / Русский / 한국어 (switch on the Status tab), **auto-update** (no setup needed)

### 🚀 Getting started
1. **[Download the latest release](https://github.com/kimuti-takuya/KeyAxis/releases/latest)** and run `KeyAxis.exe` (**single file, no Python**).
2. Accept the disclaimer on first launch.
3. You need the free **vJoy** driver. If it's missing, the app offers to set it up on launch (see below).
4. In DCS `OPTIONS → CONTROLS`, bind `vJoy Device` axes (see the [mapping](#-dcs側の軸割り当て) table above).

### 🔧 vJoy setup (driver required, once)
A kernel-mode driver is required to expose axes DCS recognizes as a real stick (it can't be embedded in the exe).
- **Automatic (recommended):** the app checks vJoy at launch and offers to run the bundled installer / auto-enable the 8 axes. Available any time via **Status tab → “vJoy auto-setup”**. Click **Yes** on the UAC prompt.
- **Manual:** install vJoy → open **“Configure vJoy”** → enable **all 8 axes** on **Device 1** (X, Y, Z, Rx, Ry, Rz, Slider1, Slider2) → Apply.

### 🎯 DCS axis mapping
| DCS control | vJoy axis |
|---|---|
| Pitch | **Y** |
| Roll | **X** |
| Rudder | **Slider 2** |
| Throttle (Left) | **Z** |
| Throttle (Right) | **RX** |
| TDC Horizontal | **RY** |
| TDC Vertical | **RZ** |
| Radar Elevation | **Slider 1** |

> Reverse direction with DCS **Axis Tune → Invert**. Run DCS in **borderless fullscreen** so key-swallowing works reliably.

### ⌨️ Default keys (rebindable)
Arrows = pitch/roll, `,`/`.` = rudder, `C` = center, `;`/`'`/`[`/`]` = trim, `U` = trim reset, `Ctrl/Alt+Wheel` = max-input/sensitivity, `PageUp/Down` (`+Shift` = fast) = throttle, `Num+/Num-` = detent, `Ctrl+Home` = throttle OFF⇔IDLE, `Num8/2/4/6` = TDC, `Home/End` = radar, `Insert` = overlay. **Unbound by default:** input ON/OFF toggle, TDC R/T toggle, snap, return-to-center toggles, pitch-limit direction. Bind them in the **Keybinds** tab (use **“Add”** for multiple keys per action).

### 🖥️ Overlay / 💾 Presets / 🔄 Auto-update
The overlay shows only while DCS is focused, is fully click-through, and each element can be dragged into place (saved relative to the DCS window). Presets store a whole key layout + all tuning, switchable per aircraft. The app checks for a newer release on launch and offers a one-click self-update.

### 🩹 Troubleshooting
- **No axis movement** → check the vJoy status reads `acquired`; verify Device 1 has all 8 axes enabled.
- **Keys leak into DCS** → enable “Swallow bound keys”; run DCS borderless fullscreen.
- **Overlay invisible/faint** → use “Reposition…”, raise Opacity.
- **Reset settings** → delete `%USERPROFILE%\.dcs_keyaxis\config.json`.

---

<div align="center">
<sub>KeyAxis — unofficial, not affiliated with DCS World / Eagle Dynamics. Use at your own risk.</sub>
</div>
