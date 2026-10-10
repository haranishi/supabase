# 日本語版（Japanese edition）

This folder is the home of the Japanese edition of the Supabase docs and Studio. It lives in a fork, has not been proposed upstream, and has no translated pages yet. English is the source of truth.

訳文はまだ 0 本で、置き場所と決まりだけを先に作った。

## 本家には翻訳の仕組みがないので、訳は `i18n/ja/` に置く

docs・Studio・www・lite-studio のどの `package.json` にも、next-intl や i18next のような i18n ライブラリはない。ページの言語も固定で、`apps/studio/routes/__root.tsx` と `apps/docs/app/layout.tsx` に `<html lang="en">` が書かれている。ドキュメントの翻訳を求めた [supabase/supabase#22687](https://github.com/supabase/supabase/issues/22687) は、2025年1月に動きがないとして Discussions へ移された。そこで、アプリのコードに触れない `i18n/ja/` に訳を置く。

README の日本語版は `i18n/README.jp.md` に既にあるので、ここでは扱わない。

## 今すぐ訳せるのはドキュメントだけで、Studio は方式の決定が先

英語版のドキュメントは MDX で 881 本ある（guides 591、troubleshooting 229、`_partials` 61）。MDX のまま訳せるので、すぐに始められる。

Studio の画面文字列は、`New project` や `Create a new project` のように各コンポーネントへ直接書かれていて、文字列をまとめたカタログがない。訳す前に、文字列の取り出し方を決める必要がある。

## 訳は原文と同じ相対パスに置く

- `apps/docs/content/guides/auth.mdx` の訳は `i18n/ja/docs/guides/auth.mdx` に置く。troubleshooting と `_partials` も、`content/` 以下の相対パスをそのまま写す
- Studio の訳は `i18n/ja/studio/` に置く。形式は未定
- 既存の README の日本語版は `jp` という名前だが、ここでは ISO 639-1 の `ja` を使う

## 最初の対象は getting-started の 42 本

新しく使い始める人が最初に開く章なので、ここから訳す。その後の順番は決めていない。

## コードと識別子は訳さず、訳語は用語集に合わせる

- コード、コマンド、設定キー、URL は訳さない。フロントマターの `id` と、`<ContentListings id="..." />` のような MDX コンポーネントの名前と属性もそのままにする。`title`・`subtitle`・`description` は訳す
- 訳語は [GLOSSARY.md](./GLOSSARY.md) に合わせる。載っていない語は、訳す前に追記する
- 原文から訳す。他のサイトにある日本語訳を写さない
- 自信のない箇所は英語のまま残し、`TODO(ja)` と書く
- 訳文は、リポジトリの LICENSE（Apache-2.0）に従う

## 表示方法・Studio の方式・訳の鮮度管理は未定

- ドキュメントの表示方法。`/docs/ja/` のような別パスにするか、別サイトにするか。アプリが `apps/docs/content/` をどう走査するかは確認していない。ビルドに影響しないよう、アプリの外の `i18n/` に置いた
- Studio の翻訳方式。ライブラリ、文字列の取り出し方、言語の選び方
- 原文が更新されたとき、訳が古くなったことをどう見つけるか
- 本家に提案するか、提案するならどの形か
- 質問と議論の受け口

最終更新: 2026-10-10
