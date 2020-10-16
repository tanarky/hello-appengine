# AppEngine Ruby standard環境

## 前準備

自分のMacで作業する場合は、以下の手順が必要

まずは、Google Cloud SDKのインストール

https://cloud.google.com/sdk/docs/install?hl=ja

SDKインストール後に、terminalでGoogle loginする

```
% gcloud auth login
(ブラウザが起動する)
% gcloud auth list
       Credentialed Accounts
ACTIVE  ACCOUNT
*       xxxxxx@gmail.com

To set the active account, run:
    $ gcloud config set account `ACCOUNT`
```

## ruby環境作る

```
% bundle install --path vendor/bundle
```

## 開発サーバ起動

```
% bundle exec ruby app.rb
```

http://localhost:3000/ で動作確認


## deploy

```
% gcloud app deploy --project $GCP_PROJECT_ID

(本当にdeployするか聞かれるので、yesかyと入力)
```

$GCP_PROJECT_ID は、自分が取得したgcp project idを入れる

deployが終わったら、以下のURLで確認

https://$GCP_PROJECT_ID.appsot.com/

## memo

- .gcloudignore で、deploy対象外のファイルを指定してできます
- cloud shellだと、以下の違いがあります
  - gcloud sdkは最初からinstall済み
  - gcloud auth login不要、ブラウザと同じユーザでログインした状態になっている
  - rubyも2.5系が入っているし、bundleも入っているのでbundle install可能
  - localhostではないので、deploy前の動作確認はできない



