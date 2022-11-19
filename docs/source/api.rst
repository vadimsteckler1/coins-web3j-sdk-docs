API Reference
=============

CoinsWeb3Manager
----------------

Resetting your CoinsWeb3Manager
`````````````

.. code-block:: console

    CoinsWeb3Manager.getInstance().reset();

Go23WalletTokensManage
----------------

Adding a token
`````````````

.. code-block:: console

    Go23WalletTokensManage.getInstance().addToken(String token,callback CallBack);
   
Deleting a token
`````````````

.. code-block:: console

    Go23WalletTokensManage.getInstance().deleteToken(String token,callback CallBack);

Finding a token in the chain
`````````````

.. code-block:: console

    Go23WalletTokensManage.getInstance().findTokensFromChain(String link,String id,callback CallBack);  

Go23WalletChainManage
---------------------

Adding a chain
```````````````

.. code-block:: console

    Go23WalletChainManage.getInstance().addChain(String link,String id,callback CallBack);

Deleting a chain
`````````````````

.. code-block:: console

    Go23WalletChainManage.getInstance().deleteChain(String link,String id,callback CallBack);

Switching to a different chain
```````````````````````````````

.. code-block:: console

    Go23WalletChainManage.getInstance().switchChain(String link,String id,callback CallBack);

Fetching all chains
````````````````````

.. code-block:: console

    Go23WalletChainManage.getInstance().findAllChains(callback CallBack);

Go23WalletWeb3Manage
---------------------

Transferring funds
``````````````````

.. code-block:: console

    Go23WalletWeb3Manage.getInstance().transfer(String fromAddress,String toAddress, long value, long gas, long gasPrice,data,String,nonce int,callback CallBack);

Approving transfer
```````````````````

.. code-block:: console

    Go23WalletWeb3Manage.getInstance().approve(String address,String data,callback CallBack);

Fetching the balance
```````````````````````

.. code-block:: console

    Go23WalletWeb3Manage.getInstance().balanceOf(String address,String chain,callback CallBack);

Go23WalletUIManage
------------------

Setting the PIN Code length
````````````````````````````

.. code-block:: console

    Go23WalletUIManage.getInstance().setPingCodeLength(int length);

Setting the tip view
`````````````````````

.. code-block:: console

    //TipView will support too many apis to help to custom ui including backgroud and text, ext.
    //tipView needs to extends TipView whitch defining in Go23WalletSdk and implements these apis.
    Go23WalletUIManage.getInstance().setTipView(tipView TipView);
