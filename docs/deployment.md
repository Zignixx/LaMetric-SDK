# Deployment

Apps are distributed as ipk files, a format designed for use on embedded Linux platforms. It essentially consists of some nested archived folders, and can be created by hand using common Linux tools such as tar and ar. To speed up the process, the SDK distribution contains a package script in the script folder. If you are using the Makefile included in the sample project, you can just make the package target, and the ipk file will be created for you in the dist folder.

If you invoke the package.sh script manually, have a look at the comments in the script itself.

Then copy the ipk file from the dist folder onto your device (e.g. via ssh).

On the device, use opkg-cl for installing the package:

```
opkg-cl install com.lametric.sdk.sample_1.0.0.ipk
```

Lastly, create a widget instance for the newly installed application:

```
widget.sh create com.lametric.sdk.sample
```

Once you have installed the package and only change the executable, you can update the app without reinstalling the whole package. Just copy the executable to the application folder under `/lametric/data/apps/{package_name}. The OS will automatically notice the program changed and start it anew.
