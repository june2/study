## Debug
1. Run expo 
2. Import gradle project
3. Setup setting

![image](https://user-images.githubusercontent.com/5827617/68465667-3d78ee80-0256-11ea-8767-2026a872126c.png)
 

4. Select simulator or device / control + R

## Build release and Upload to Play store
1. run `expo publish`
2. Genrate signed bundle

![image](https://user-images.githubusercontent.com/5827617/68465740-639e8e80-0256-11ea-8c88-789474fbb34d.png)


3. Select AAB or APK (You can reduce app size by AAB)

![image](https://user-images.githubusercontent.com/5827617/68465827-8d57b580-0256-11ea-8092-6e7ad1b80831.png)

4. Input the key
 - To get keystore, you can run `expo fetch:android:keystore` and download the file from your root project.

![image](https://user-images.githubusercontent.com/5827617/68465907-b4ae8280-0256-11ea-9c9f-d07fcd6de568.png)

5. Upload release file

![image](https://user-images.githubusercontent.com/5827617/68466117-1838b000-0257-11ea-8536-5a9338f3a3b7.png)
