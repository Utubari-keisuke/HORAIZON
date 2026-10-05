# Null Geodesic (ASTER-NG-2021)

> 一般相対性理論に基づく光のヌル測地線シミュレーション、代理AIモデル推論、およびリアルタイム重力レンズ可視化システム

---

## 🌌 Overview

ブラックホール周辺の強重力場における光の軌道（ヌル測地線）を高精度に計算・可視化するプロジェクトです
「**物理的に正確な計算**」と「**リアルタイムなWeb可視化**」を分離し、厳密な数値積分データからPINNs（物理情報ニューラルネットワーク）などの代理モデルを構築することで、Web環境における低遅延かつ高精度な光線軌道描画を実現します[span_2](start_span)[span_2](end_span)。

---

## 🏛 Architecture

本システムは、責務に応じた4層アーキテクチャで構成されています
```text
[ View Layer ]    Three.js / WebGPU / GLSL
       ▲          リアルタイム重力レンズ描画・UI操作
       │
[ Control Layer ] 星槍中枢AI (API Gateway / Audit Engine)
       │          理論統合・物理整合性監査・動的解説生成
       ▼
[ Bridge Layer ]  AI Accelerator (PyTorch / PINNs / ONNX)
       │          測地線方程式の代理モデル高速推論
       ▼
[ Core Layer ]    Physics Engine (NumPy / SciPy / EinsteinPy)
                  Schwarzschild解 & Kerr解の厳密数値積分
```

## Features

- **厳密な物理数値積分 (Core Layer)**: Schwarzschild解およびKerr計量時空におけるヌル測地線方程式の常微分方程式（ODE）ソルバー。
- **物理情報ニューラルネットワーク (Bridge Layer)**: ヌル拘束条件 $g_{\mu\nu} \dot{x}^\mu \dot{x}^\nu = 0$ および保存則を損失関数に組み込んだ代理モデル。
- **脱ブラックボックス・物理監査 (Control Layer)**: AI推論のヌル拘束残差や保存則（エネルギー・角運動量）を常時監視し、信頼度スコアを算出。
- **リアルタイム光線追跡 (View Layer)**: WebGL / WebGPU カスタムシェーダーによる事象の地平面、光子球、アクレッションディスク（降着円盤）の重力レンズ効果描画。

## Repository Structure
```
├── core/                  # 物理エンジン & 教師データセット生成
│   ├── physics/           # 計量テンソル、クリストッフェル記号、測地線ソルバー
│   └── dataset/           # サンプリング・HDF5/Parquetエクスポート
├── bridge/                # AI代理モデル（PINNs学習・ONNXエクスポート）
├── control/               # 星槍中枢AI（API Gateway、物理監査、解説モジュール）
├── view/                  # フロントエンド（Three.js / WebGPU / シェーダー）
└── horaizon.html          # プロトタイプ描画用スタンドアロンHTML
```

## 👥 Contributors

- 空治 景祐
- 水村 佑
- 星宮 伊織
- Noel Lucien Beaumont
- Alain Charles Alessandro-Aldrovandi


SECOND ASTER PLOJECT(2021)

