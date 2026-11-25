# Wave Logger Rev.1 製造・部品手配

[README](../README.md)・[基板の設計と寸法](PCB-Rev1.md)・[製造性検証](verification/Rev1-DFM.md)

## 手はんだ部品の手配

[手はんだ部品表](../pcb/manufacturing/Hand_Assembly_BOM.csv)には、基板1枚分の数量、型番、販売コード、販売単位の入数を記載しています。マイコンU1と液晶J2は、手はんだしたソケットに取り付けます。本体の外部電源にはセンタープラスの安定化DC 12 V・1 Aアダプターを用意します。[対応アダプター M120100-A010JP](https://akizukidenshi.com/catalog/g/g117429/)

## 入稿ファイル

WeAct用ソケットは外周60穴。基板1枚あたりの工場実装は裏面23品種74点。microSD用R66～R69には既存の47 kΩ品 C25819を使い、カードと同じWeAct P3.5のVDD33に接続する。Gerber・BOM・CPLはこの3ファイルを組み合わせる。

手はんだ用の実装図には、Waveの裏面全体、精密抵抗16個の拡大図、表面の挿入部品を掲載した。[手はんだ実装図](../enclosure/drawings/Hand-Solder-Assembly-Rev1.pdf)・[現行GerberのJLCDFMレポート](verification/JLCDFM-2026-11-26.pdf)

| JLCPCBの指定欄 | ファイル |
|---|---|
| Gerber | [製造用Gerber ZIP](../pcb/manufacturing/RS422-485-Wave-Logger-Gerber.zip) |
| BOM | [JLCPCB実装部品表](../pcb/manufacturing/JLCPCB-BOM.csv) |
| CPL | [工場実装CPL](../pcb/manufacturing/JLCPCB-CPL.csv) |

100 × 100 mm、FR-4、2層、1.6 mm、1 oz、緑／白シルク、有鉛HASL。手はんだの秋月抵抗24点は工場BOM・CPL・裏面ステンシルの対象外。D7・D8は帯側が1番（K）。工場プレビューの照合には底面から見た配置を使う。[裏面配置図](PCB-back.png)・[照合結果](verification/Rev1-BOM-check.md)

再出力時は基板の作業コピーで、工場BOMに含まれない部品のパッドから B.Paste を外してプロットする。現行ZIPは工場実装74点・裏面ペースト166開口をBOM、CPL、基板のパッド中心と照合済み。JLCDFMが指摘したR67・R68のビア近接は、現行ZIPで修正した。DRC違反・未配線・回路図との不一致は各0件。microSDの実カード動作は試作機で確認する。[発注前レビュー](Pre_Order_Review.md)

## 実装向きの確認

2026年11月26日に、現行CPLの工場実装74点をJLCDFMの `Component Placements` で照合した。欠落・余分な部品は各0点。無極性の抵抗41点とセラミックコンデンサ21点は、全点のCPL回転軸が基板のランドと一致した。

端子台を上にした裏面プレビューで、向きがある12点を照合した。D1・D2の単独端子は右。カソードはD3が下、D5が右、D6が左、D7が下、D8が右。Q1・Q2のドレインは上、ゲートは左下。U2の1番は右下、U3の1番は左下、U5の放熱タブは左で、すべて基板と一致した。

### D7・D8の極性確認

JLCPCBの `Component Placements` で裏面を表示し、C19627026（BAT54X）の `−` 端子を基板のK表示とKiCadの1番ランドに照合した。端子台を上にして裏面から見たとき、**D7のカソードは下、D8のカソードは右**で、設計と一致した。入稿CPLの回転はD7が270°、D8が0°。[工場実装CPL](../pcb/manufacturing/JLCPCB-CPL.csv)

## 発注条件

基板5枚のうち2枚に裏面Economic実装。位置決め穴はJLCPCB追加。
