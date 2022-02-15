---

# JobCenter  
NECのジョブマネージャー

## manual  
[基本操作ガイド R12.10](https://jpn.nec.com/websam/jobcenter/download/manual/12_10/JB_BASIC.pdf)  
[JobCenter R12.8 基本操作ガイド](https://support.microfocus.com/kb/kmdoc.php?id=KM1302285&fileName=web0-2008.pdf)


## How To  

### 指定した時刻まで待つ  
[待ち合わせ部品を使い分けよう](https://jpn.nec.com/websam/jobcenter/blog/vol11.html)

### 前のJOBが成功した場合、次のJOBを実行する。  
+ 基本的な考え方。  
直前のJOBのリターンコードが判定に使用される。  
JOBのステータスはリターンコードを元に、単位JOBの設定で決まる。  
+ 前のJOBが直列処理の場合  
最後に実行されたJOBのリターンコードが判定に使用される。並列処理の中でも同じ考え方をする。  
+ 前のJOBが並列処理の場合  
並列の中で一番大きいリターンコードが判定に使用される。  
+ 前のJOBがジョブネットワークの場合  
ジョブネットワークの中で最後に発生したリターンコードが判定に使用される。  
並列、直列に対する考え方は、単位JOBの時と同じ。  


