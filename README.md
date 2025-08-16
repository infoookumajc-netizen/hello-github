# hello-github
## 2025/08/15
今日はGitHub勉強会に参加した。
Gitとか３年以上触ってない。
今後開発やるならやっておくべきだ。

もう一度変更を加えてみるよ

pull をした上でもう一度だよ

## 2025/08/16
testブランチ上に「This branch is 3 commits behind main.」が出ていて
どのように解決すれば良いかわからず、ChatGPTに相談

新しくtest2ブランチを作成して作業した。
結果的には、ターミナルで fetch をすることで解決した。

1. VSCode 左上のメニュー → 「ターミナル」 → 「新しいターミナル」
2. ターミナルで作業ブランチにいるか確認：
`git branch`
* feature-branch のように * が付いているブランチが作業中

3. main の最新を取り込む：
`git fetch origin`
`git rebase origin/main`
origin/main はリモートの main ブランチ

コンフリクトが出たら VSCode 上で修正 → ステージ →
`git rebase --continue`

4. リベース完了後、リモートに送る：
`git push --force-with-lease`
リベース後は履歴が書き換わるため 強制プッシュが必要

これをやったらtest2では出なくなった。
fetch作業が大事ってこういうことか。

⚪︎fetch と pull の違い
fetch
リモートリポジトリ（GitHub）の最新情報を取得
ローカルの作業ブランチは変わらない。
リモートの状態だけが更新される。

pull
リモートリポジトリの最新情報を取得して、自分のブランチにマージする
ローカルブランチにリモートの変更を統合する（場合によってコンフリクトが起こる）

初心者はとりあえず fetch で確認。
必要ならrebase / merge でローカルに反映する作業をする