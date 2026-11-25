# Rev1　実装座標とBOMの照合

## 11月25日の回路図と部品表

JLCPCB実装は23品種70点。工場用BOMの全参照番号が実装座標（CPL）と一致し、70点のフットプリントをKiCadのネットリストと照合した。秋月の追加・交換抵抗は4種類24点で、すべて手はんだする。差動アンプの8組の直列、2チャネルの終端抵抗の並列、D7・D8の極性、CANの121 Ω直列終端を確認した。変更対象以外の既存端子は変更前と同じネットに接続されている。[手はんだ部品表](../../pcb/manufacturing/Hand_Assembly_BOM.csv)・[工場用BOM](../../pcb/manufacturing/JLCPCB-BOM.csv)・[ネットリスト](Rev1-netlist.xml)

ERCはエラー0件。警告618件の内訳は接続グリッド外496件、ライブラリ参照122件。基板・CPL・Gerberを更新し、工場BOM70点の参照番号・座標・面を照合した。裏面ステンシル158開口は全て該当実装パッドの中心と一致した。[ERC結果](Rev1-ERC.rpt)

[最新CPL](../../pcb/manufacturing/JLCPCB-CPL.csv)・[KiCad座標](../../pcb/manufacturing/back-pos.csv)・[現行DRC](Rev1-DRC.rpt)

## 11月24日の基板と実装座標

Rev1のGrove実装を含む調達BOMと入稿用BOMは、裏面実装81点・23品種で一致した。KiCadから出力した裏面座標と入稿用CPLはいずれも81行で、すべての参照番号を一度ずつ含む。座標、回転、実装面をKiCad基板と照合した。[入稿用BOM](https://github.com/fa-yoshinobu/RS422-485-Wave-Logger-HW/blob/85fb58b/pcb/manufacturing/JLCPCB-BOM.csv)・[入稿用CPL](https://github.com/fa-yoshinobu/RS422-485-Wave-Logger-HW/blob/85fb58b/pcb/manufacturing/JLCPCB-CPL.csv)・[KiCad裏面座標](https://github.com/fa-yoshinobu/RS422-485-Wave-Logger-HW/blob/85fb58b/pcb/manufacturing/back-pos.csv)

Groveの100 Ω直列抵抗R49～R52にはC22775を実装する。R53・R54はC23162を実装、J7・J8は表面に手はんだする。裏面のU8・C15・SW1・SW2も手はんだで、これら手はんだ6点は工場向けBOMとCPLの対象外。

| JLCPCBコード | 参照番号 | 1台当たり個数 |
|---|---|---:|
| C8963 | U2, U3 | 2 |
| C6186 | U5 | 1 |
| C8678 | D3, D6 | 2 |
| C81598 | D5 | 1 |
| C15127 | Q1 | 1 |
| C8545 | Q2 | 1 |
| C25803 | R27, R34 | 2 |
| C502564 | D1, D2 | 2 |
| C14663 | C1, C2, C3, C4, C5, C6, C25, C29, C30, C31 | 10 |
| C15850 | C12, C13, C28 | 3 |
| C12891 | C24 | 1 |
| C1588 | C16, C17, C19, C20, C21, C22, C23 | 7 |
| C25811 | R1, R2, R3, R4, R11, R12, R28, R29 | 8 |
| C4184 | R5, R6, R7, R8 | 4 |
| C25819 | R13, R14, R15, R16, R30, R31, R32, R33, R35 | 9 |
| C25804 | R9, R10, R23, R24, R25, R26, R37, R38, R45 | 9 |
| C23138 | R19, R20, R21 | 3 |
| C22787 | R39, R42, R46 | 3 |
| C23228 | R40, R41, R43, R44 | 4 |
| C22859 | R48 | 1 |
| C21190 | R36 | 1 |
| C22775 | R49, R50, R51, R52 | 4 |
| C23162 | R53, R54 | 2 |
| **計** | **23品種** | **81** |

配置座標はKiCadのmm単位・底面出力（Xの反転なし）。Gerberとドリルと同じ基準原点を使用する。

JLCPCB用CPLは裏面プレビューに合わせてD5を180°、D6を0°、Q1・Q2を270°、U2を90°、U3を0°に補正した。修正版の別見積でダイオードの極性、単独端子、ICの1番端子とランドの向きを確認した。
