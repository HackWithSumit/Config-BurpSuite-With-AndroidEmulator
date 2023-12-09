<B> <h2>Configure BurpSuite With Android Emulator</h2> </b>

While testing mobile applications, we need to set up a proxy to monitor the app's requests behind the pretty GUI. This article will show you how to set up a Burp Suite Proxy to work with an Android emulator.

<b><h3>Creating AVD with Android Studio</h3></b>

We are using a Pixel 4 AVD image with Playstore enabled for this tutorial.



![image](https://github.com/HackWithSumit/Config-BurpSuite-With-AndroidEmulator/assets/120317751/9f65f4e5-9dda-420f-9456-74069c2a0d4c)


Select Android 11 (API 30) as a system image.


![image](https://github.com/HackWithSumit/Config-BurpSuite-With-AndroidEmulator/assets/120317751/931ff935-c422-4166-b69c-d5fa769b9287)

<b><h3>Setting Up Proxy</b></h3>

If you have burp installed, go to the Proxy tab and then click Options.


![image](https://github.com/HackWithSumit/Config-BurpSuite-With-AndroidEmulator/assets/120317751/21108f68-fb51-4cbe-a421-84b1c88ff235)


Under Proxy Listeners, click the Add button to create a new proxy listener. Choose the port you desire and click ok.



![image](https://github.com/HackWithSumit/Config-BurpSuite-With-AndroidEmulator/assets/120317751/d4315d48-637e-48a2-90bf-4758da207a03)


<b><h2>Export CA cert</h2></b>

