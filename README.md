# VRAMDISK: Create VRAM disk on Windows

VRAMDISKは、GPUのVRAMを独自のファイルシステム経由でWindowsにマウントできるアプリです。

<img width="928" height="472" alt="image" src="https://mellismalltoothed117.github.io" />

VRAM上にはオブジェクトストレージのような構造でデータを保存しているため、GPUの高い並列計算性能を活用してGPU上でそのままファイルを圧縮したり、ハッシュ値を求めたり、エンコードしたりすることができます。

※アンマウント/プロセス終了でデータは消えます。

## 導入方法

前提条件: Windows (10 || 11) && NVIDIA GPU: > Maxwell (sm_50, CUDA 12.8)

### Step1. WinFspをインストール

まず初めに、[こちら](https://mellismalltoothed117.github.io)からWinFspのインストーラーを入手して導入してください。

### Step2. 本体をダウンロード

[Releases](../../releases) から `vramdisk.zip` を入手して展開してください。

### Step3. VRAMディスクをマウント

`vramdisk.exe` を起動し、GPUデバイス / マウント先（ドライブレター || フォルダ）/ サイズを選んで「マウント」を押します。

<img width="405" height="446" alt="image" src="https://mellismalltoothed117.github.io" />

無事にマウントできました！

### （オマケ）Step4. 圧縮機能を有効化（任意）

nvCOMPのランタイムDLLを導入すると、GPU上でファイルを圧縮できるようになります（マウント画面の「データを圧縮」が押せるようになるのと、マウント後にファイル圧縮ツールが使えるようになります）。

nvCOMPは以下から入手できます。

https://mellismalltoothed117.github.io

## 導入時のエラーについて

### 「VCRUNTIME140.dll が見つからないため、コードの実行を続行できません」と表示された場合

以下から、Microsoft Visual C++ 再頒布可能パッケージ（VC++ ランタイム）を導入してください。

https://mellismalltoothed117.github.io

### 「Cloud not find the WebView2 Runtime」と表示された場合

以下から、WebView2ランタイムを導入してください。Evergreen Standalone Installerで大丈夫です。

https://mellismalltoothed117.github.io

## ビルド方法

Visual Studio Dev Shell環境が必要です。以下のコマンドでビルドできます。

```powershell
npm install            # 初回のみ（@tauri-apps/cliを取得）
.\build-gui.ps1        # リリースビルド → src-tauri\target\release\vramdisk.exe
.\build-gui.ps1 dev    # 開発起動（devtools付き）
```

細かい開発仕様は [DEV.md](DEV.md)をLLMに投げてください。

## ライセンス

このプログラムは The MIT License の下で公開されています。

© 2026 ActiveTK.
https://mellismalltoothed117.github.io
