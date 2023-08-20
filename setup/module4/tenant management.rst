
tenant設定
########

本手順ではWebGUIを使用してF5OSのtenant設定をする方法を紹介します。


1. tenantの構築
--------------

1-1.　テナントイメージのダウンロード
~~~~~~~~

\ `F5 downloads <https://my.f5.com/s/downloads>`__ から使用するテナントのイメージファイルをダウンロードします。

.. NOTE::
   利用するイメージによってぢ要可能なテナント数が異なります。
   詳細情報は\ `Overview of the BIG-IP tenant image types <https://support.f5.com/csp/article/K45191957>`__
   をご参照ください。


1-2.　テナントイメージのアップロード
~~~~~~~~

画面左側にあるメニューバーから ``TENANT MANAGEMENT >> Tenant Images`` を選択し、テナントイメージの管理画面を開いてください。

``Upload`` をクリックしアップロードするイメージファイルを選択します。

.. image:: ./media/tenant-image-upload.png
      :width: 400

1-3.　テナントの設定
~~~~~~~~

画面左側にあるメニューバーから ``TENANT MANAGEMENT >> Tenant Deployments`` を選択し、 ``Add`` をクリックしてください。

作成するテナント名、および使用するイメージファイル、およびテナントの管理インターフェースを設定します。

リソースプロビジョニング項目ではRecommended/Advancedを選択可能であり、Recommendedを選択する場合テナントに割り当てるメモリは自動的に決定されます。

テナントに割り当てるリソースを設定し、テナントの状態をConfigured/Provisioning/Deoloyedから選択可能です。

.. NOTE::
  テナントのstatusがConfigured/Provisioningedとなっている時はリソースサイズを変更可能ですが、Deployすると変更不可となります。
  リサイズが必要となった際にはstatusを上記どちらかの状態へ変更する必要があります。

.. image:: ./media/tenant-deploy.png
      :width: 250

デプロイが完了するとテナントのstatusが ``Running`` となり、Running Versionに稼働中のTMOSバージョンが表示されます。

.. image:: ./media/tenant-deployed.png
      :width: 500
