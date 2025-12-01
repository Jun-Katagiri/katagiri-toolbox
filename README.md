# Turborepo starter

This Turborepo starter is maintained by the Turborepo core team.

## Using this example

Run the following command:

```sh
npx create-turbo@latest
```

## What's inside?

This Turborepo includes the following packages/apps:

### Apps and Packages

- `docs`: a [Next.js](https://nextjs.org/) app
- `web`: another [Next.js](https://nextjs.org/) app
- `@repo/ui`: a stub React component library shared by both `web` and `docs` applications
- `@repo/eslint-config`: `eslint` configurations (includes `eslint-config-next` and `eslint-config-prettier`)
- `@repo/typescript-config`: `tsconfig.json`s used throughout the monorepo

Each package/app is 100% [TypeScript](https://www.typescriptlang.org/).

### Utilities

This Turborepo has some additional tools already setup for you:

- [TypeScript](https://www.typescriptlang.org/) for static type checking
- [ESLint](https://eslint.org/) for code linting
- [Prettier](https://prettier.io) for code formatting

### Build

To build all apps and packages, run the following command:

```
cd my-turborepo

# With [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation) installed (recommended)
turbo build

# Without [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation), use your package manager
npx turbo build
yarn dlx turbo build
pnpm exec turbo build
```

You can build a specific package by using a [filter](https://turborepo.com/docs/crafting-your-repository/running-tasks#using-filters):

```
# With [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation) installed (recommended)
turbo build --filter=docs

# Without [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation), use your package manager
npx turbo build --filter=docs
yarn exec turbo build --filter=docs
pnpm exec turbo build --filter=docs
```

### Develop

To develop all apps and packages, run the following command:

```
cd my-turborepo

# With [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation) installed (recommended)
turbo dev

# Without [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation), use your package manager
npx turbo dev
yarn exec turbo dev
pnpm exec turbo dev
```

You can develop a specific package by using a [filter](https://turborepo.com/docs/crafting-your-repository/running-tasks#using-filters):

```
# With [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation) installed (recommended)
turbo dev --filter=web

# Without [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation), use your package manager
npx turbo dev --filter=web
yarn exec turbo dev --filter=web
pnpm exec turbo dev --filter=web
```

### Remote Caching

> [!TIP]
> Vercel Remote Cache is free for all plans. Get started today at [vercel.com](https://vercel.com/signup?/signup?utm_source=remote-cache-sdk&utm_campaign=free_remote_cache).

Turborepo can use a technique known as [Remote Caching](https://turborepo.com/docs/core-concepts/remote-caching) to share cache artifacts across machines, enabling you to share build caches with your team and CI/CD pipelines.

By default, Turborepo will cache locally. To enable Remote Caching you will need an account with Vercel. If you don't have an account you can [create one](https://vercel.com/signup?utm_source=turborepo-examples), then enter the following commands:

```
cd my-turborepo

# With [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation) installed (recommended)
turbo login

# Without [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation), use your package manager
npx turbo login
yarn exec turbo login
pnpm exec turbo login
```

This will authenticate the Turborepo CLI with your [Vercel account](https://vercel.com/docs/concepts/personal-accounts/overview).

Next, you can link your Turborepo to your Remote Cache by running the following command from the root of your Turborepo:

```
# With [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation) installed (recommended)
turbo link

# Without [global `turbo`](https://turborepo.com/docs/getting-started/installation#global-installation), use your package manager
npx turbo link
yarn exec turbo link
pnpm exec turbo link
```

## Useful Links

Learn more about the power of Turborepo:

- [Tasks](https://turborepo.com/docs/crafting-your-repository/running-tasks)
- [Caching](https://turborepo.com/docs/crafting-your-repository/caching)
- [Remote Caching](https://turborepo.com/docs/core-concepts/remote-caching)
- [Filtering](https://turborepo.com/docs/crafting-your-repository/running-tasks#using-filters)
- [Configuration Options](https://turborepo.com/docs/reference/configuration)
- [CLI Usage](https://turborepo.com/docs/reference/command-line-reference)
=======
# Toolbox Monorepo

複数の小規模ツールをまとめて管理するための **Next.js + Turborepo** ベースのモノレポです。  
UI は共通の shadcn/ui コンポーネント、DB は Drizzle ORM + Turso を共通利用します。
All small tools that may be useful for translators live in this monorepo, katagiri-toolbox.
They share the common shadcn/ui components and DB.

---

## 📁 Repository Structure

```
.
├─ apps/
│   ├─ sequence-runner/   # 1行＝1ステップのシーケンス実行ツール
│   ├─ simon/             # 9パネル版 Simon Says（公開予定）
│   ├─ regex-editor/      # 正規表現パターン＆ロジックエディタ（予定）
│   ├─ IR-doc-checker/    # Compares a bilingual IR file (planned)
│   └─ (more tools...)
│
├─ packages/
│   ├─ ui/                # 共通UIコンポーネント（shadcn/ui）
│   ├─ db/                # Drizzle ORM schema & DB utils
│   ├─ utils/             # 共通ロジック
│   └─ types/             # 共通型定義
│
└─ docs/
    ├─ sequence_tool_spec.md
    ├─ regex_editor_spec.md
    └─ architecture.md
```

---

## 🧰 Goals

- 複数の Next.js ベースのツールを **1つのモノレポで統一管理**  
- UI / DB / ロジックを **共通パッケージ化** して再利用性を高める  
- 個人開発ツールの “実験場（Toolbox）“ として運用  
- 完成度の上がったものから順に公開  

---

## 🏗 Tech Stack

- **Next.js (App Router)**
- **Turborepo**
- **TypeScript**
- **shadcn/ui**
- **Tailwind CSS**
- **Drizzle ORM**
- **SQLite（開発） / Turso（本番）**

---

## 🚧 Work in Progress

最初の実装対象は **Sequence Runner**。  
仕様は [`docs/sequence_tool_spec.md`](docs/sequence_tool_spec.md) を参照。

予定されている追加ツール：
- Regex Editor（正規表現＋ルール管理ツール）
- 9パネル Simon Says

---

## 📜 License

MIT License (予定)

---

## ✨ Author

This repository is maintained as a personal development toolbox.  
Tool names and structure may change as features evolve.

