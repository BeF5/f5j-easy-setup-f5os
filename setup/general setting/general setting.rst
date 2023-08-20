
一般設定
####

設定方法
====
本手順ではWebGUIを使用して設定する方法を紹介します。

====

1.Hostnameの設定
~~~~~~~~

フロントパネルに触れ、画面を起動してください。

.. image:: ./media/hos tname.png
      :width: 250



2.ライセンスの設定
~~~~~~~~

画面左側のメニューバーから

.. image:: ./media/license.png
      :width: 250


.. NOTE::
   rSeriesでは、F5OSに適用されたライセンスがテナントにも継承されます。
   ライセンス管理はF5OS側で一括で管理することができます。

3.DNSサーバの設定
~~~~~~~~

下記コマンドにより内部通信に使用しているアドレスを確認できます。

.. image:: ./media/dns server.png
      :width: 250

ご使用予定の環境に合わせ、Out-of-band通信と重複しないようアドレス種別を変更してください。

`RFC` まで入力し、`Tab` キーを入力すると選択可能なアドレスの種類が表示できます。

.. code-block:: cmdin

   r10k-2# config
   r10k-2(config)# system network config network-range-type RFC
    Possible completions:  #デフォルトRFC6598
    RFC1918   System uses 10.[0-15]/12 as specified by RFC1918
    RFC6598   System uses 100.64/10 as specified by RFC6598
   r10k-2(config)# system network config network-range-type RFC1918
   r10k-2(config)# commit

4.設定した管理IPを利用してログインする手順
~~~~~~~~

``https://<管理IP address>`` によって設定した管理IPへGUI接続できるようになります。

.. image:: ./media/login.png
      :width: 250
