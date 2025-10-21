# この例を実行する前に、かならずGitHubのWebページ上でREADME.mdを編集し、コミットをしておいて下さい。
#
# ここではfetchをする前のgitの状態を確認しています。
# fetchをする前なので、リモートの状態がわからない状態です。
# そのため、本当はリモートでは変更が行われているのに
# "Your branch is up to date with 'origin/main'
# （あなたのブランチはサーバ上のorigin/mainと同じだよ）
# と出力されています。
$ git status 
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
$ git fetch # フェッチします。これでリモートの変更が origin/mainにタウンロードされます。
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/ishihara-su/hello_world
   ad59682..47b0cd7  main     -> origin/main
$
# fetch実行後にgit statusをしてみると、
# 今度は"Your branch is behind 'origin/main'...
# とサーバとの間で食い違いがあると報告されます。
$ git status
On branch main
Your branch is behind 'origin/main' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

nothing to commit, working tree clean
$ git branch # 念のため、今作業中のブランチを確認します。
* main
$ git merge origin/main # 今のローカルのブランチにorigin/mainをマージします。
Updating ad59682..47b0cd7
Fast-forward
 README.md | 2 ++
 1 file changed, 2 insertions(+)
$ git status # 再び状態確認…"Your branch is up to date"と表示されます。
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
$ cat README.md
# hello_world

これはテストです。

新しいブランチに書き込んでみました。

石原 進

サーバ上で編集したよ。
