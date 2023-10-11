
# Post \#68678008 [Link](https://stackoverflow.com/questions/68678008/)

## Apps targeting Android 12 and higher required to specify an explicit value for `android:exported` [Cordova]

**Vote**: 19 (269/702) **Views**: 18143 (317/702) 

**Internal ID** \#0-0-16

Created at 2021-08-06 07:49:26

Tags: `node.js` `angular` `cordova` `github` `ionic-framework`

----------

#### Metadata:

Area: `Front-end`

Language: `javascript` (full parsed tag list: `javascript`)

----------

**Notepad**


----------

When I am running to make the Apk in GitHub I got the error. As I am building the Apk in GitHub. There is no way to define something inside manifest as it is building every time fresh. All I can do is inside the Config.Xml file. After Adding `android:exported="false"` to it, also getting same error. Both images for this question reference attached here. [GitHub Error](https://i.stack.imgur.com/LLMnt.png) and [Config.Xml](https://i.stack.imgur.com/yBSTy.png). Help will be appreciated.
```
<?xml version='1.0' encoding='utf-8'?>
<widget id="com.likehub.sweetheart" version="1.1.64" xmlns="http://www.w3.org/ns/widgets" xmlns:cdv="http://cordova.apache.org/ns/1.0">
    <name>sweetheart</name>
    <description>making love bird together</description>
    <author email="mynamey9er@gmail.com" href="">likehub</author>
    <content src="index.html" />
    <access origin="*" />
    <allow-intent href="http://*/*" />
    <allow-intent href="https://*/*" />
    <allow-intent href="tel:*" />
    <allow-intent href="sms:*" />
    <allow-intent href="mailto:*" />
    <allow-intent href="geo:*" />
    <preference name="AndroidXEnabled" value="true" />
    <preference name="WebViewBounce" value="false" />
    <preference name="UIWebViewBounce" value="false" />
    <preference name="DisallowOverscroll" value="true" />
    <preference name="LoadUrlTimeoutValue" value="700000" />
    <preference name="ScrollEnabled" value="false" />
    <preference name="SplashMaintainAspectRatio" value="true" />
    <preference name="FadeSplashScreenDuration" value="1000" />
    <preference name="FadeSplashScreen" value="true" />
    <preference name="SplashShowOnlyFirstTime" value="false" />
    <preference name="SplashScreen" value="screen" />
    <preference name="SplashScreenDelay" value="5000" />
    <preference name="AutoHideSplashScreen" value="true" />
    <preference name="ShowSplashScreen" value="false" />
    <preference name="ShowSplashScreenSpinner" value="false" />
    <preference name="android-minSdkVersion" value="22" />
    <preference name="BackupWebStorage" value="none" />
    <preference name="Orientation" value="portrait" />
    <preference name="AndroidPersistentFileLocation" value="Compatibility" />
    <preference name="GradlePluginKotlinEnabled" value="true" />
    <preference name="GradlePluginKotlinCodeStyle" value="official" />
    <preference name="GradlePluginKotlinVersion" value="1.3.50" />
    <preference name="AndroidLaunchMode" value="singleTask" />
    <feature name="StatusBar">
        <param name="ios-package" onload="true" value="CDVStatusBar" />
    </feature>
    <platform  name="android">
        <preference name="android-targetSdkVersion" value="31" />
        <edit-config  file="app/src/main/AndroidManifest.xml" mode="merge" android:exported="true" target="/manifest/application" xmlns:android="http://schemas.android.com/apk/res/android">
            <application android:usesCleartextTraffic="true" />
            <application android:networkSecurityConfig="@xml/network_security_config" />
            
            <intent-filter>
                <action  android:name="MainActivity" android:exported="false"/>
                <category android:name="android.intent.category.DEFAULT" />
            </intent-filter>
        </edit-config>
        <resource-file src="resources/android/xml/network_security_config.xml" target="app/src/main/res/xml/network_security_config.xml" />
        <allow-intent href="market:*" />
        <icon density="ldpi" src="resources/android/icon/drawable-ldpi-icon.png" />
        <icon density="mdpi" src="resources/android/icon/drawable-mdpi-icon.png" />
        <icon density="hdpi" src="resources/android/icon/drawable-hdpi-icon.png" />
        <icon density="xhdpi" src="resources/android/icon/drawable-xhdpi-icon.png" />
        <icon density="xxhdpi" src="resources/android/icon/drawable-xxhdpi-icon.png" />
        <icon density="xxxhdpi" src="resources/android/icon/drawable-xxxhdpi-icon.png" />
        <splash density="land-ldpi" src="resources/android/splash/drawable-land-ldpi-screen.png" />
        <splash density="land-mdpi" src="resources/android/splash/drawable-land-mdpi-screen.png" />
        <splash density="land-hdpi" src="resources/android/splash/drawable-land-hdpi-screen.png" />
        <splash density="land-xhdpi" src="resources/android/splash/drawable-land-xhdpi-screen.png" />
        <splash density="land-xxhdpi" src="resources/android/splash/drawable-land-xxhdpi-screen.png" />
        <splash density="land-xxxhdpi" src="resources/android/splash/drawable-land-xxxhdpi-screen.png" />
        <splash density="ldpi" src="resources/android/splash/drawable-port-ldpi-screen.png" />
        <splash density="port-ldpi" src="resources/android/splash/drawable-port-ldpi-screen.png" />
        <splash density="mdpi" src="resources/android/splash/drawable-port-mdpi-screen.png" />
        <splash density="port-mdpi" src="resources/android/splash/drawable-port-mdpi-screen.png" />
        <splash density="hdpi" src="resources/android/splash/drawable-port-hdpi-screen.png" />
        <splash density="port-hdpi" src="resources/android/splash/drawable-port-hdpi-screen.png" />
        <splash density="xhdpi" src="resources/android/splash/drawable-port-xhdpi-screen.png" />
        <splash density="port-xhdpi" src="resources/android/splash/drawable-port-xhdpi-screen.png" />
        <splash density="xxhdpi" src="resources/android/splash/drawable-port-xxhdpi-screen.png" />
        <splash density="port-xxhdpi" src="resources/android/splash/drawable-port-xxhdpi-screen.png" />
        <splash density="xxxhdpi" src="resources/android/splash/drawable-port-xxxhdpi-screen.png" />
        <splash density="port-xxxhdpi" src="resources/android/splash/drawable-port-xxxhdpi-screen.png" />
    </platform>
    <platform name="ios">
        <allow-intent href="itms:*" />
        <allow-intent href="itms-apps:*" />
        <icon height="57" src="resources/ios/icon/icon.png" width="57" />
        <icon height="114" src="resources/ios/icon/icon@2x.png" width="114" />
        <icon height="29" src="resources/ios/icon/icon-small.png" width="29" />
        <icon height="58" src="resources/ios/icon/icon-small@2x.png" width="58" />
        <icon height="87" src="resources/ios/icon/icon-small@3x.png" width="87" />
        <icon height="20" src="resources/ios/icon/icon-20.png" width="20" />
        <icon height="40" src="resources/ios/icon/icon-20@2x.png" width="40" />
        <icon height="60" src="resources/ios/icon/icon-20@3x.png" width="60" />
        <icon height="48" src="resources/ios/icon/icon-24@2x.png" width="48" />
        <icon height="55" src="resources/ios/icon/icon-27.5@2x.png" width="55" />
        <icon height="29" src="resources/ios/icon/icon-29.png" width="29" />
        <icon height="58" src="resources/ios/icon/icon-29@2x.png" width="58" />
        <icon height="87" src="resources/ios/icon/icon-29@3x.png" width="87" />
        <icon height="40" src="resources/ios/icon/icon-40.png" width="40" />
        <icon height="80" src="resources/ios/icon/icon-40@2x.png" width="80" />
        <icon height="120" src="resources/ios/icon/icon-40@3x.png" width="120" />
        <icon height="88" src="resources/ios/icon/icon-44@2x.png" width="88" />
        <icon height="50" src="resources/ios/icon/icon-50.png" width="50" />
        <icon height="100" src="resources/ios/icon/icon-50@2x.png" width="100" />
        <icon height="60" src="resources/ios/icon/icon-60.png" width="60" />
        <icon height="120" src="resources/ios/icon/icon-60@2x.png" width="120" />
        <icon height="180" src="resources/ios/icon/icon-60@3x.png" width="180" />
        <icon height="72" src="resources/ios/icon/icon-72.png" width="72" />
        <icon height="144" src="resources/ios/icon/icon-72@2x.png" width="144" />
        <icon height="76" src="resources/ios/icon/icon-76.png" width="76" />
        <icon height="152" src="resources/ios/icon/icon-76@2x.png" width="152" />
        <icon height="167" src="resources/ios/icon/icon-83.5@2x.png" width="167" />
        <icon height="172" src="resources/ios/icon/icon-86@2x.png" width="172" />
        <icon height="196" src="resources/ios/icon/icon-98@2x.png" width="196" />
        <icon height="1024" src="resources/ios/icon/icon-1024.png" width="1024" />
        <splash height="480" src="resources/ios/splash/Default~iphone.png" width="320" />
        <splash height="960" src="resources/ios/splash/Default@2x~iphone.png" width="640" />
        <splash height="1024" src="resources/ios/splash/Default-Portrait~ipad.png" width="768" />
        <splash height="768" src="resources/ios/splash/Default-Landscape~ipad.png" width="1024" />
        <splash height="1125" src="resources/ios/splash/Default-Landscape-2436h.png" width="2436" />
        <splash height="1242" src="resources/ios/splash/Default-Landscape-736h.png" width="2208" />
        <splash height="2048" src="resources/ios/splash/Default-Portrait@2x~ipad.png" width="1536" />
        <splash height="1536" src="resources/ios/splash/Default-Landscape@2x~ipad.png" width="2048" />
        <splash height="2732" src="resources/ios/splash/Default-Portrait@~ipadpro.png" width="2048" />
        <splash height="2048" src="resources/ios/splash/Default-Landscape@~ipadpro.png" width="2732" />
        <splash height="1136" src="resources/ios/splash/Default-568h@2x~iphone.png" width="640" />
        <splash height="1334" src="resources/ios/splash/Default-667h.png" width="750" />
        <splash height="2208" src="resources/ios/splash/Default-736h.png" width="1242" />
        <splash height="2436" src="resources/ios/splash/Default-2436h.png" width="1125" />
        <splash height="2732" src="resources/ios/splash/Default@2x~universal~anyany.png" width="2732" />
        <icon height="216" src="resources/ios/icon/icon-108@2x.png" width="216" />
        <splash height="2688" src="resources/ios/splash/Default-2688h~iphone.png" width="1242" />
        <splash height="1242" src="resources/ios/splash/Default-Landscape-2688h~iphone.png" width="2688" />
        <splash height="1792" src="resources/ios/splash/Default-1792h~iphone.png" width="828" />
        <splash height="828" src="resources/ios/splash/Default-Landscape-1792h~iphone.png" width="1792" />
    </platform>
    <plugin name="cordova-plugin-googleplus" spec="^8.4.0">
        <variable name="WEB_APPLICATION_CLIENT_ID" value="0000000000000-wwwwwwwmkv51oxxxxxxxxxxx.apps.googleusercontent.co" />
    </plugin>
    <platform name="android">
        <preference name="GoogleAndroidClientId" value="888809hhju-i9hd0hc6v51obgdubbgxwbnhiywgdiueh.apps.googleusercontent.com" />
    </platform>
    <plugin name="cordova-plugin-whitelist" spec="1.3.5" />
    <plugin name="cordova-plugin-statusbar" spec="2.4.3" />
    <plugin name="cordova-plugin-device" spec="2.0.3" />
    <plugin name="cordova-plugin-splashscreen" spec="6.0.0" />
    <plugin name="cordova-plugin-ionic-webview" spec="5.0.0" />
    <plugin name="cordova-plugin-ionic-keyboard" spec="^2.2.0" />
</widget>
```


> Apps targeting Android 12 and higher are required to specify an explicit value for `android:exported` when the corresponding component has an intent filter defined. See [https://developer.android.com/guide/topics/manifest/activity-element#exported](https://developer.android.com/guide/topics/manifest/activity-element#exported) for details.


----------
        
## Answer \#0

**Accepted** Vote: 2

Created at 2021-08-15 14:31:38

------------

Build-tool 31.0.0 installed in virtual environment was causing this error.
Adding this solution worked for me
> - 
Also removed this
> ionic cordova platform add android@latest
uses (cordova-android@10.0.1)
and added this
> ionic cordova platform add android
uses (cordova-android@9.0.0)
As cordova-android@10.0.1 was also causing
> app:compileReleaseJavaWithJavac FAILED
Modified Working Workflow:
```
runs-on: ubuntu-latest
   steps:
   - uses: actions/checkout@v2
   - uses: actions/setup-java@v2
     with:
      distribution: 'adopt' # See 'Supported distributions' for available options
      java-version: '8'
   - name: Use coturiv/setup-ionic
     uses: coturiv/setup-ionic@v1.0.4

   - name: Uninstall 31.0.0 Build tool
     run: $ANDROID_SDK_ROOT/tools/bin/sdkmanager --uninstall 'build-tools;31.0.0'

   - name: Run cordova project tests
     run: |
       ionic start testapp blank --cordova --type angular --no-link --no-git --no-interactive --confirm
       cd testapp
       ionic cordova platform add android
       ionic cordova build android
```




------------
    
    
## Answer \#1

 Vote: 18

Created at 2021-08-06 14:51:20

------------

You can try like this in `config.xml` under android platform -
```
<edit-config
  file="app/src/main/AndroidManifest.xml"
  target="/manifest/application/activity[@android:name='MainActivity']"
  mode="merge">
    <activity android:exported="true"/>
</edit-config>
```

Make sure to target the file and the activity's name properly.
Due to `merge` mode, `android:exported="true"` will be added to target activity element. This will replace the values if the it is already exist in the target element.


------------
    
    
## Answer \#2

 Vote: 6

Created at 2022-07-07 12:05:11

------------

As the message is saying:
`android:exported`
To fix this I went to the `platforms/android/app/src/main/AndroidManifest.xml` and searched for all `<intent-filter>` tags.
Then I checked if their parent tag had the `android:exported` property and added it where it was missing by using `<edit-config>`.
In my case, the `Social Sharing` plugin was causing the problem, so I add this in my `config.xml` file.
```
<platform name="android">
  <edit-config file="app/src/main/AndroidManifest.xml" mode="merge" target="/manifest/application/receiver[@android:name='nl.xservices.plugins.ShareChooserPendingIntent']">
    <activity android:exported="true" />
  </edit-config>
  ...
</platform>
```

Solution found in [here](https://github.com/EddyVerbruggen/SocialSharing-PhoneGap-Plugin/pull/1158).


------------
    
    
## Answer \#3

 Vote: 1

Created at 2022-08-21 18:59:31

------------

I tried to change a lot of configurations, but update Gradle did the trick
```
sdk install gradle 7.5.1
```



------------
    
    
## Answer \#4

 Vote: 0

Created at 2022-05-29 18:52:18

------------

For Capacitor ionic, I had to manually change the minCompileSDK at the following path from 31 to 30.
C:\Users\yourUserFolder.gradle\caches\transforms-3\be06223ace9bb785a17b62c00389baa4\transformed\browser-1.4.0\META-INF\com\android\build\gradle\aar-metadata.properties
Please note that your path might not be exactly the same as mine, and this is not a fix but just to allow you to build your apk as you figure out a more permanent solution


------------
    
    