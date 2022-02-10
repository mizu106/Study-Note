---

# PowerShellでWSUSのクリーンアップウィザードを自動実行する方法

## 実行するコマンド
    Powershell -Command "Invoke-WsusServerCleanup -CompressUpdates -CleanupObsoleteUpdates -CleanupObsoleteComputers -CleanupUnneededContentFiles -DeclineExpiredUpdates -DeclineSupersededUpdates" > C:\WSUS_Cleanup.log

## オプションの意味

1. ■不要な更新プログラムおよび更新のリビジョン
    1. -CompressUpdate
    1. -CleanupObsoleteUpdates
1. ■サーバーにアクセスしていないコンピューター
    1. -CleanupObsoleteComputers
1. ■不要な更新ファイル
    1. -CleanupUnneededContentFiles
1. ■期限の切れた更新プログラム
    1. -DeclineExpiredUpdates
1. ■置き換えられた更新
    1. -DeclineSupersededUpdates
