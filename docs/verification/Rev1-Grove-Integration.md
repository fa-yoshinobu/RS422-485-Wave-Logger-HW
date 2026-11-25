# Rev1のGrove追加記録（2026-11-24）

この資料は11月24日版の検証記録です。現行版の製造工程と検証結果は[11月25日版の報告](Rev1-DFM.md#2026-11-25-発注用データ)を参照してください。

Rev1の回路図・基板・製造データにGrove 2口を反映した。旧差分 `pcb/variants/Grove-next.patch` の内容は回路図に反映済み。

## 回路

| 部品 | 内容 | 接続 |
|---|---|---|
| J7 | Grove I²C、`Tap:Grove_110990037_RightAngle` | 1 J7_SCL / 2 J7_SDA / 3 3V3 / 4 GND |
| J8 | Grove GPIO/ADC、同上 | 1 J8_IO1 / 2 J8_IO2 / 3 3V3 / 4 GND |
| R49 / R50 | 100 Ω 0603（C22775） | GROVE_SCL（U1 F36 PA15）–J7_SCL、GROVE_SDA（F35 PB4）–J7_SDA |
| R51 / R52 | 100 Ω 0603（C22775） | GROVE_IO1（F37 PA5）–J8_IO1、GROVE_IO2（F38 PA0）–J8_IO2 |
| R53 / R54 | 4.7 kΩ 0603、**実装（C23162）** | 3V3–GROVE_SCL、3V3–GROVE_SDA |

## 配置と検証

- J7は (35.00, 95.10) mm、J8は (55.00, 95.10) mmの表面。両口とも挿入口を手前（+Y）の y = 100.00 mmにそろえた。液晶基板下面との公称隙間は6.04 mm。ケーブルと指先を仮定した通過経路をCADで確認した。実物でのラッチ解除は未確認。[基板配置](../PCB-Rev1.md)・[ケースの組み立て](../../enclosure/drawings/Assembly.md)
- R49～R54は裏面。J7のI²Cクロック（SCL）はR53、データ（SDA）はR54で、それぞれ4.7 kΩを介して3.3 Vへプルアップする。当時の入稿用BOMは23品種、CPLは81点。[R53・R54の実装記録](Rev1-Grove-Pullups.md)・[BOM・CPL照合](Rev1-BOM-check.md)
- 信号線幅は0.25 mm、3V3配線は0.40 mm。GroveコネクタのGNDは0.50 mm幅のサーマルで本体GNDベタに接続した。CAN側と本体側の最小銅箔間隔は表5.899 mm、裏4.000 mm。[DFM](Rev1-DFM.md)
- DRC違反・未配線・回路図との不一致は各0件。ERCはエラー0件、警告579件。[DRC](Rev1-DRC.rpt)・[ERC](Rev1-ERC.rpt)・[現行の製造・部品手配](../Rev1-order-estimate.md)

## J8_IO1とMID_1V65の配線修正（2026-11-24）

修正前はJ8_IO1と差動アンプの基準電圧MID_1V65が、同じ層で約12 mm、銅箔縁間0.45 mmで並走していた。J8_IO1を引き直し、配線間の最短は2.250 mm、ビア・ランドを含む最短は2.075 mmになった。Grove GPIOとアナログ信号の40組で、同一層の銅箔縁間1 mm未満・角度差5°以内の並走は0か所。[測定結果](Rev1-DFM.md)
