<div align="center">

# 🛟 KeyAxis トラブルシューティング / Troubleshooting

[日本語](#-日本語) ・ [English](#-english)

</div>

---

## 🇯🇵 日本語

### 🔴 DCS のキー割り当てが消えた／欄がズレた（HOTAS のバインドが空になった）

> **まず落ち着いてください。ほとんどの場合、バインドは消えていません。**
> DCS が「別デバイス」と勘違いして表示できていないだけで、設定ファイルはディスクに残っています。

#### なぜ起きる？
DCS はキーバインドを **「デバイス名 ＋ ハードウェアID(GUID)」のファイル名**で保存します（例：`Joystick - HOTAS Warthog {E9E49100…}.diff.lua`）。
**Windows 側でそのデバイスの“表示名”が変わる**と（Windows更新、ドライバの再認識、USBポート変更、仮想デバイス追加に伴う再列挙など）、GUID は同じでも名前が変わるため、DCS は「知らない新しいデバイス」と判断し、**空の新ファイル**を作ります。その結果バインドが消えた・欄がズレたように見えます。元のバインドは**旧名のファイルにそのまま残っています**。

> ℹ️ これは **KeyAxis / vJoy が原因ではありません**。両者は DCS の設定ファイルやデバイスの登録名に一切書き込みません。仮想デバイス(vJoy)を足すと DCS のデバイス一覧（列）は変化しますが、他デバイスのバインドを消すことはありません。

#### ⚠️ 最初に必ず：バックアップ
何かする前に、このフォルダを丸ごとコピーして保管してください（数秒）。
```
%USERPROFILE%\Saved Games\DCS\Config\Input
```
（OpenBeta は `Saved Games\DCS.openbeta\Config\Input`）

#### 復旧方法A：バインドファイルをコピーする（レジストリを触らない・安全）
1. **DCS を完全終了**する。
2. 上記 `Input` フォルダを開く。各機体フォルダの中の `joystick\` を見る。
3. 同じ `{GUID}` で**名前だけ違う** `.diff.lua` が2つある機体を探す：
   - **中身がある方**（ファイルサイズが大きい／日付が古い）＝あなたの本来のバインド（旧名）。
   - **空に近い方**（数百バイト／今日の日付）＝名前が変わった後の新ファイル。
4. **中身がある方をコピー**し、コピーの名前を**空ファイルとまったく同じ名前**に変更して、空ファイルを置き換える。
5. DCS を起動 → バインドが戻ります。

#### 復旧方法B：デバイス名を元に戻す（根本修正・1回で全機体復活）
1. どのデバイスの名前が化けたか確認（PowerShell に貼り付け）：
   ```powershell
   Get-ChildItem 'HKCU:\System\CurrentControlSet\Control\MediaProperties\PrivateProperties\Joystick\OEM' |
     ForEach-Object { "{0} = {1}" -f $_.PSChildName, (Get-ItemProperty $_.PSPath).OEMName }
   ```
   → 「2 軸 19 ボタン ジョイスティック…」のような**汎用名**になっている `VID_xxxx&PID_xxxx` が犯人です。
2. **正しい名前**は、`Input` フォルダにある**あなたのバインドが入ったファイルの名前**の ` {` より前の部分です（例：`Joystick - HOTAS Warthog`）。
3. 名前を戻す（`VID_xxxx&PID_xxxx` と名前を自分の値に置き換え）：
   ```powershell
   Set-ItemProperty -LiteralPath 'HKCU:\System\CurrentControlSet\Control\MediaProperties\PrivateProperties\Joystick\OEM\VID_xxxx&PID_xxxx' -Name OEMName -Value '正しいデバイス名'
   ```
4. **デバイスを挿し直す**（同じ USB ポート推奨）か **PC を再起動** → DCS 起動で元のバインドに自動で戻ります。

#### 🛡️ 予防
- HOTAS は**いつも同じ USB ポート**に挿す（差し替えで GUID が変わることがある）。
- ドライバ（Thrustmaster TARGET 等）を再インストールした後は名前が変わっていないか確認。
- たまに `Saved Games\DCS\Config\Input` をコピーして保管（数秒の保険）。

---

### 軸が動かない
- KeyAxis の **Status タブ**で vJoy 表示が `acquired` か確認。
- **Configure vJoy** で **Device 1** の **8軸**（X, Y, Z, Rx, Ry, Rz, Slider1, Slider2）が有効か確認。
- DCS の `CONTROLS` で各軸に `vJoy Device` を割り当てたか確認（Pitch=Y / Roll=X / Rudder=Slider2 / ThrL=Z / ThrR=RX / TDC=RY,RZ / Radar=Slider1）。

### キー入力が DCS にも漏れる
- Status タブの **「割り当てキーを飲み込む」** を ON。
- それでも漏れるなら DCS を**ボーダーレス・フルスクリーン**で起動（排他的フルスクリーンだと低レベルフックが届かないことがあります）。

### オーバーレイが見えない／薄い／動かせない
- 対象ウィンドウ（DCS）が前面の時だけ表示されます。
- オーバーレイタブの **Opacity** を上げる。**「位置調整…」** で配置し直して「確定」。

### 設定を初期化したい
- 設定は `%USERPROFILE%\.dcs_keyaxis\config.json`。削除すると初期化されます。

---

## 🇬🇧 English

### 🔴 My DCS bindings disappeared / a device column shifted (HOTAS binds look wiped)

> **Don't panic — in almost all cases your binds are NOT deleted.** DCS just can't match them because the device's *name* changed in Windows. The files are still on disk.

#### Why it happens
DCS stores bindings in files named **"device name + hardware id (GUID)"** (e.g. `Joystick - HOTAS Warthog {E9E49100…}.diff.lua`). If Windows changes that device's *friendly name* (a Windows/driver update, USB port change, re-enumeration after adding a virtual device, etc.), the GUID is the same but the name differs, so DCS treats it as a **new device** and creates **empty** bind files. Your original binds are still there under the **old name**.

> ℹ️ This is **not caused by KeyAxis / vJoy** — neither writes to DCS config or to the device's Windows name. Adding a virtual device (vJoy) changes DCS's device list/columns, but it never deletes another device's binds.

#### ⚠️ First: back up
Before anything, copy this whole folder somewhere safe:
```
%USERPROFILE%\Saved Games\DCS\Config\Input
```
(OpenBeta: `Saved Games\DCS.openbeta\Config\Input`)

#### Fix A: copy the bind files (no registry, safest)
1. **Fully close DCS.**
2. Open the `Input` folder above; in each aircraft's `joystick\` folder look for **two** `.diff.lua` files with the **same `{GUID}`** but different name prefixes:
   - the **larger / older** one = your real binds (old name);
   - the **near-empty / today-dated** one = the renamed device.
3. **Copy the file that has your binds**, then rename the copy to **exactly** the empty file's name, replacing it.
4. Start DCS — your binds are back.

#### Fix B: restore the device's name (root fix, all aircraft at once)
1. Find which device was renamed (paste into PowerShell):
   ```powershell
   Get-ChildItem 'HKCU:\System\CurrentControlSet\Control\MediaProperties\PrivateProperties\Joystick\OEM' |
     ForEach-Object { "{0} = {1}" -f $_.PSChildName, (Get-ItemProperty $_.PSPath).OEMName }
   ```
   The `VID_xxxx&PID_xxxx` showing a generic name (e.g. "2 axis 19 button joystick…") is the culprit.
2. The **correct name** is the part before ` {` in your binds file's name (e.g. `Joystick - HOTAS Warthog`).
3. Restore it (replace the VID/PID and the name with yours):
   ```powershell
   Set-ItemProperty -LiteralPath 'HKCU:\System\CurrentControlSet\Control\MediaProperties\PrivateProperties\Joystick\OEM\VID_xxxx&PID_xxxx' -Name OEMName -Value 'Correct Device Name'
   ```
4. **Re-plug the device** (same USB port) or **reboot**, then start DCS — binds return automatically.

#### 🛡️ Prevention
- Always use the **same USB port** for your HOTAS.
- After reinstalling a driver, check the name didn't change.
- Occasionally back up `Saved Games\DCS\Config\Input`.

---

### Other quick fixes
- **No axis movement** — check vJoy reads `acquired` (Status tab); enable all 8 axes on Device 1 in *Configure vJoy*; bind the `vJoy Device` axes in DCS (Pitch=Y, Roll=X, Rudder=Slider2, ThrL=Z, ThrR=RX, TDC=RY/RZ, Radar=Slider1).
- **Keys leak into DCS** — enable “Swallow bound keys”; run DCS borderless fullscreen.
- **Overlay invisible / faint / won't move** — it shows only while DCS is focused; raise Opacity; use “Reposition…”.
- **Reset settings** — delete `%USERPROFILE%\.dcs_keyaxis\config.json`.

---

<div align="center">
<sub>KeyAxis — unofficial, not affiliated with DCS World / Eagle Dynamics / Heatblur. Use at your own risk.</sub>
</div>
