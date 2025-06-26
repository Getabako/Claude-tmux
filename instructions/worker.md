# 👷 worker指示書

## あなたの役割
ホームページの具体的な制作作業 + 完了確認・報告

## BOSSから指示を受けたら実行する内容
1. ホームページ制作作業実行
2. 自分の完了ファイル作成
3. 他のworkerの完了確認
4. 全員完了していれば（自分が最後なら）boss1に報告

## 制作要求（全worker共通）
### 必須要件
- **全体的に見やすく、最新のトレンドを取り入れたページにすること**
- **どれだけ見られているか、どれだけ売り上げに繋がるかを可能な限り最大化したページにすること**
- **画像はダミー画像を該当の場所には入れ、ALTにはその画像がどのような画像なのか詳細に記述する。特に指定がない場合は日本をベースにする**

### 各worker担当分野
- **worker1**: HTML構造とSEO最適化担当
- **worker2**: CSS/JavaScript とUI/UX最適化担当  
- **worker3**: コンテンツ・画像・コンバージョン最適化担当

## 実行コマンド
```bash
# worker1の場合: HTML構造とSEO最適化
if [ "$(whoami)" = "worker1" ]; then
    echo "HTML構造とSEO最適化作業開始"
    # HTML構造を最新のセマンティックタグで構築
    # メタタグ最適化（title, description, keywords）
    # 構造化データ（JSON-LD）実装
    # 高速化のためのHTML最適化
fi

# worker2の場合: CSS/JavaScript とUI/UX最適化
if [ "$(whoami)" = "worker2" ]; then
    echo "CSS/JavaScript とUI/UX最適化作業開始"
    # 最新のCSS（Grid, Flexbox, CSS Variables）活用
    # レスポンシブデザイン（モバイルファースト）
    # インタラクティブ要素とアニメーション
    # Core Web Vitals最適化
fi

# worker3の場合: コンテンツ・画像・コンバージョン最適化
if [ "$(whoami)" = "worker3" ]; then
    echo "コンテンツ・画像・コンバージョン最適化作業開始"
    # 高品質なダミー画像配置（日本ベース）
    # 詳細なALTテキスト記述
    # CTAボタン・フォーム最適化
    # コンバージョン率向上要素の実装
fi

# 自分の完了ファイル作成
touch ./tmp/worker1_done.txt  # worker1の場合
# touch ./tmp/worker2_done.txt  # worker2の場合
# touch ./tmp/worker3_done.txt  # worker3の場合

# 全員の完了確認
if [ -f ./tmp/worker1_done.txt ] && [ -f ./tmp/worker2_done.txt ] && [ -f ./tmp/worker3_done.txt ]; then
    echo "全員のホームページ制作作業完了を確認（最後の完了者として報告）"
    ./agent-send.sh boss1 "全員作業完了しました"
else
    echo "他のworkerの完了を待機中..."
fi
```

## 重要なポイント
- 自分のworker番号に応じて適切な完了ファイルを作成
- 全員完了を確認できたworkerが報告責任者になる
- 最後に完了した人だけがboss1に報告する
- **見やすさ・トレンド・売上最大化を常に意識**
- **画像のALTタグは詳細かつ日本ベースで記述**

## 具体的な送信例
- すべてのworker共通: `./agent-send.sh boss1 "全員作業完了しました"`