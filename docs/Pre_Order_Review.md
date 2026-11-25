# RS422-485 Wave Logger 発注前レビュー

Rev.1の初回発注前レビュー。2026年11月26日にmicroSDプルアップ追加後の製造データでJLCDFMを実行した。

## 発注前レビューの結果

- **microSDのCMD・DAT0～2用の外付け47 kΩは反映済み。** R66～R69はWeAct P3.5のVDD33へ接続した。DAT3はWeAct V1.1上のR11（100 kΩ）を使う。[製造・部品手配](Rev1-order-estimate.md)
- **現行GerberはJLCDFMで解析済み。** SMT DFMの危険・警告は各0件。工場実装74点の配置と向きは照合済み。R67・R68のビアと近接シルク、J1端子名の修正も反映した。[最終解析PDF](verification/JLCDFM-2026-11-26.pdf)・[修正内容](verification/Rev1-DFM.md)

## 確認済みの範囲

- ベタ再充填後のDRC違反・未配線・回路図との接続不一致は各0件。
- ERCはエラー0件、警告618件。内訳は接続点のグリッド外496件とライブラリ参照122件。[ERC記録](verification/Rev1-ERC.rpt)
- 工場実装BOM・CPL・JLCDFM裏面一覧は74点が一致。CPLの中心と裏面ペースト166開口をKiCadと照合した。[現行の入稿ファイル](Rev1-order-estimate.md#入稿ファイル)
- シルクと開口する加工穴の最小間隔は表0.515 mm、裏0.299 mm。[製造性解析](verification/Rev1-DFM.md)

## 試作機での確認

- WeActモジュール上のP5は偶数側4ピンだけにL型ヘッダーを取り付け、SWD書き込みを確認する。2番GND、4番SWCLK、6番SWDIO、8番VTref。奇数側の3番（PA10、UART RX）はU3出力と直結している。リセット接続が必要になった場合は7番（NRST）を追加する。[手はんだ部品表](../pcb/manufacturing/Hand_Assembly_BOM.csv)・[SWDの接続手順](https://github.com/fa-yoshinobu/RS422-485-Wave-Logger-FW/blob/main/docs/validation/Bringup.md)
- WeActソケットの手はんだ時は、R66横の最小ランド間隔0.239 mmでこて先とはんだの広がりを確認する。microSDは実カードで認識、再初期化、連続記録を確認する。[製造性解析](verification/Rev1-DFM.md)

[Serial Tap Loggerの発注前レビュー](https://github.com/fa-yoshinobu/Serial-Tap-Logger-HW/blob/main/docs/Pre_Order_Review.md)
