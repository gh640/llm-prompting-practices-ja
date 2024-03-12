# (Japanese) LLM プロンプト作成のコツ

品質の高い参考資料をもとに LLM （大規模言語モデル）プロンプト作成のコツをかんたんにまとめました。

概要のみ記載しています。
詳細は各資料を参照してください。

プロンプトエンジニアリングのテクニックは公開されている資料である程度学習できます。
プロンプトエンジニアリングに関する（多くは情報弱者向けの）コース・商材・書籍の購入を検討されている方はぜひこれらの資料に先に目を通してみてください。

## コツ

## OpenAI: Prompt Engineering

[Prompt engineering - OpenAI API](https://platform.openai.com/docs/guides/prompt-engineering)

> ### 6 つの戦略
>
> 1. 明確な指示を書く
>     - 詳細を含める
>     - ペルソナを割り当てる
>     - 入力文の異なるパーツの間を明確に分ける
>     - タスクの完了に必要な手順を指定する
>     - 例を提示する
>     - 求める回答の長さを指定する
> 2. 参考テキストを提供する
>     - リファレンステキストを使って回答するように指示する
>     - リファレンステキストからの引用を添えて解凍するように指示する
> 3. 複雑なタスクをシンプルなサブタスクに分割する
>     - インテント分類を使ってユーザのクエリに関連性の高い指示を特定する
>     - 非常に長い会話を必要とする対話アプリケーションでは以前の対話を要約またはフィルタリングする
>     - 長い文書は断片的に要約してから再帰的に全体の要約を構築する
> 4. モデルに考える時間を与える
>     - 結論に飛びつく前にモデル自身に解決策を見つけるように指示する
>     - インナーモノローグや一連のクエリを使ってモデルの推論プロセスを隠す
>     - 前のパスで何か見落としがなかったかモデルに尋ねる
> 5. 外部のツールを使う
>     - embeddings ベースの検索を使って効率的な knowledge retrievel を行う
>     - code execution を使ってより精確な計算や外部 API 呼び出しをする
>     - モデルに特定の function へのアクセスを与える
> 6. システマティックに変更をテストする
>     - ゴールドスタンダードの答えを参考にモデルの出力を評価する

## Google: Prompt design strategies

[Prompt design strategies  |  Google AI for Developers](https://ai.google.dev/docs/prompt_best_practices)

> ### プロンプトデザイン戦略
>
> 1. 明確で具体的な指示を出す
>     - 実行すべきタスクを定義する
>     - すべての制約を指定する
>     - 回答のフォーマットを定義する
> 2. 数個の例を含める
>     - zero-shot と few-shot プロンプト
>     - 例の最適な数を見つける
>     - 例はアンチパターン（べからず集）ではなくパターンを示すために用いる
>     - 提示する例では一貫したフォーマットを使う
> 3. コンテキスト情報を加える
> 4. プリフィックスを加える
>     - 入力プリフィックス
>     - 出力プリフィックス
>     - 例プリフィックス
> 5. モデルに部分的な入力を与えて補完をさせる
> 6. プロンプトをシンプルなコンポーネントにブレークダウンする
>     - 指示をブレークダウンする
>     - プロンプトのチェーンを作る（前のプロンプトの出力を次のプロンプトの入力にする）
>     - レスポンスを集約する
> 7. さまざまなパラメータ値を試す
>     - 最大出力トークン
>     - Temperature （温度）
>     - Top-K
>     - Top-P
> 8. プロンプトの改善サイクル戦略
>     - 異なる言い回しを使う
>     - 類似のタスクに切り替える
>     - プロンプトコンテンツの順序を変える
> 9. フォールバックレスポンス
> 10. 避けるべきこと
>     - 事実に関する情報の生成をモデルに頼るのは避ける
>     - 数学とロジックの問題には注意をして使う

## Google: Prompt Engineering for Generative AI

[Prompt Engineering for Generative AI  |  Machine Learning  |  Google for Developers](https://developers.google.com/machine-learning/resources/prompt-eng)

> ### 生成 AI のためのプロンプトエンジニアリング
>
> #### プロンプト作成ベストプラクティス
>
> 1. どのコンテンツ・情報が最も重要なのかを明確に伝える。
> 2. プロンプトを構造化する: 役割の定義から始めて、コンテキストと入力のデータを与えて、指示を出す。
> 3. 具体的で多様な例を使って、モデルが焦点を絞って精確な結果を生成できるようにする。
> 4. 制約を与えてモデルの出力のスコープを制限する。そうすることで指示から逸脱して不正確な情報を出すのを避ける。
> 5. 複雑なタスクはブレークダウンしてシンプルなシーケンスの連なりにする。
> 6. モデルに自身の回答を生成する前に評価・チェックするよう指示する（「回答は 3 文以内にしてください。」「出力の簡潔さを 1 - 10 の尺度で評価してください。」「これが正しいと思いますか？」）。
>
> #### プロンプトのタイプ
>
> 1. ダイレクトプロンプティング（ zero-shot ）
> 2. 例を付けたプロンプティング（ one-shot / few-shot / multi-shot ）
> 3. CoT (Chain-of-Thought) プロンプティング
> 4. zero-shot CoT
> 5. プロンプトの改善サイクル戦略

## Anthropic: Prompt engineering

[Prompt engineering](https://docs.anthropic.com/claude/docs/prompt-engineering)

### プロンプト開発のライフサイクル

> 1. タスクと成功基準を定める
>     - 考えるべき主要な成功基準
>         - パフォーマンスと精度
>         - レイテンシー
>         - 価格
> 2. テストケースを作る
> 3. 暫定のプロンプトを作る
> 4. テストケースに対してプロンプトを試す
> 5. プロンプトを改良する
>     - ステップ 4 に戻って改良を繰り返す
> 6. 磨き上げたプロンプトをリリースする
>
> 最初に最も能力の高いモデルと長いプロンプトから始めて、望ましいアウトプット品質が得られるようになったら、レイテンシーとコスト削減のためにより小さいモデルや短いプロンプトを試すとよい。
>
> ### プロンプトエンジニアリングテクニック
>
> 1. 明確に直接伝える
> 2. 例を使う
> 3. モデルに役割を与える
> 4. XML タグを使う（ Claude 固有）
> 5. 大きなプロンプトを分ける
> 6. モデルに step-by-step で考えさせる
> 7. 期待する出力の先頭を指定する
> 8. 出力フォーマットを指定する
> 9. リライトをお願いする
> 10. コンテキストウィンドウが長いモデルはそれを活用する

## DAIR.AI: Prompt Engineering Guide

[Prompt Engineering Guide](https://www.promptingguide.ai/)

> ### LLM 設定
>
> | 名前 | 説明 |
> | --- | --- |
> | temperature | ランダムさの度合い。 temperature を上げるとランダムさが上がり、下げるとランダムさが下がる。 |
> | top P | nucleus sampling （核サンプリング）と呼ばれるサンプリングの方法。 top P を高くすると回答の多様性が上がる。 |
> | max length | 回答の最大長。単位はトークン数や文字数などモデルによって異なる。 |
> | stop sequence | 回答の生成を停止する文字列パターン。 |
> | frequency penalty | 特定のトークンの出現頻度のペナルティ。 |
> | presence penalty | あらゆるトークンの出現頻度のペナルティ。 |
>
> ### プロンプトの構成要素
>
> プロンプトの構成要素として次のものを考慮するとよい。
>
> | 名前 | 日本語 | 説明 |
> | --- | --- | --- |
> | instruction | 指示 | モデルに行ってもらいたいタスク |
> | context | コンテキスト | 外部情報や追加のコンテキスト |
> | input data | 入力データ | 回答を求める入力や質問 |
> | output indicator | 出力インジケータ | 出力のタイプやフォーマット |
>
> ### 全般的なヒント
>
> - シンプルに始めて改良を繰り返す
> - 命令調で要望を指示する
> - 具体的に直接的に
> - 不正確さを避ける
> - 「こうしないで」よりも「こうして」
>
> ### プロンプト作成テクニック
>
> - Zero-shot Prompting
> - Few-shot Prompting
> - CoT (Chain-of-Thought) Prompting
> - Self-Consistency
> - Generated Knowledge Prompting
> - Prompt Chaining
> - ToT (Tree of Thoughts)
> - RAG (Retrieval Augmented Generation)
> - ART (Automatic Reasoning and Tool-use)
> - APE (Automatic Prompt Engineer)
> - Active-Prompt
> - Directional Stimulus Prompting
> - PAL (Program-Aided Language Models)
> - ReAct Prompting
> - Reflexion
> - Multimodal CoT Prompting
> - GraphPrompt
>
> ### リスクと誤用
>
> - 敵対的プロンプティング（プロンプト攻撃）
>     - プロンプトインジェクション
>     - プロンプトリーキング
>     - ジェイルブレーキング（脱獄）
> - 真実性
> - バイアス

## 参考資料

### ガイドライン

- OpenAI: [Prompt engineering - OpenAI API](https://platform.openai.com/docs/guides/prompt-engineering)
- Google: [Prompt design strategies  |  Google AI for Developers](https://ai.google.dev/docs/prompt_best_practices)
- Google: [Prompt Engineering for Generative AI  |  Machine Learning  |  Google for Developers](https://developers.google.com/machine-learning/resources/prompt-eng)
- Anthropic: [Prompt engineering](https://docs.anthropic.com/claude/docs/prompt-engineering)
- DAIR.AI: [Prompt Engineering Guide](https://www.promptingguide.ai/)

### サンプル集

- OpenAI: [Examples - OpenAI API](https://platform.openai.com/examples)
- Google: [Example Prompts, Code and Integrations  |  Google AI for Developers](https://ai.google.dev/examples?keywords=prompt)
- Anthropic: [Prompt library](https://docs.anthropic.com/claude/prompt-library)

### リンク集

- OpenAI: [Related resources from around the web | OpenAI Cookbook](https://cookbook.openai.com/articles/related_resources)
- DAIR.AI: [Papers | Prompt Engineering Guide](https://www.promptingguide.ai/papers)
