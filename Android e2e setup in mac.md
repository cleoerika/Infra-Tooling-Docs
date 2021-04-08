# E2E Android setup in Mac

### Pre-requisite
  - JDK 8
  - Eclipse
  - TestNg for Eclipse
  - Appium Desktop for mac (V1.6.3) https://github.com/appium/appium-desktop/releases/tag/v1.6.3
  - Android Studio (4.1.3 or latest version) https://developer.android.com/studio?gclid=EAIaIQobChMI0JfgsZvv7wIVlJ1LBR1CIwCHEAAYASAAEgKvr_D_BwE&gclsrc=aw.ds
  - Kony Visualizer (V9 SP2 FP13) https://community.kony.com/downloads

### Steps:
#### Setting up in eclipse
1. Clone the **androidautomation** and **stargategalaxy** repository
  - https://github01.hclpnp.com/phoenix-core/androidautomation
  - https://github01.hclpnp.com/phoenix-core/stargategalaxy

2. Navigate to **/androidautomation** folder and modify the url inside .gitmodules
  ```
  url = "https://github01.hclpnp.com/phoenix-core/stargategalaxy.git"
  ```
  
3. In command line, go to **/stargategalaxy** and run the ff. git commands:

  ```
  git submodule init
  ```

  ```
  git config --file=.gitmodules submodule.stargategalaxy.url git@github01.hclpnp.com/phoenix-core/stargategalaxy
  ```

  ```
  git submodule sync
  ```
  
  ```
  git submodule update
  ```
  This will get the **stargategalaxy** as a submodule to your **/androidautomation** repo
  
4. Navigate to **/stargategalaxy** repo then **/Stargate** and run **mvn clean install**
5. Navigate to **~/androidautomation/AndroidStargate** and run **mvn clean install then mvn eclipse:eclipse**
6. Navigate to **~/androidautomation/PlatformQATests** and run **mvn clean install then mvn eclipse:eclipse**
7. Import **AndroidStargate** and **PlatformQATest** in eclipse


#### Setting up Appium
1. Open Appium

 <img width="651" alt="image" src="https://user-images.githubusercontent.com/56558508/113621049-b966a880-968d-11eb-8540-713ea6e3671d.png">

2. Click 'Start Server v1.8.1'

  <img width="653" alt="image" src="https://user-images.githubusercontent.com/56558508/114081671-700d9780-98df-11eb-9cd1-e9fe9e7fbf97.png">

#### Setting up Android Studio
1. Open Android Studio

 <img width="778" alt="image" src="https://user-images.githubusercontent.com/56558508/113623375-da7cc880-9690-11eb-9bd6-c3dfd1eb60b9.png">

2. Select **Create New Project** then **Empty Activity** as Project Template then click **Next**

 <img width="900" alt="image" src="https://user-images.githubusercontent.com/56558508/113623437-ef595c00-9690-11eb-910f-8b27ee3d9e5b.png">

3. Set Language to **Java** and Minimum SDK to **API 28: Android 9.0 (Pie)**

 <img width="901" alt="image" src="https://user-images.githubusercontent.com/56558508/113623650-3a736f00-9691-11eb-8a22-79fd25f533f6.png">

4. Then **Finish**, the Application will pop 

<img width="1400" alt="image" src="https://user-images.githubusercontent.com/56558508/113623759-5b3bc480-9691-11eb-8f46-08ed72292b1f.png">

5. Click the arrow down beside **Pixel_3a...** then select **AVD Manager**

<img width="1399" alt="image" src="https://user-images.githubusercontent.com/56558508/113624031-b8377a80-9691-11eb-97b5-f5d8d2b7d0bb.png">

6. Another window will open **Your Virtual Devices**

<img width="1199" alt="image" src="https://user-images.githubusercontent.com/56558508/113624271-ffbe0680-9691-11eb-8329-9e5cfb9ccec9.png">

7. Click **+ Create Virtual Device...**, window of **Select Hardware** will pop

<img width="1000" alt="image" src="https://user-images.githubusercontent.com/56558508/113624383-27ad6a00-9692-11eb-858b-9164b6b15a34.png">

8. Select **Phone** and choose **Nexus 5X** then click **Next**
9. Select **x86 Images** tab then look for API level **28** with ABI **x86_64** and Target **Android 9.0 (Google APIs)**

<img width="999" alt="image" src="https://user-images.githubusercontent.com/56558508/113624918-d18cf680-9692-11eb-95f5-58dd1141fd36.png">

10. Click **Download** and **Accept**

<img width="899" alt="image" src="https://user-images.githubusercontent.com/56558508/113625150-229cea80-9693-11eb-84ee-1f63d19a475d.png">

11 It will start to install

<img width="901" alt="image" src="https://user-images.githubusercontent.com/56558508/113625214-3a746e80-9693-11eb-8137-1be19c08e553.png">

12. Then **Finish**

<img width="901" alt="image" src="https://user-images.githubusercontent.com/56558508/113625790-f5047100-9693-11eb-8814-c9d2e3d24d79.png">

13. Since it is already installed the **Next** button for the **Pie 28 x86_64** will be enabled,**Next**

<img width="999" alt="image" src="https://user-images.githubusercontent.com/56558508/113625956-2715d300-9694-11eb-875c-3390e7cb67c8.png">

14.**Finish**

<img width="997" alt="image" src="https://user-images.githubusercontent.com/56558508/113626045-3d239380-9694-11eb-81c5-2830a68d8d52.png">

15. The device will be added in the list then close the window

<img width="1200" alt="image" src="https://user-images.githubusercontent.com/56558508/113626148-5fb5ac80-9694-11eb-8268-a4d198ac51c3.png">

16. You can now select **Nexus 5X API 28** in the dropdown and click the green play button beside

<img width="1401" alt="image" src="https://user-images.githubusercontent.com/56558508/113627035-7f99a000-9695-11eb-8da3-20e7b22922eb.png">

17. The device will be launched

<img width="502" alt="image" src="https://user-images.githubusercontent.com/56558508/113627153-ace64e00-9695-11eb-9110-a7537bb93b44.png">


#### Setting up Visualizer
1. Download atleast 1 or 2 zip files from https://github01.hclpnp.com/phoenix-core/V9-Preview/tree/phx-dev/9.0
2. Open Visualizer
3. 

