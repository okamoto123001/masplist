# masplist
AppleへMAS配信する際のplistの設定項目について。
今回はelectron-builderを使用して、MAS向けのアプリをビルドした際の設定値である。
electron以外では必要ない設定値もある。

## com.apple.security.app-sandbox

Developerサイト

https://developer.apple.com/documentation/security/app_sandbox

MacOS内のシステムリソースやユーザーデータへのアクセスを制限する。
アプリに問題があった場合に行ってくれるそうだ。

## om.apple.security.cs.allow-jit

Developerサイト

https://developer.apple.com/documentation/bundleresources/entitlements/com_apple_security_cs_allow-jit

MAP_JITを使用してアプリが書き込み可能、実行可能なメモリを作成してよいかを設定できる。
JITは「Just In Time」の略。JITコンパイルは、従来のソフトウェアが実行前に完全にコンパイルされるのに対し、実行時にコンパイルする方式。
MAP_JITは何かは不明。

下記electronの公式サイトにはtrueに設定する必要がある、と記載されているのでtrueにしておこう。
electronに関係ない場合は必要ないかもしれない。
https://www.electronjs.org/ja/docs/latest/tutorial/code-signing


## com.apple.security.files.user-selected.read-only
## com.apple.security.files.user-selected.read-write

Developerサイト

https://developer.apple.com/documentation/bundleresources/entitlements/com_apple_security_files_user-selected_read-only
https://developer.apple.com/documentation/bundleresources/entitlements/com_apple_security_files_user-selected_read-write

ユーザーが選択・保存ダイアログで選択したファイルに対して、アプリが読み込み、書き込みアクセスができるかどうかを設定する。
read-onlyのあとにread-writeが記載されているので、read-onlyは必要ないのでは？

## com.apple.security.network.server
## com.apple.security.network.client

Developerサイト

https://developer.apple.com/documentation/bundleresources/entitlements/com_apple_security_network_server
https://developer.apple.com/documentation/bundleresources/entitlements/com_apple_security_network_client

アプリがincoming、もしくはoutgoingのネットワークコネクションを開くことができるか設定する。
incomingがserver、outgoingがclientになる。

# mapchild.plist

## com.apple.security.inherit

親のサンドボックスの設定を引き継ぐ。
electronを使用する場合は必須の設定。
