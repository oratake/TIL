# Rust

## 開発の流れ

`cargo new` (新規ディレクトリ) か `cargo init` (今のディレクトリ)

```shell
$ cargo new hello-world
```
### クレート追加

Cargo.tomlに直で書き込み or `cargo add hogecrate`

## Tips


### クレートのuse

TypeScriptでいう `import React form 'React';` みたいな部分

```rust
use axum::{
    routing::get,
    Router // axumクレート直下の「構造体」
};
```
[cf. 構造体(struct)](https://doc.rust-jp.rs/rust-by-example-ja/custom_types/structs.html)

↓完全修飾パス
axum::routing::get
クレート::モジュール::モジュール内の関数(アイテム?)

### 戻り値のジェネリクス <()>

`fn main() -> anyhow::Result<()>` みたいなやつ
- () は空のユニット型
- Result型は `Result<成功時の型, 失敗時の型>`
要は戻り値voidみたいな話
「空という値が存在する」という考え方

### std::result anyhow::Result

`std::result::Result` はエラー型 E を自分で指定する必要があり面倒
`fn main() -> Result<(), Box<dyn std::error::Error>>`

対してanyhow::Result

`anyhow::Result<()>`

### 未使用変数を明示する _

変数名の先頭にアンダースコアで未使用の変数と明示できる。
_単体で書くと値を完全に無視できるので実行だけしたいものにつけるとよい。Result型を返す
```
let _unuse = hoge();
```

### デバッグ

ファイル名、行番号、変数名、そして値をまとめて標準エラー出力に
`dbg!()`
