# E2E Android setup in Mac

## Pre-requisite
- JDK 8
- Eclipse
- TestNg for Eclipse
- Appium Desktop for mac (V1.6.3) https://github.com/appium/appium-desktop/releases/tag/v1.6.3
- Android Studio (4.1.3 or latest version) https://developer.android.com/studio?gclid=EAIaIQobChMI0JfgsZvv7wIVlJ1LBR1CIwCHEAAYASAAEgKvr_D_BwE&gclsrc=aw.ds
- Kony Visualizer (V9 SP2 FP13) https://community.kony.com/downloads


Download and install Appium Desktop for mac 1.6.3 version from https://github.com/appium/appium-desktop/releases/tag/v1.6.3

<img width="651" alt="image" src="https://user-images.githubusercontent.com/56558508/113621049-b966a880-968d-11eb-8540-713ea6e3671d.png">

Click 'Start Server v1.8.1'

Open Android Studio

<img width="778" alt="image" src="https://user-images.githubusercontent.com/56558508/113623375-da7cc880-9690-11eb-9bd6-c3dfd1eb60b9.png">

Create New Project

Select Empty Activity then click Next

<img width="900" alt="image" src="https://user-images.githubusercontent.com/56558508/113623437-ef595c00-9690-11eb-910f-8b27ee3d9e5b.png">

Set Language to 'Java' and Minimum SDK to 'API 28: Android 9.0 (Pie)'

<img width="901" alt="image" src="https://user-images.githubusercontent.com/56558508/113623650-3a736f00-9691-11eb-8a22-79fd25f533f6.png">

then Finish, the Application will pop 

<img width="1400" alt="image" src="https://user-images.githubusercontent.com/56558508/113623759-5b3bc480-9691-11eb-8f46-08ed72292b1f.png">

Click the arrow down beside 'Pixel_3a...' then select 'AVD Manager'

<img width="1399" alt="image" src="https://user-images.githubusercontent.com/56558508/113624031-b8377a80-9691-11eb-97b5-f5d8d2b7d0bb.png">

Another window will open 'Your Virtual Devices'

<img width="1199" alt="image" src="https://user-images.githubusercontent.com/56558508/113624271-ffbe0680-9691-11eb-8329-9e5cfb9ccec9.png">

Click '+ Create Virtual Device...', window of Select Hardware will pop

<img width="1000" alt="image" src="https://user-images.githubusercontent.com/56558508/113624383-27ad6a00-9692-11eb-858b-9164b6b15a34.png">

Select 'Phone' from the Category and choose 'Nexus 5X' then click Next
Select 'x86 Images' tab then look for API level 28 with ABI x86_64 and Target Android 9.0 (Google APIs)
<img width="999" alt="image" src="https://user-images.githubusercontent.com/56558508/113624918-d18cf680-9692-11eb-95f5-58dd1141fd36.png">

Click 'Download' and 'Accept'
<img width="899" alt="image" src="https://user-images.githubusercontent.com/56558508/113625150-229cea80-9693-11eb-84ee-1f63d19a475d.png">

It will start to install

<img width="901" alt="image" src="https://user-images.githubusercontent.com/56558508/113625214-3a746e80-9693-11eb-8137-1be19c08e553.png">

Then 'Finish'

<img width="901" alt="image" src="https://user-images.githubusercontent.com/56558508/113625790-f5047100-9693-11eb-8814-c9d2e3d24d79.png">

Since it is already installed the 'Next' button for the Pie 28 x86_64 will be enabled,

<img width="999" alt="image" src="https://user-images.githubusercontent.com/56558508/113625956-2715d300-9694-11eb-875c-3390e7cb67c8.png">

Next


<img width="997" alt="image" src="https://user-images.githubusercontent.com/56558508/113626045-3d239380-9694-11eb-81c5-2830a68d8d52.png">

Finish, the device will be added in the list then close the window

<img width="1200" alt="image" src="https://user-images.githubusercontent.com/56558508/113626148-5fb5ac80-9694-11eb-8268-a4d198ac51c3.png">

You can now select 'Nexus 5X API 28' in the dropdown and click the green play button beside

<img width="1401" alt="image" src="https://user-images.githubusercontent.com/56558508/113627035-7f99a000-9695-11eb-8da3-20e7b22922eb.png">

The device will be launched

<img width="502" alt="image" src="https://user-images.githubusercontent.com/56558508/113627153-ace64e00-9695-11eb-9110-a7537bb93b44.png">



