# AUX-2 Grove LCD

给 Home Assistant Connect AUX-2 加装 Seeed Grove LCD RGB Backlight（16×2）。第一行显示播放状态和进度，例如 `PLAY 01:23/04:56`；第二行显示曲名和艺人，超出 16 字符时滚动。曲目信息由 Sendspin 提供；LCD 无法显示的字符会替换为 `?`。

## 安装

1. 将 LCD 接到 AUX-2 的 Grove 口。配置会启用 Grove 电源，并识别 V5（`0x30`）或 V4（`0x62`）的背光控制器。连接前请核对 [Seeed 的供电规格](https://wiki.seeedstudio.com/Grove-LCD_RGB_Backlight/)。
2. 把 [`aux-2-grove-lcd.yaml`](aux-2-grove-lcd.yaml) 放在设备 YAML 同一目录。在已有 `packages:` 下添加下面的 `grove_lcd` 条目，并保留原有 [AUX-2 包](https://github.com/NabuCasa/aux-2/blob/main/packages/aux-2.yaml)。

   ```yaml
   packages:
     # 保留原有 AUX-2 包条目
     grove_lcd: !include aux-2-grove-lcd.yaml
   ```

3. 如果通过 Improv 配网且设备 YAML 尚未启用 Improv，在顶层添加：

   ```yaml
   improv_ble:
     authorizer: none
   improv_serial:
   ```

4. 在 ESPHome Builder 中验证并编译**设备 YAML**。此配置已在 ESPHome **2026.11.0-dev** 上完整编译通过。

## 背光与状态

- **LCD Backlight**：手动调整颜色、亮度和开关。
- **LCD Automatic Color**：自动配色。播放为蓝色，暂停或播报为琥珀色，空闲为白色，检测到网络或设备错误时为红色。要保留手动颜色，请关闭此开关。
- **LCD Status**：在 Home Assistant 中查看播放或错误状态。

## 3D 打印

下载 [`Grove_LCD_R2_PC.3mf`](3d-print/Grove_LCD_R2_PC.3mf)，用支持 3MF 的切片软件打开。仓库保留了原始 3MF；切片前请核对打印机和材料设置。
