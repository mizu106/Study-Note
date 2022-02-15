---

# WSUSの基本

## WSUSの基礎知識  
[これから始めるWSUS 3.0入門（前編）](https://atmarkit.itmedia.co.jp/ait/articles/0708/16/news071.html)  
[これから始めるWSUS 3.0入門（後編）](https://atmarkit.itmedia.co.jp/ait/articles/0709/13/news125.html)  
[Q&A Windows Server Update Services（第6回）](https://atmarkit.itmedia.co.jp/fwin2k/operation/wsusqa06/wsusqa06_02.html)  

---

## クリーンアップ  
[WSUS と Configuration Manager SUP のメンテナンスに関する完全なガイド](https://docs.microsoft.com/ja-jp/troubleshoot/mem/configmgr/wsus-maintenance-guide)  
[WSUS で不要な更新プログラムのインストーラーを削除する](https://social.msdn.microsoft.com/Forums/ja-JP/8848a2f3-fb6d-46cc-8405-3c05d3fe0ced/wsus?forum=jpsccmwsus)  
[WSUS で定期的なクリーンアップ、ちゃんとやっていますか？](https://turningp.jp/server-client/windows/wsus-cleanup)  

### コマンドラインでクリーンアップ  
[WSUS 関連の Windows PowerShell コマンドレット (Invoke-WsusServerCleanup) について](https://kogelog.com/2014/01/05/20140105-01/)  

### クリーンアップ自動化スクリプト    
[【PowerShell】WSUSのクリーンアップを定期的に自動実行](https://www.livefree.jp/powershell_wsus_cleanup/)  
[【PowerShell】WSUSのクリーンアップを定期的に自動実行２](https://www.livefree.jp/powershell_wsus_cleanup2/)  
+ イベントログに通知を行う方法。  

### レプリカが同期に失敗する  
[レプリカ構成では サーバー クリーンアップ ウィザード にご注意ください ](https://social.msdn.microsoft.com/Forums/ja-JP/f05e2bae-7fd4-4eed-9ba6-b646308417d0/1252412503125221245927083251041239112399-12469125401249612540?forum=jpsccmwsus)  
[レプリカ WSUS サーバーの同期がタイムアウトで失敗する](https://blogs.iis.net/wincat/wsus)  
+ マスターからクリーンアップを行うと、レプリカの動機に失敗する事象が発生することの詳細。

### 自分なりの解釈  
+ 「-CompressUpdates」と「-CleanupObsoleteUpdates」で不要なパッチを指定する処理に時間がかかる。  
ここの処理でタイムアウトするため、マスターサーバーから実行するとレプリカが同期できなくなるトラブルが発生する。  
そこで、レプリカから先にコマンドラインで繰り返し実行し、不要なパッチの指定を終えてからマスターで同様に不要なパッチを指定して、マスター、レプリカともに不要なパッチの指定が終わってから、ファイル削除、コンピューター情報の削除などを行うとうまくいくらしい。  
+ 複数のレプリカは同時に実行しても問題なかった。
+ 「-CompressUpdates」と「-CleanupObsoleteUpdates」を実行するとWSUSサービスが停止する。
+ WSUSサービスと管理画面が実行できても、パッチ配信出来ないことがある。
+ 不要パッチの指定は長時間かかるが、残りの処理は１～２時間で終了した。
