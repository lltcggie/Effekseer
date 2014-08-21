Effekseer
=========
本ソフトウェア及びランタイムはオープンソースにて開発しているヴィジュアルエフェクト編集ツール・再生用ランタイムです。
主にゲームに組み込み使用しており、パーティクル等ヴィジュアルエフェクトをプログラマでなくデザイナが担当できるようにすること想定しています。

**Version 0.610**
* ランタイム：D3DX及びDirectXTexを不必要になるよう変更

# ビルド方法(Windows)
1. [CMake](http://www.cmake.org/)をインストール
2. PATHにcmake.exeがあるディレクトリを追加
3. VSの開発者コマンド プロンプトを開く
4. Effekseerのディレクトリへ移動
5. 「setenv.bat」を編集してDirectX SDKのパスを設定
6. 「VisualStudio_Library.bat」を実行

* 「VisualStudio_Library.bat」のCPUCountをPCのCPUに合わせて変更すればビルドが早くなる可能性がある
* x64のビルドは無効になっているが、「VisualStudio_Library.bat」のPlatformMaxを0から1に変更すればビルドできるかもしれない(未確認)

# RoadMap

**Version 0.7(予定)**
* ターゲットに向かうようなエフェクト（ターゲット位置からの相対位置x,y,z,終点速度）
* 対象指定 重力　風　引力　ゴール

# Todo
プルリクエストお待ちしております。

**小規模な追加・変更**
* ドキュメントの改良
* 文言の改良
* 各種アイコンの追加
* サンプルの追加
* Windows、Linux以外のテストの構築
* 高速化

**中規模な追加・変更**
* Effectのパラメーターの動的な変更
* ショートカットの見直し
* 自動カリング
* モデル出力プラグイン(Blender等)
* 生成時間のランダム(現在の設計で実装可能なのか要検証)
* コード整備

**大規模な追加・変更**
* ツールのGUIライブラリの変更
* ツールのマルチプラットフォーム化

# 既存の不具合
* ステート復帰が不完全
* ウインドウ位置の初期化でウインドウ位置が正しく初期化されない

