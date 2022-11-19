Installation
============

To install CoinsGO23 Wallet complete the following steps:

1. Download ``coins.center.aar`` and add it to ``libs``.

2. Run the following ``build. gradle`` script in your project. 

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

3. Run the following ``build. gradle`` script in your app module.

.. code-block:: console

   buildscript {
    repositories {
        flatDir {
            dirs 'libs'
        }
    }
 }

 apply plugin: 'realm-android'
 apply plugin: 'com.dicedmelon.gradle.jacoco-android'
 apply plugin: 'maven-publish'

 dependencies {
    implementation 'androidx.core:core-ktx:1.9.0'
    implementation 'androidx.appcompat:appcompat:1.5.1'
    implementation('com.fasterxml.jackson.core:jackson-core:2.9.0')

    implementation('com.fasterxml.jackson.core:jackson-databind:2.9.10.4')

    // Http client
    implementation 'com.squareup.okhttp3:okhttp:4.9.3'

    implementation('com.google.code.gson:gson:2.8.5')

    implementation 'com.google.android.material:material:1.6.1'

    implementation ('org.web3j:core:4.8.8')

    // Sugar
    implementation('androidx.constraintlayout:constraintlayout:2.1.4')

    // ReactiveX
    implementation('io.reactivex.rxjava2:rxjava:2.2.21')

    implementation("io.reactivex.rxjava2:rxandroid:2.1.1")

    // Keyboard visibility
    implementation('net.yslibrary.keyboardvisibilityevent:keyboardvisibilityevent:3.0.0-RC3')

    // WebKit - for WebView Dark Mode
    implementation('androidx.webkit:webkit:1.4.0')

    // Image Loader
    implementation('com.github.bumptech.glide:glide:4.13.2')

    implementation('com.github.bumptech.glide:compiler:4.13.2')

    implementation(group: 'com.google.guava', name: 'guava', version: '30.1.1-android')

    implementation('com.trustwallet:wallet-core:3.0.9')

    implementation('com.github.salomonbrys.kotson:kotson:2.5.0')

    implementation('com.github.mailchimp:mailchimp-sdk-android:1.0.0')

    implementation('androidx.preference:preference-ktx:1.2.0')

    implementation('androidx.work:work-runtime:2.7.1')
    implementation 'androidx.swiperefreshlayout:swiperefreshlayout:1.1.0'
    implementation 'com.google.android.flexbox:flexbox:3.0.0'
    
    //coins-center.aar 
    implementation (name:'coins-center', ext:'aar')

 }

4. Add the following code to proguard.rules.pro

.. code-block:: console

  -keep class wallet.core {*;}
  -keep class com.coins.app.** { *; }

 # For native methods, see http://proguard.sourceforge.net/manual/examples.html#native
 -keepclasseswithmembernames class * {
    native <methods>;
 }

  Keep setters in Views so that animations can still work.
 -keepclassmembers public class * extends android.view.View {
    void set*(***);
    *** get*();
 }

 # We want to keep methods in Activity that could be used in the XML attribute onClick.
 -keepclassmembers class * extends android.app.Activity {
    public void *(android.view.View);
 }

 # For enumeration classes, see http://proguard.sourceforge.net/manual/examples.html#enumerations
 -keepclassmembers enum * {
    public static **[] values();
    public static ** valueOf(java.lang.String);
 }

 -keepclassmembers class * implements android.os.Parcelable {
    public static final ** CREATOR;
 }

 -keepclassmembers class **.R$* {
    public static <fields>;
 }

 # Preserve annotated Javascript interface methods.
 -keepclassmembers class * {
    @android.webkit.JavascriptInterface <methods>;
 }

 # Understand the @Keep support annotation.
 -keep class androidx.annotation.Keep

 -keep class wallet.** {*;}

 -keep @androidx.annotation.Keep class * {*;}

 -keepclasseswithmembers class * {
    @androidx.annotation.Keep <methods>;
 }

 -keepclasseswithmembers class * {
    @androidx.annotation.Keep <fields>;
 }

 -keepclasseswithmembers class * {
    @androidx.annotation.Keep <init>(...);
 }

 -keep public class * extends android.app.Activity
 -keep public class * extends android.app.Application
 -keep public class * extends android.app.Service
 -keep public class * extends android.content.BroadcastReceiver
 -keep public class * extends android.content.ContentProvider
 -keep public class * extends android.app.backup.BackupAgentHelper
 -keep public class * extends android.preference.Preference
 -keep public class com.android.vending.licensing.ILicensingService
 -keep class javax.** { *; }
 -keep class org.web3j.** { *; }

5. Add the following code to the application

.. code-block:: console

     CoinsWeb3Manager.getInstance().build(getApplicationContext(), "clientId", "clientSecret");

6. Finally, add the following code to the location where theuser is redirected to the GameCenter:

.. code-block:: console

      CoinsWeb3Manager.getInstance().setUniqueId("uniqueId").setEmail("email").setPhone("phone").start();
