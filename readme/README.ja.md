# SoftwareLogBook

## 言語
- 英語（デフォルト）
- [Deutsch](README.de.md)
- [Español](README.es.md)
- [Français](README.fr.md)
- [日本語](README.ja.md)

SoftwareLogBookは、YAMLフロントマター付きのMarkdownファイルを用いるソフトウェアシステムのログブックです。

## 目的と範囲
SoftwareLogBookは、ソフトウェアツール、そのデプロイメント、ライフサイクルイベントを、特別なツールなしで読んで確認できる形式で記録します。

ファイル + Markdown + Gitを使う理由:
- プレーンテキストは読みやすく、差分やレビューが容易です。
- Gitは履歴、追跡性、append-onlyの規律を提供します。
- 構造はツールが限られた環境でも利用できます。

想定される利用シナリオ:
- 内製または外部ベンダーのツールを小規模から中規模で管理する場合。
- リリース、インシデント、保守メモを一か所に監査可能な形で残したいチーム。
- リポジトリベースの軽量なログブックで十分な環境。

これは次のものではありません:
- CMDBではありません。
- チケットシステムではありません。
- 監視システムではありません。

## 中核概念（概要）
- Software: ツールとその責任範囲の文脈を記述するレコード。
- Deployment: 環境にインストールされたソフトウェアツールのインスタンス。
- Entry: append-onlyのイベント記録（例: リリース、インシデント、保守）。
- Global entry: すべてのツールに適用されるイベントまたはポリシー。
- Corrections: 修正対象のエントリを参照する専用のエントリ。

## リポジトリ構造
- `software/<softwareKey>/`: ツールごとのフォルダ。
- `software/<softwareKey>/software.md`: ソフトウェアレコード。
- `software/<softwareKey>/deployments/`: デプロイメントレコード。
- `software/<softwareKey>/entries/<YYYY>/`: 年ごとのツール別ログブックエントリ。
- `_global/entries/<YYYY>/`: 年ごとのグローバルログブックエントリ。
- `taxonomy/`: 共有の列挙値と参照タイプ。
- `templates/`: 新規レコードのテンプレート。

## 最小ワークフロー
1. `../templates/software.template.md`を使って新しいソフトウェアレコードを作成します。
2. `../templates/deployment.template.md`を使ってデプロイメントレコードを追加します。
3. `../templates/entry.template.md`を使ってエントリを追加します（リリース、インシデント、保守）。
4. 修正が必要な場合は、`type: correction`の新しいエントリを追加し、元のエントリを参照します。

## 参考資料
- `../SPEC.md`: 構造とルールの正本。
- `../CONTRIBUTING.md`: 命名、ユニーク性、append-onlyのガイド。
- `../GUARDRAILS.md`: 推奨される検証チェックと衛生ガイド。

## Viewerとツール（任意）
このリポジトリはツールなしでも完全に利用できます。ViewerやCLIツールを追加で作ることはできますが、標準の一部ではありません。

## ライセンス
MIT（`../LICENSE`を参照）

## Translation note
This text was translated by ChatGPT.
