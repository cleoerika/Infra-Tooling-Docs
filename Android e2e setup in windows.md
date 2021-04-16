# E2E Android setup in Windows

### Pre-requisite
  - git
  - Apache Maven
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
  
  <img width="1341" alt="image" src="https://user-images.githubusercontent.com/56558508/115071595-0b7aba00-9f29-11eb-870a-74b8ae6a8fd6.png">

This will get the **stargategalaxy** as a submodule to your **/androidautomation** repo
  
4. Navigate to **/stargategalaxy** repo then **/Stargate** and run **mvn clean install**
5. Navigate to **~/androidautomation/AndroidStargate** and run **mvn clean install then mvn eclipse:eclipse**
6. Navigate to **~/androidautomation/PlatformQATests** and run **mvn clean install then mvn eclipse:eclipse**
7. Import **AndroidStargate** and **PlatformQATest** in eclipse

