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


