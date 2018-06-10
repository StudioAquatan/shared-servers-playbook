# 工房のサーバ用playbook

## 使い方

1. ログイン用の秘密鍵を`id_rsa`としてリポジトリ直下へ配置する
2. 復号用パスワードを`.ansible-vault-pass`に記述し，リポジトリ直下へ配置する
3. playbookを実行

```bash
# 共用サーバのセットアップ
$ ansible-playbook share-playbook.yml
```

## Octopassの初回インストール

1. 新しくインストールするサーバのアドレスとログインユーザ名，ログインパスワードを記述する（**絶対にcommitしないこと**）

```yaml
share:
  hosts:
    { new host name }:
      ansible_host: { new server address }
      ansible_ssh_user: { your login username }
      ansible_ssh_pass: { your login pass }
```

2. ansible-playbookを実行する
3. ログインパスワードを消去し，鍵名に置き換える

```yaml
share:
  hosts:
    { new host name }:
      ansible_host: { new server address }
      ansible_ssh_user: deploy
      ansible_ssh_private_key_file: ./id_rsa
```

4. addしてcommitしてpush

# Author

pudding
