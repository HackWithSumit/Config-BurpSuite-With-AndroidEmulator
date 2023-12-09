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


Now, we will export the CA certificates from burp.

Under the same tab, click on the "Import / export CA certificate" button.


![image](https://github.com/HackWithSumit/Config-BurpSuite-With-AndroidEmulator/assets/120317751/57d3221a-e4b6-447c-aa3b-35f55e3c0585)

Export it as DER format but save it with the .crt extension.


![image](https://github.com/HackWithSumit/Config-BurpSuite-With-AndroidEmulator/assets/120317751/012eff6f-4900-462b-a708-68f0dfe3475a)



![image](https://github.com/HackWithSumit/Config-BurpSuite-With-AndroidEmulator/assets/120317751/584d97c3-41bd-4eee-b495-738ed8e70f74)


<B><h2>Configure Proxy Settings for Emulator<b></h2>

On your emulator, click on the ... icon, then go to Settings.

Under the Proxy tab, configure the following settings, then click apply.  

![image](https://github.com/HackWithSumit/Config-BurpSuite-With-AndroidEmulator/assets/120317751/fd8e40f7-dd3d-4d89-bde3-2f08336d1a27)


        💡 Make sure the port number in the emulator is the same as in your burp settings.


<b><h2>Installing Burp CA Cert</h2></b>

To transfer the certs into your device for installation, you can simply drag and drop the .crt certificate into the emulator, or you can use adb to push the file to the AVD.

Once you transfer the certificate, go to Settings > Security > Encryption & Credentials. Then click on the "Install certificates from SD card" option.


![image](https://github.com/HackWithSumit/Config-BurpSuite-With-AndroidEmulator/assets/120317751/ebadab2d-246b-4a90-89ea-9aea750a74f7)

Select the Certificate file. If you dragged and dropped the file, it will be under /sdcard/Downloads.

![image](https://github.com/HackWithSumit/Config-BurpSuite-With-AndroidEmulator/assets/120317751/b8a6424a-b87e-4e75-bd75-895d1bb496f6)


Once installed, you can check your certificate under the Trusted credentials tab.

![image](https://github.com/HackWithSumit/Config-BurpSuite-With-AndroidEmulator/assets/120317751/d36fae5a-42c4-4dc8-a8dc-0370d04207a8)



With this, you can start browsing the web through chrome and fill up the request in burp.

![image](https://github.com/HackWithSumit/Config-BurpSuite-With-AndroidEmulator/assets/120317751/1590f6d2-a6ce-49bd-802d-7f14e7d71ce0)


<b><h2>Adding Certificates to System Trust Store</h2></b>


But we are not done yet. From Android 7 and upwards, Android uses 2 different Trust Stores, the user trust store and the system trust store. Chrome is one of the few apps that trust custom root CA certificates installed by the user. However, unlike chrome, most apps nowadays don't trust the certificates that are not from the System Trust Store.

We will have to inject our CA cert into the System Trust Store to solve this. There are various ways to do this, but one of the easiest ways is to use magisk and a module.


<b><h2>Rooting the AVD</b></h2>


      ‼️Security Caution:
      The script below is an Open Source Tool developed by newbit. Running unknown script on your system is often dangerous and is discouraged. The source code of this 
      script is available on Github for you to audit yourself, but running opensource scripts and tools is a matter of trust. They can be changed at any given time to 
      contain malicious code that can collect your data or do anything nefarious with your system. Continue at your own risk as any actions and activities related to 
      the material contained within is solely your responsibility. We will not be held responsible in the event any damages is incurred.












