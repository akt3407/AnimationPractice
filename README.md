# AnimationPractice

**Astro で Web アニメーションを練習し、その記録を載せるサイト**です。

## 技術スタック

| 種別                 | 採用                                     |
| -------------------- | ---------------------------------------- |
| フレームワーク       | Astro 6                                  |
| スタイル             | Tailwind CSS v4 (`@tailwindcss/vite`)    |
| CMS                  | microCMS (`microcms-js-sdk`)             |
| 言語                 | TypeScript（strict）                     |
| Lint / Format        | ESLint (Flat config) + Prettier          |
| その他               | `@astrojs/sitemap` / husky + lint-staged |
| パッケージマネージャ | pnpm                                     |

## ディレクトリ構成

```
src/
├── components/
│   ├── ui/          # 再利用可能なUI primitives (Card など)
│   └── layout/      # Header / Footer などレイアウト構成要素
├── images/          # Astro が最適化処理する画像
├── layouts/         # ページ全体のレイアウト
├── lib/             # microCMS クライアントなどのヘルパー
├── pages/           # ルーティング (Astro 必須)
├── section/         # ページを構成するセクション単位のコンポーネント
├── styles/          # global.css / fonts.css
└── types/           # 共有 TypeScript 型
```

### Path alias によるimport

`tsconfig.json` に以下のエイリアスを設定済み:

| Alias           | 解決先                                                 |
| --------------- | ------------------------------------------------------ |
| `@/*`           | `src/*` (catch-all)                                    |
| `@layouts/*`    | `src/layouts/*`                                        |
| `@components/*` | `src/components/*`                                     |
| `@ui/*`         | `src/components/ui/*`                                  |
| `@layout/*`     | `src/components/layout/*`                              |
| `@section/*`    | `src/section/*`                                        |
| `@lib/*`        | `src/lib/*`                                            |
| `@styles/*`     | `src/styles/*`                                         |
| `@images/*`     | `src/images/*`                                         |
| `~types/*`      | `src/types/*` (※`@types`はTSが予約済みのため`~`を使用) |

```astro
---
import Layout from '@layouts/Layout.astro';
import Card from '@ui/Card.astro';
import Header from '@layout/Header.astro';
import { client } from '@lib/microcms';
import type { NavItem } from '~types/site';
---
```

## セットアップ

```bash
pnpm install
```

microCMS を使うため、ルートに `.env` を用意する。

```env
MICROCMS_SERVICE_DOMAIN=xxxxx
MICROCMS_API_KEY=xxxxx
```

## コマンド

| Command             | 内容                              |
| ------------------- | --------------------------------- |
| `pnpm dev`          | 開発サーバ起動 (`localhost:4321`) |
| `pnpm build`        | `astro check` + 本番ビルド        |
| `pnpm preview`      | ビルド成果物のローカルプレビュー  |
| `pnpm lint`         | ESLint                            |
| `pnpm lint:fix`     | ESLint 自動修正                   |
| `pnpm format`       | Prettier 整形                     |
| `pnpm format:check` | Prettier 検証のみ                 |

## 拡張の追加

```bash
pnpm astro add mdx        # MDX サポート
pnpm astro add react      # React コンポーネントを島として使う
pnpm astro add vercel     # Vercel デプロイアダプタ
```

## 今後の予定

- [ ] 具体的なアニメーションテーマを実装
- [ ] ScrollTrigger / Flip など GSAP プラグインの練習を拡充

## 参考リンク

- [Astro Docs](https://docs.astro.build)
- [GSAP Docs](https://gsap.com/docs/v3/)
- [Tailwind CSS Docs](https://tailwindcss.com/docs)
