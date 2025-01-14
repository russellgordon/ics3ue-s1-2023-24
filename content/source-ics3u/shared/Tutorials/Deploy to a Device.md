---
created: 2023-11-06T00:00:00.000-0400
---
To run applications you write in Xcode on your iPhone or iPad, a few *one-time-only* setup steps are required.

> [!NOTE]
> 
> These instructions were written a year ago for iOS 16 and Xcode 14, however... the steps are identical for iOS17 and Xcode 15. Minor details in some of the screenshots may differ.

First, be sure Xcode is open.

Select the menu sequence **Window** → **Devices and Simulators**.

Then, connect your iPhone or iPad to your Mac using a cable.

The first time you do this, you will see an image something like this:

![[Screen Shot 2022-10-31 at 7.09.22 AM.png]]

To test applications you write on a physical device the device must be in *developer mode*. 

> [!NOTE]
> The instructions that follow are for **iOS 16.**
> If you have an earlier version of iOS on your phone, try [these instructions instead](https://www.russellgordon.ca/tutorials/adding-a-physical-device-as-a-run-destination/).

To do this, first open the **Settings** app, then select **Privacy & Security**:

![[IMG_1521 copy.png|400]]

Then select **Developer Mode**:

![[IMG_1522 copy.png|400]]

Then restart your iPhone:

![[IMG_1523 copy.png|400]]

> [!NOTE]
> Despite the warning about reduced device security, know that an application cannot be loaded on to your phone unless it is unlocked and you have explicitly indicated that you trust the developer who wrote the app.

After restarting your phone, you will see this message appear – select **Turn on**:

![[IMG_1524 copy.png|400]]

You will need to provide your device passcode:

![[IMG_1525 copy.png|400]]

Now that you have enabled developer mode on your phone, back in Xcode in the **Devices and Simulators** dialog, you will see a yellow banner message telling you that certain required files are being copied to and from your device:

![[Screen Shot 2022-10-31 at 7.14.04 AM.png]]

That process may take a few minutes to complete; be patient. When it is finished, the yellow banner will disappear.

Next, you can select the device you've connected as a run destination.

At the top of the primary Xcode window, click the list of devices (1), then select your device from the list (2):

![[Screen Shot 2022-10-31 at 7.35.54 AM.png]]

Now build the application:

![[Screen Shot 2022-10-31 at 7.37.00 AM.png]]

Next, will likely see a message indicating that Xcode cannot run the application on the device, because, essentially, your iPhone or iPad currently does not "trust" the Mac that you are developing on to install applications upon it:

![[Screen Shot 2022-10-31 at 7.39.02 AM.png|300]]

On your phone, you will see a message like this:

![[IMG_1526.png|400]]

To create the necessary trust, follow these steps.

Open **Settings** again, and choose **General**:

![[IMG_1527.png|400]]

Then select **VPN &  Device Management**:

![[IMG_1528.png|400]]

Under **Developer App**, you will see a profile tied to your LCS Apple ID – select that profile:

![[IMG_1529.png|400]]

To run apps you make using your LCS Apple ID on your device, select the button as shown:

![[IMG_1530.png|400]]

Finally, on the dialog that appears, select **Trust**:

![[IMG_1531.png|400]]

The next time you build your application with your iPhone or iPad as the selected run destination, after a few seconds, you should see the app open on your device.

Have fun! 🚀
