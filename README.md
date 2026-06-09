# AnimationPractice

**Astro（今後 Next.js も）で Web アニメーションを練習するためのプロジェクト集**です。
1 つのリポジトリに、土台となるテンプレート（`top`）と、テーマ別の練習プロジェクト（`Practice01`〜）を並べています。
各プロジェクトは**独立**しており（個別の `package.json` / lockfile / `node_modules`）、それぞれ単体で起動・ビルドできます。

> 📌 現状はすべて **Astro** 製です。**Next.js** での練習プロジェクトは今後追加予定です。

## 技術スタック

| 種別                 | 採用                                         |
| -------------------- | -------------------------------------------- |
| フレームワーク       | Astro 6 / Astro 5（今後 Next.js も追加予定） |
| スタイル             | Tailwind CSS v4 (`@tailwindcss/vite`)        |
| アニメーション       | GSAP（SplitText ほか）                       |
| 言語                 | TypeScript（strict）                         |
| Lint / Format        | ESLint (Flat config) + Prettier              |
| パッケージマネージャ | pnpm                                         |

## リポジトリ構成

```
AnimationPractice/
├── top/         # 再利用テンプレート（astro-template）— 練習プロジェクトの土台
├── Practice01/  # SplitText アニメーション練習（Astro + GSAP）
├── Practice02/  # 練習用（テーマ未定）
├── Practice03/  # 練習用（テーマ未定）
├── Practice04/  # 練習用（テーマ未定）
└── Practice05/  # 練習用（テーマ未定）
```

## プロジェクト一覧

| ディレクトリ                 | 内容                     | 主な技術              | README                           |
| ---------------------------- | ------------------------ | --------------------- | -------------------------------- |
| [`top`](./top)               | テンプレート（土台）     | Astro 6 / Tailwind 4  | [README](./top/README.md)        |
| [`Practice01`](./Practice01) | SplitText アニメーション | Astro 5 / GSAP        | [README](./Practice01/README.md) |
| [`Practice02`](./Practice02) | 練習用（テーマ未定）     | astro-template ベース | [README](./Practice02/README.md) |
| [`Practice03`](./Practice03) | 練習用（テーマ未定）     | astro-template ベース | [README](./Practice03/README.md) |
| [`Practice04`](./Practice04) | 練習用（テーマ未定）     | astro-template ベース | [README](./Practice04/README.md) |
| [`Practice05`](./Practice05) | 練習用（テーマ未定）     | astro-template ベース | [README](./Practice05/README.md) |

各プロジェクトの詳細（ディレクトリ構成・path alias・コマンドなど）は、それぞれの README を参照してください。

## セットアップ & 起動

ルートにまとめた依存はありません。**動かしたいプロジェクトのディレクトリに入って**操作します。

```bash
cd Practice01      # 起動したいプロジェクトへ移動
pnpm install       # 依存をインストール
pnpm dev           # 開発サーバ起動 → http://localhost:4321
```

### よく使うコマンド

| Command        | 内容                                                      |
| -------------- | --------------------------------------------------------- |
| `pnpm dev`     | 開発サーバ起動 (`localhost:4321`)                         |
| `pnpm build`   | 本番ビルド（`top`/`Practice02-05` は `astro check` 込み） |
| `pnpm preview` | ビルド成果物のローカルプレビュー                          |

> `top` および `Practice` では `pnpm lint` / `pnpm format` も利用できます。

## 新しい練習プロジェクトを追加する

土台テンプレート `top` を複製して始めます。

1. `top/` を `PracticeNN/` としてコピー
2. `package.json` の `name` を変更（例: `parallax-practice`）
3. `astro.config.mjs` の `site` を実際のドメインに変更
4. このルート README の「プロジェクト一覧」に 1 行追加

## 今後の予定

- [ ] **Next.js** での練習プロジェクトを追加
- [ ] 具体的なアニメーションテーマを実装
- [ ] ScrollTrigger / Flip など GSAP プラグインの練習を拡充

## 参考リンク

- [Astro Docs](https://docs.astro.build)
- [GSAP Docs](https://gsap.com/docs/v3/)
- [Tailwind CSS Docs](https://tailwindcss.com/docs)
