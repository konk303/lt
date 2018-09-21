## stackdriver
loggingの他に apm機能もある
gemを入れれば、あとはunicorn/nginxのログだけにfluentd

## DWH -> BigQuery
looker (BI)

## ハイブリッドクラウド
vpn already

## GAS
使い所があれば…
意外となさそう (google appsを上手に使う)

## cloudsqlへのmigration
1. mysqlの外部マスター設定できるようになった
1. gtidの使用がマスト
1. 5.7にもしたい… 5.6のslaveで5.7は可能？
1. cloud memory storeもmigration機能あり (gcs経由) -> lruでキャッシュにも使いたい
-> あとはmailも外に出せれば、self manage middlewaregroongaくらいに(stateful set化)

## cloud firestore
1. document型のnosql クライアントとsync
1. gcp側と統合されてる
1. datastoreとも統合

## Google Service Platform
istio統合・もうすぐアルファができる
skaffold CI/CDもGCPで
`data studio`
spinnaker automated canarie deploy
google cloud build

## cloud sql活用
チューニングやったほうが良い (innodb_bufferとかは設定済み)

## fastly
エッジ・LBとしてCDN使う (mercari) 後ろにマルチクラウド

## stackdriver
pagerduty

## bigquery
partition分ける (設定でfilter必須にできる)
sqs/pubsub等使ってデータimport stream化する (開始・終了確認は別jobに)
(rxもう一度調べておく)

## spinnaker
使いたい

## app maker
結構面白そう

# インフラ移行
1. mailをaspに移す (sendgrid or mailgun)
1. makanaiに持っていく・corp/owned media
1. cloud sql / memory store
1. groongaはstateful set
1. まずはstatから
1. cron spinnakerに持っていけないか <- scheduleを使うべき
