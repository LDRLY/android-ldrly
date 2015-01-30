LDRLY SDK for Android
=====
The LDRLY SDK for Android provides the required functionality to integrate the LDRLY ecosystem into an Android Studio or Android Eclipse project. Players can access LDRLY features through the provided UI, reducing development time when implementing social features and leaderboards.

Overview
-----
This SDK, distributed as a Android Library (JAR), communicates with the LDRLY API. The following functionality is provided by this package:

- Authenticate users
    - Authenticate through Facebook
    - Authenticate through Google+
- Post user scores
    - Posting Max Scores
    - Posting Min Scores
    - Posting Summation Scores
    - Posting Replace Scores
- Posting use analytics
- Posting game analytics
- Open the integrated LDRLY UI

Requirements:

- A LDRLY developer account
- LDRLY API credentials (provided in the developer page)
- Android Studio 1.1+ or Eclipse
- Supported Platform:
  - Android 4.0+

Getting Started
-----
Sign up for a developer account at <a href="https://developers.ldrly.com/">https://developers.ldrly.com/</a>

Setup
-----
1.  Download the JAR from the repository directly through GitHub or clone the repository.
2.  Add the SDK to your IDE of choice by copying the JAR and adding it to the libs folder in your application. e.g. /AndroidProject/app/libs/ldrly-android.jar
3.  Make sure the JAR is included as a Dependency.
    * In Android Studio open the Module Settings
    * Click on Dependencies
    * Add a file dependency for ldrly-android.jar
4. Import the LDRLY SDK in your Activity. e.g. MainActivity.java
<p><code>import com.ldrly.android.sdk.LDRLY;</code/></p>
5. Update your AndroidMainfest.xml with the required properties.
    1. Add the following required permissions:
    <pre>
        <code>
            <uses-permission android:name="android.permission.INTERNET" />
        </code/>
    </pre>
    2. Add the following required activity in-between your application element:
    <pre>
        <code>
            <activity
                android:name="com.ldrly.android.sdk.portal.WebPortalActivity"
                android:label="WebPortalActivity"
                android:allowEmbedded="true"
                android:allowTaskReparenting="true"
                android:enabled="true">
            </activity>
        </code/>
    </pre>
6. Add the initialization call into your Activity onCreate method:
```java

import com.ldrly.android.sdk.LDRLY;

public class MainActivity extends Activity {
    LDRLY ldrly;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        final String NAMESPACE = "your_game_namespace";
        final String API_KEY = "your_api_key";
        final String API_SECRET = "your_api_secret";

        ldrly = new LDRLY(this, API_KEY, API_SECRET, NAMESPACE, true);
    }
}

```
7. To invoke the LDRLY UI: ldrly.openPortal()
8. To submit player data on LDRLY, the *submit stat* methods must be invoked throughout the game. 
    1.For more details on each **stat type** see https://developers.ldrly.com/docs/
    2. e.g. ldrly.submitMaxStat("coins", 500)
        1. This value will be added to the **coins** stat for this player.

Upgrading
-----

Re-import the new LDRLY JAR, following the same steps outline in Setup.

Support
-----

Questions? Please contact us at support@ldrly.com.