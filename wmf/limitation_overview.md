# 既知の問題と制限事項

初回使用時に PowerShell のショートカットが壊れている
------------------------------------------------------------

**解決策:** 次の操作のいずれかを実行します。

1.  PowerShell のショートカットを右クリックします。 [Windows PowerShell] を選択し、管理者特権以外のモードで起動します。
2.  PowerShell のショートカットを右クリックします。 [Windows PowerShell] を右クリックし、[管理者として実行] を選択して管理者特権モードで起動します。

上記の操作のいずれかを実行すると、PowerShell のショートカットが機能します。 これらの操作は、一度だけ実行する必要があります。


Windows 7 で PowerShell モジュールと DSC リソースにより ExecutionPolicy についてエラーがレポートされる
-------------------------------------------------------------------------------------
Windows 7 で PowerShell モジュールと DSC リソースを使用すると、ExecutionPolicy についてレポートされるエラーとなる場合があります。

**解決策:** 管理者特権の PowerShell セッション (管理者として実行) で、次のコマンドを実行して ExecutionPolicy を RemoteSigned に設定します。

```powershell
Set-ExecutionPolicy RemoteSigned
```

古いリモート Exchange のエンドポイントに接続するとクラッシュが発生する
------------------------------------------------------------

古い Exchange のエンドポイントは、新しいエンドポイントにリダイレクトします。 リダイレクト ロジックに含まれたバグにより、クラッシュが発生します。

**解決策:** 新しいエンドポイントに直接接続します。


Windows Server 2012 R2 に WMF 5.0 をインストールした後、ソフトウェア インベントリ ログ機能が誤って停止される
-------------------------------------------------------------------------------------------------------------

SIL を既に実行している Windows Server 2012 R2 に WMF 5.0 をインストールする場合、インストール後ソフトウェア インベントリ ログ機能が誤って停止されます。

**解決策:** インストール プロセスでソフトウェア インベントリ ログ機能が誤って停止されるため、WMF のインストール後に Start-SilLogging コマンドレットを 1 回実行します。

-LiteralPath と -Recurse を一緒に使用すると Get-ChildItem が機能しない
--------------------------------------------------------------------------

ディレクトリ名に無効なワイルドカードが含まれている場合、-LiteralPath と -Recurse を一緒に使用すると、Get-ChildItem によって
期待どおりの結果が生成されません。

**解決策:** 理想的ではありませんが、現在の対応策では、コマンドレットに依存するのではなく、スクリプトに再帰を実装します。
<!--HONumber=Mar16_HO2-->