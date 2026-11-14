# sso-portal

社内ポータルのログインページ（静的サイト）。認証は Supabase Auth を使用します。

## 公開前に必ず書き換える場所（index.html の CONFIG）

| 項目 | 内容 |
|---|---|
| `demoMode` | 本番は `false` |
| `supabaseUrl` | SupabaseのProject URL |
| `supabaseKey` | anon（publishable）キー。**service_role キーは絶対に入れない** |
| `usernameDomain` | ユーザー名ログイン用の仮ドメイン |
| `orgName` / `helpText` | 組織名・問い合わせ文 |

## 公開手順

1. このフォルダの中身をGitHubリポジトリ直下に置く（`index.html` `CNAME` `.nojekyll` `README.md`）
2. `CNAME` ファイルの `portal.YOURNAME.f5.si` を実際のホスト名に書き換える
3. Settings → Pages → Source を `main` / `(root)` にして保存
4. Custom domain にホスト名を入れて保存
5. DDNS Now でホスト名のCNAMEを `GitHubユーザー名.github.io` に向ける
6. DNSが反映されたら「Enforce HTTPS」をオンにする

## 注意

- 無料プランではリポジトリが公開になるため、秘密情報は一切置かない
- ログインの判定はSupabase側で行われる。ページを隠すだけでは保護にならない
