
2.1. テナントのデプロイ
########

以下の手順でテナントをデプロイします。


2.1.1. テナントイメージのダウンロード
--------------
\ `F5 downloads <https://my.f5.com/s/downloads>`__ から使用するテナントのイメージファイルをダウンロードします。

.. NOTE::
   利用するイメージによって収容可能なテナント数が異なります。
   詳細情報は\ `Overview of the BIG-IP tenant image types <https://support.f5.com/csp/article/K45191957>`__
   をご参照ください。

.. list-table:: テナントイメージの種類
   :header-rows: 1

   * - BIG-IP テナントイメージ
     - 対応モジュール
     - ブートロケーション数
     - Use Case
   * - ALL-F5OS
     - rSeriesで対応している全モジュール
     - 2
     - マルチテナント、マルチモジュール、サービスチェイン
   * - T4-F5OS
     - rSeriesで対応している全モジュール
     - 2
     - 単一テナント、マルチモジュール
   * - T2-F5OS
     - LTM, DNS
     - 2
     - 大量のテナント利用時
   * - T1-F5OS
     - LTM, DNS(低負荷構成)
     - 1 
     - 大量のテナント利用時

2.1.2. テナントイメージのアップロード
--------------
画面左側にあるメニューバーから ``TENANT MANAGEMENT >> Tenant Images`` を選択し、テナントイメージの管理画面を開きます。

``Upload`` をクリックしアップロードするイメージファイルを選択します。

.. image:: ./media/tenant-image-upload.png
      :width: 400

2.1.3. テナントの設定
--------------
画面左側にあるメニューバーから ``TENANT MANAGEMENT >> Tenant Deployments`` を選択し、 ``Add`` をクリックします。

作成するテナント名、および使用するイメージファイル、およびテナントの管理インターフェースを設定します。

リソースプロビジョニング項目ではRecommended/Advancedを選択可能であり、Recommendedを選択する場合テナントに割り当てるメモリは自動的に決定されます。

テナントに割り当てるリソースを設定し、テナントの状態をConfigured/Provisioning/Deoloyedから選択可能です。

.. NOTE::
  Stateが *Deployed* になっている場合には、BIG-IPテナントを停止した場合でも自動で起動するようにF5OS-A側で制御するため、
  テナントを停止する場合には、StateをDeployedからProvisionedに変更する必要があります。

.. image:: ./media/tenant-deploy.png
      :width: 250

.. list-table:: テナント設定項目
   :header-rows: 1

   * - 設定項目
     - 説明
     - 設定可能値
     - 備考
   * - Name
     - テナント名
     - 任意
     - ・最大49文字

       ・利用可能な文字: 英数字 (小文字)およびハイフン (-)

       ・数字は1文字目に利用不可
   * - Type
     - テナント種別
     - BIG-IP
     - 現時点では“BIG-IP”のみ指定可能
   * - Image
     - テナントに適用するイメージ
     - (イメージを選択)
     - 
   * - IP Address
     - テナントの管理 (Management) IPアドレス
     - IPv4 or IPv6アドレス
     - 
   * - Prefix Length
     - Management IPのサブネットマスク長
     - 1-128
     - 
   * - Gateway
     - Management IPのデフォルトGW
     - IPv4 or IPv6アドレス
     - 
   * - VLANs
     - テナントに割り当てるVLAN
     - F5OSで作成したVLANを選択
     - VLANは複数指定可能
   * - Resource Provisioning
     - プロビジョニングの方法
     - Recommended/Advanced
     - 
   * - vCPUs
     - テナントに割り当てる仮想CPU数
     - 2, 4, 6, 8 … (選択)
     - ・選択された値のみ指定可能

       ・Resource Provisioningで“Advanced”設定時のみ、”1”を選択可

       ・奇数は指定不可
   * - Memory
     - テナントに割り当てるメモリ
     - vCPU数に依存
     - ・Resource Provisioningで“Advanced”設定時のみ指定可能

       ・最小メモリサイズ = (3.5 * 1024 * #ofvCPUs) + 512
   * - Virtual Disk Size
     - テナントに割り当てる仮想ディスク・サイズ (GB)
     - 22-700
     - デフォルト: 76
   * - State
     - テナントの状態
     - Configured/Provisioned/Deployed
     - ・Configured: テナント設定のみシステム上に存在

       ・Provisioned: ソフトウェアをインストールし、仮想ディスクを作成

       ・Deployed: リソース (CPU/Memory)を割り当て、テナントを起動
   * - Crypto/Compression Acceleration
     - 暗号化/圧縮のアクセラレーション
     - Enabled (デフォルト)/Disabled
     - 有効時は、暗号化/圧縮処理をハードウェアへオフロード
   * - Appliance Mode
     - アプライアンスモードの有効化/無効化
     - Enabled/Disabled (デフォルト)
     - 有効時は、テナントへのBashアクセスが無効化


デプロイが完了するとテナントのstatusが ``Running`` となり、Running Versionに稼働中のTMOSバージョンが表示されます。

.. image:: ./media/tenant-deployed.png
      :width: 500

