
F5OS 基本設定
########

本手順ではWebGUIを使用してF5OSの基本設定をする方法を紹介します。


1. Hostnameの設定
--------------

画面左側にあるメニューバーから ``SYSTEM SETTINGS >> General`` を選択し、一般設定画面を開いてください。

Hostnameを入力し、画面右下にある ``Save`` をクリックして保存してください。

.. NOTE::
   F5OSのSyslog設定で外部にログを配信する場合には、当該設定後にも送信元ホスト名は *appliance-1* として表示されます。

.. image:: ./media/host-name.png
      :width: 250

2. ライセンスの設定
--------------

画面左側のメニューバーから ``SYSTEM SETTINGS >> Licensing`` を選択し、ライセンス適用画面を開いてください。

ライセンスキーを入力し、

.. NOTE::
   rSeriesでは、F5OSに適用されたライセンスがテナントに継承されます。
   そのためライセンス管理はF5OS側での一括管理となります。

.. image:: ./media/license.png
      :width: 250

3. DNSサーバの設定
--------------

画面左側のメニューバーから ``SYSTEM SETTINGS >> DNS`` を選択し、DNS設定画面を開いてください。

DNS Lookup Serversの項目にて ``Add`` を選択し、DNSサーバのIP addressを入力し、

``Save & Close`` をクリックして設定を保存してください。


.. image:: ./media/dns-server.png
      :width: 250


4. 時刻設定
--------------

画面左側のメニューバーから ``SYSTEM SETTINGS >> Time Setings`` を選択し、時刻設定画面を開いてください。

時刻設定ではNTPサーバとタイムゾーンの設定ができます。

.. image:: ./media/time.png
      :width: 250

4-1. NTP Serverの設定
~~~~~~~~
NTP Serversの項目にて ``Add`` を選択し、NTPサーバのHostnameを入力し、

``Save & Close`` をクリックして設定を保存してください。

.. image:: ./media/time-server.png
      :width: 250


4-2. Time Zoneの設定 
~~~~~~~~
Time Zoneの項目にてドロップダウンリストから該当するタイムゾーンを選択してください。

.. image:: ./media/time-zone.png
      :width: 250


5. ログ設定
--------------

画面左側のメニューバーから ``SYSTEM SETTINGS >> Log Setings`` を選択し、ログ設定画面を開いてください。

ログ設定ではリモートログサーバとログの出力レベルの設定ができます。

.. image:: ./media/log-server.png
      :width: 250

5-1. 外部ログサーバの設定　
~~~~~~~~
外部のログサーバへログを転送する場合には、Remote Log Serversの項目にて ``Add`` を選択し、

転送先のIP address、Portを入力してください。

``Save & Close`` をクリックして設定を保存してください。

.. image:: ./media/r-log-server.png
      :width: 250

5-2. ログ出力レベルの設定
~~~~~~~~
Software Component Log Levels項目にてドロップダウンリストから各コンポーネントのログ出力レベルを選択してください。

変更完了しましたら、 ``Save`` をクリックして設定を保存してください。

5-3. ログ確認
~~~~~~~~
出力されたログファイルは ``SYSTEM SETTINGS >> File Utilities`` から確認可能です。

Base Directory項目にてドロップダウンリストから ``log/system`` を選択し、

確認したいログファイルをエクスポートしてください。

.. image:: ./media/log-file.png
      :width: 250

6. SNMP設定
--------------
SNMPリクエストを受けるけるためには接続許可リストへの追加、およびSNMP設定が必要です。

6-1. 許可リストへの追加設定　
~~~~~~~~
画面左側のメニューバーから ``SYSTEM SETTINGS >> Allow List`` を選択し、許可リスト設定画面を開いてください。

``Add`` をクリックして追加画面へ遷移し、SNMPマネージャーのIP address および接続予定Port(161 SNMP)を設定してください。

``Save & Close`` をクリックして設定を保存してください。

.. image:: ./media/snmp-allow-list.png
      :width: 250

6-2. SNMPの設定
~~~~~~~~
画面左側のメニューバーから ``SYSTEM SETTINGS >> SNMP Configuration`` を選択し、SNMP設定画面を開いてください。

``Add`` をクリックし、使用予定のSNMPバージョンに応じてCommunity、Userを追加してください。

変更完了しましたら、 ``Save & Close`` をクリックして設定を保存してください。

.. image:: ./media/snmp.png
      :width: 250
