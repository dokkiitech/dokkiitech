```text
██████╗  ██████╗ ██╗  ██╗██╗  ██╗██╗██╗████████╗███████╗ ██████╗██╗  ██╗
██╔══██╗██╔═══██╗██║ ██╔╝██║ ██╔╝██║██║╚══██╔══╝██╔════╝██╔════╝██║  ██║
██║  ██║██║   ██║█████╔╝ █████╔╝ ██║██║   ██║   █████╗  ██║     ███████║
██║  ██║██║   ██║██╔═██╗ ██╔═██╗ ██║██║   ██║   ██╔══╝  ██║     ██╔══██║
██████╔╝╚██████╔╝██║  ██╗██║  ██╗██║██║   ██║   ███████╗╚██████╗██║  ██║
╚═════╝  ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═╝╚═╝╚═╝   ╚═╝   ╚══════╝ ╚═════╝╚═╝  ╚═╝
```

```console
$ whoami
dokkiitech — インフラ / バックエンド寄りの個人開発者

$ cat profile.txt
AWS と Cloudflare を Terraform で全部コード管理して、
SaaS・業務ツール・ゲームサーバーまで自分で作って自分で運用してる。
「手で触った設定は、いつか必ず忘れる」が信条。

$ ls focus/
iac/  ci-cd/  serverless/  networking/  nextjs/  automation/
```

---

## 🏗️ Infrastructure

個人のインフラを 1 つの IaC リポジトリに集約して、PR ベースで運用してる。

| レイヤ | やってること |
|---|---|
| **IaC** | Terraform で AWS / Cloudflare を丸ごとコード管理。state は S3 バックエンド |
| **CI/CD** | GitHub Actions で PR 時に `terraform plan`（差分リソース一覧を 1 コメントに集約）→ master マージで `apply` |
| **認証** | シークレットレス運用。AWS は OIDC フェデレーション、Cloudflare トークンは SSM Parameter Store から取得 |
| **権限分離** | plan は ReadOnly ロール / apply は master push からしか assume できないロール |
| **可観測性** | apply の開始・結果を Slack にスレッド通知。失敗したらその場で気付ける |
| **コスト管理** | `default_tags` で全リソースに `Project` タグ → Cost Explorer でプロダクト別に分解 |
| **ネットワーク** | Cloudflare Zone / DNS / Tunnel、到達経路を Tailscale だけに絞った踏み台ホスト |
| **サーバー** | EC2 のオンデマンド起動・時間帯停止でコスト削減（Minecraft 統合版サーバー / セルフホスト Redmine） |
| **サーバーレス** | Lambda + EventBridge の定期ジョブ、DynamoDB の TTL で 24h で消える使い捨て検証メール |
| **メール** | Amazon SES（送信 identity + Easy DKIM、受信は S3 → Lambda） |
| **構成管理** | Ansible をロール分割し、`--check --diff` が changed=0 になることで収束を担保 |
| **ドキュメント** | 構成図は draw.io、シーケンス図は mermaid でリポジトリに同梱して差分を追えるように |

---

## 🧰 Tech Stack

### Languages
<p>
  <img src="https://skillicons.dev/icons?i=java,python,go,typescript,javascript,bash&theme=dark" height=48 />
</p>

### Frameworks
<p>
  <img src="https://skillicons.dev/icons?i=nextjs,react,nodejs,spring,tailwind&theme=dark" height=48 />
</p>

### Cloud / Infra
<p>
  <img src="https://skillicons.dev/icons?i=aws,cloudflare,terraform,ansible,docker,nginx,githubactions,grafana&theme=dark" height=48 />
</p>

### Data
<p>
  <img src="https://skillicons.dev/icons?i=postgres,mysql,redis,firebase,supabase&theme=dark" height=48 />
</p>

### Tooling / OS
<p>
  <img src="https://skillicons.dev/icons?i=git,github,neovim,idea,vscode,notion,linux,debian,ubuntu,apple&theme=dark" height=48 />
</p>

---

## 🔭 Now

- **チケット駆動開発** — セルフホスト Redmine ＋ 自作 MCP サーバー([redmine-mcp](https://github.com/dokkiitech/redmine-mcp))で、Claude Code から起票・ステータス更新・工数記録まで完結させてる
- **マルチアカウント IaC** — 一般社団法人 TSUNAGU のインフラを、別 org / 別 AWS アカウント / 別 Cloudflare アカウントで独立して IaC 管理
- **プロダクト開発** — Next.js (App Router) + TypeScript で SaaS・業務ツールを継続開発
- **業務自動化** — Google Calendar / Meet / SES を組み合わせた予約バックエンド、カレンダー同期、Discord / Slack 通知基盤
- **IoT ちょっと** — SwitchBot → Discord 通知、M5Stack、NFC まわり

---

## 📊 GitHub Stats

<p align="center">
  <a href="https://github.com/dokkiitech">
    <img height=170 src="https://githubrandmestats-git-main-dokkiitechs-projects.vercel.app/api?username=dokkiitech&bg_color=0d1117cc&title_color=58a6ff&text_color=c9d1d9&icon_color=58a6ff&show_icons=true&include_all_commits=true&count_private=true&hide_border=true&custom_title=GitHub%20Stats" />
  </a>
  <a href="https://github.com/dokkiitech">
    <img height=170 src="https://githubrandmestats-git-main-dokkiitechs-projects.vercel.app/api/top-langs/?username=dokkiitech&bg_color=0d1117cc&title_color=58a6ff&text_color=c9d1d9&hide=css,html,vue,scss,ejs&layout=compact&hide_border=true" />
  </a>
</p>
<p align="center">
  <a href="https://github.com/dokkiitech">
    <img height=170 src="https://github-readme-streak-stats.herokuapp.com/?user=dokkiitech&theme=tokyonight&hide_border=true" />
  </a>
  <a href="https://github.com/dokkiitech">
    <img height=170 src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=dokkiitech&theme=github_dark" />
  </a>
</p>

---

## 🔗 Links

| | |
|---|---|
| 🌐 Website | [dokkiitech.com](https://dokkiitech.com) |
| ✍️ Zenn | [zenn.dev/dokkiitech](https://zenn.dev/dokkiitech) |
| 🐙 GitHub | [@dokkiitech](https://github.com/dokkiitech) |

<sub>`$ exit` — 手で触らず、コードで直す。</sub>
