API Reference
=============

CoinsWeb3Manager
----------------

Resetting your CoinsWeb3Manager
`````````````

Invoking this method resets CoinsWeb3Manager in your environment.

.. code-block:: console

    CoinsWeb3Manager.getInstance().reset();

Go23WalletTokensManage
----------------

Adding a token
`````````````

This method adds a new crypto token.

.. code-block:: console

    Go23WalletTokensManage.getInstance().addToken(String token,callback CallBack);
   
Deleting a token
`````````````

This method deletes an existing crypto token.

.. code-block:: console

    Go23WalletTokensManage.getInstance().deleteToken(String token,callback CallBack);

Finding a token in the chain
`````````````

This method finds an existing token in a wallet's chain.

.. code-block:: console

    Go23WalletTokensManage.getInstance().findTokensFromChain(String link,String id,callback CallBack);  

Go23WalletChainManage
---------------------

Adding a chain
```````````````

This method adds a new active chain to a wallet.

.. code-block:: console

    Go23WalletChainManage.getInstance().addChain(String link,String id,callback CallBack);

Deleting a chain
`````````````````

This method deletes an existing chain from a wallet.

.. code-block:: console

    Go23WalletChainManage.getInstance().deleteChain(String link,String id,callback CallBack);

Switching the active chain
```````````````````````````````

This method switches a wallet's currently active chain.

.. code-block:: console

    Go23WalletChainManage.getInstance().switchChain(String link,String id,callback CallBack);

Fetching all chains
````````````````````

This method fetches all currently active chains for a wallet.

.. code-block:: console

    Go23WalletChainManage.getInstance().findAllChains(callback CallBack);

Go23WalletWeb3Manage
---------------------

Transferring funds
``````````````````

Invoke this methods to transfer funds from one wallet to another.

.. code-block:: console

    Go23WalletWeb3Manage.getInstance().transfer(String fromAddress,String toAddress, long value, long gas, long gasPrice,data,String,nonce int,callback CallBack);

Approving transfer
```````````````````

This method approves a funds transfer.

.. code-block:: console

    Go23WalletWeb3Manage.getInstance().approve(String address,String data,callback CallBack);

Fetching the balance
```````````````````````

This method fetches a wallet's current balance.

.. code-block:: console

    Go23WalletWeb3Manage.getInstance().balanceOf(String address,String chain,callback CallBack);

Go23WalletUIManage
------------------

Setting the PIN Code length
````````````````````````````

This method allows modifying the length of a PIN Code.

.. code-block:: console

    Go23WalletUIManage.getInstance().setPingCodeLength(int length);

Setting the tip view
`````````````````````

This method enables TipView that supports multiple APIs and is used to customize various UI elements, including the background, text, etc.

.. code-block:: console

    //TipView supports multiple APIs and helps custom ui including background and text, etc.
    //This is the extension of TipView in Go23WalletSdk that implements those APIs.
    Go23WalletUIManage.getInstance().setTipView(tipView TipView);
