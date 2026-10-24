# スマートホーム
スマートホーム関係知識

## Matter
スマートホーム用のメーカ共通規格。Alexa、Apple Home、Google Homeなど統合可
LAN上で通信できるのでネット障害下でもつよい

- Matter Controller
サーバの役割。Google Nest Hubなど

- Matter Server と Matter Client (用語)
一見ではサーバにクライアントが紐づくようにも見えるが、Matterの場合、Switchbot Hub2のようなデバイス側が情報を提供し、Controller側が受け取ることになりがちなので、末端のデバイスがServer、統括するControllerがClientとなる。感覚的にちょっと逆な感あるので注意。

- multiadmin (複数管理)
Matterは1つのControllerで制御しきるのではなく、複数のControllerで対等にデバイスを共同管理する考え方。1つのデバイスに対してAppleやらGoogleやらのスマートホームが各個紐づけできる
