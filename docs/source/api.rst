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
