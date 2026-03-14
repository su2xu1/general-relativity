# general-relativity

アインシュタイン方程式を出発点として、一般相対性理論をおとに重力波を導出するノートです。  
数式は 日本語・英語の両言語で公開しています。
[＊製作過程をblogに記載しました](http://step2.cocolog-nifty.com/step2/)

## 概要

一般相対性理論の教科書（Landau & Lifshitz『場の古典論』）をベースに、計量テンソルの摂動論から出発して **重力波** を導出する過程を書いてみました。  
単なる結果の羅列ではなく、途中の計算を省略せず追跡できることを目指しています。

## ドキュメント

| 言語 | リンク |
|------|--------|
| 日本語 | [docs/ja/](docs/ja/index.md) |
| English | [docs/en/](docs/en/index.md) |

## 扱うトピック

- 弱重力場近似と計量の摂動 $g_{ik} = g_{ik}^{(0)} + h_{ik}$
- 微小座標変換とゲージ自由度（ゲージ固定条件 $\partial_k \phi^k_i = 0$）
- リッチテンソル・リーマン曲率テンソルの線形近似
- アインシュタイン方程式の波動方程式への帰着


## リポジトリ構成

```
general-relativity/
├── README.md
├── docs/
│   ├── _config.yml        # Jekyll 設定（kramdown + MathJax）
│   ├── en/
│   │   └── index.md       # English version
│   └── ja/
│       └── index.md       # 日本語版
└── draft/
    └── gravitational-wave.md  # 執筆中の草稿
```

## ローカルでの閲覧

[Jekyll](https://jekyllrb.com/) を使ってローカルでサイトを確認できます。

```bash
cd docs
bundle exec jekyll serve
```

ブラウザで `http://localhost:4000` を開いてください。  
数式は [MathJax 3](https://www.mathjax.org/) によってレンダリングされます。

## 参考文献

- L.D. Landau, E.M. Lifshitz, *The Classical Theory of Fields* (Course of Theoretical Physics, Vol. 2) 『場の古典論』（東京図書）

