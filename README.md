# Mitsui Commodity Prediction Challenge – 個人プロジェクト

## コンペ概要
- [Kaggle: Mitsui Commodity Prediction Challenge](https://www.kaggle.com/competitions/mitsui-commodity-prediction-challenge)
- コモディティ（商品）の将来価格を予測するAIモデルの開発コンペ
- 各種市場データやマクロ経済指標等をもとに、予測精度を競う

## 🔄 開発フロー（全体像）

1. **課題理解・データ把握**  
   データセットの中身・関連情報やドメイン知識を整理

2. **EDA（探索的データ分析）**  
   可視化・欠損値・外れ値の確認と傾向分析

3. **特徴量エンジニアリング**  
   新しい特徴の作成や既存特徴の処理と選択。スクリプト化を推奨

4. **モデル設計・ベースライン構築**  
   AutoML や LightGBM 等によるベースライン性能の取得と比較

5. **実験管理・チューニング**  
   Weights & Biases や MLflow でパラメータやメトリクスを一元管理

6. **提出とフィードバックサイクル**  
   Kaggle API を利用した投稿の自動化（GitHub Actions + CI/CD 等）

7. **振り返りと最適化の継続**  
   実験ログ・可視化結果・方針書を元に“次のトライ”を設計

---

## 🧪 Colab での操作テンプレート

以下は、「Google Drive 上にクローンしたリポジトリ→Colabで編集→GitHub に push」するための標準運用テンプレートです 🎯

### ✅ セッション起動時（最初の Colab セルに貼ることを推奨）

```python
from google.colab import drive
drive.mount('/content/drive', force_remount=False)

# プロジェクトルートへの移動（必要に応じてパスを修正）
PROJECT = "/content/drive/MyDrive/【Kaggle】MITSUI&CO. Commodity Prediction Challenge/MITSUI-CO-Commodity-Prediction-Challenge"
%cd "$PROJECT"

# GitHub から最新を pull（初回は clone、2回目以降は pull のみ）
!git pull origin main

# 認証情報（PAT）を永続化：credential helper をセット（初回のみ）
!git config --global credential.helper store
```
### 📘 ノートブック作成と編集 

notebooks/ 以下にある .ipynb ファイル（例：01_baseline.ipynb）を Colab 上で開き、実行・編集します。 または「File → Save a copy in Drive」から複製して編集も可能です。 .ipynb は全て Drive に保存されるため、Colab セッション終了後も消えません。

### 📦 コミット & Push（作業後）

```bash
!git add notebooks/ src/ docs/
!git commit -m "Update EDA notebook"
!git push origin main
```
最初の git push の際に、GitHub アカウント名 と Personal Access Token（PAT） の入力が求められます。 .gitconfig に保存されれば、次回から認証は自動化されます。 
※ただし Drive 上に PAT が平文で保存されるため、非公開フォルダに置くことを強く推奨します。

## 利用ツール一覧
- **Google Colab**：EDA、前処理、モデル開発
- **Kaggle Notebook**：データ確認、ローカル提出用
- **ChatGPT / Gemini**：コード・アイデア生成＆ブラッシュアップ
- **GitHub + Copilot**：バージョン管理、自動補完＆CI/CD
- **MLflow / Weights & Biases (W&B)**：実験管理・パラメータ/結果記録
- **AutoMLツール（Kaggle, Vertex AI, AutoGluon, PyCaret等）**：ベースライン生成・効率化
- **Notion/Obsidian/Google Docs（任意）**：進捗・アイデア・学びのメモ

---

## ディレクトリ構成（予定）
```
mitsui-commodity-challenge/
│
├── README.md                # 本ファイル
├── notebooks/               # EDA・実験用ノートブック
├── src/                     # Pythonスクリプト（前処理・学習・推論）
├── input/                   # データ格納用（git管理対象外）
├── output/                  # 生成物（予測値、可視化結果等）
├── logs/                    # 実験ログ・パラメータ記録
├── docs/                    # 方針・設計メモ・WBS等
└── .gitignore               # 無視ファイル設定
```

---

## 今後のTODO・進め方
- [ ] 公式Starter Code/Notebookのクローン＆分析
- [ ] データセットの内容・前処理方法の把握
- [ ] EDA開始（notebooks/配下で実施・成果記録）
- [ ] ベースライン（AutoML＋自作モデル）構築
- [ ] 実験管理ツール（MLflow/W&B）の導入
- [ ] 開発フロー・仮説検証サイクルのアップデート

---

## メモ・記録方針
- 方針変更や仮説・気づきは随時READMEまたはdocs/配下に記録
- 重要な実験のパラメータ・結果もMLflow/W&Bとあわせて要点記録
- 失敗例・うまくいかなかったことも資産化

---

## 備考
- プライベートリポジトリで管理し、外部公開はKaggle規約・公式ルールを遵守
- プロジェクト進行にあたってChatGPT等の支援AIから得られたノウハウも積極記録

---

> **本READMEは随時アップデートし、開発の全過程・ナレッジの記録台帳とします。**

