Installation
============

To install CoinsGO23 Wallet complete the following steps:

1. Download ``coins.center.aar`` and add it to ``libs``.

2. Run the ``build. gradle`` script in your project. 

.. code-block:: console

   buildscript {
   
    repositories {
        google()
        mavenCentral()
        maven {
            url 'https://maven.google.com/'
            name 'Google'
        }
        maven {
            url 'https://developer.huawei.com/repo/'
        }
        flatDir {
            dirs 'libs'
        }
        maven {
            url "https://plugins.gradle.org/m2/"
        }
        maven { url 'https://jitpack.io' } // <-- New repository
        maven {
            url = uri("https://maven.pkg.github.com/trustwallet/wallet-core")
            credentials {
                //Generate a GitHub [Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) with `read:packages, read:user` permission
                username = 'Your GitHub Email'
                password = new String("Your GitHub Token".decodeBase64())
            }
        }
    }
    dependencies {
        classpath "com.dicedmelon.gradle:jacoco-android:0.1.5"
        classpath "io.realm:realm-gradle-plugin:10.8.0"
    }
  }

Creating recipes
----------------

To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']

