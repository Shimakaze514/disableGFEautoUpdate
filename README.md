# 中文
## 下载老版本GeForce Experience
[Reddit原贴链接](https://www.reddit.com/r/GeForceExperience/comments/1hrwdp0/any_way_to_download_the_old_geforce_experience_app/)

[3.28.0.417版本](https://web.archive.org/web/*/https://us.download.nvidia.com/GFE/GFEClient/3.28.0.417/GeForce_Experience_v3.28.0.417.exe)
最新，也是最后的GFE版本，此版本后官方放弃GFE全面转向NVIDIA App

[3.27.0.120版本](https://web.archive.org/web/*/https://us.download.nvidia.com/GFE/GFEClient/3.27.0.120/GeForce_Experience_v3.27.0.120.exe)
倒数第二个版本，据说比最后一个版本要稳定
~~但是会把OBS识别成某个不知名游戏，虽然对使用没有影响~~

> **注意**:下载安装完成之后先不要登录，登录了他就会开始检查更新并且提示重启安装更新。
---

## 禁止程序写入GFE文件夹
1.  右键 `C:\Program Files\NVIDIA Corporation\NVIDIA GeForce Experience`
2.  属性→安全→高级→（所有者）更改→高级→立即查找
3.  在搜索结果里找到自己的用户名，选中后点击确定
4.  在 `NVIDIA GeForce Experience高级安全设置` 页面左下角点击 `禁用继承`，然后选择删除自动生成的权限
5.  点击 `添加` ，把你自己添加为唯一有权限的人，并且只勾选以下权限
    - 读取和执行
    - 列出文件夹内容
    - 读取
6.  一路点击确定离开属性页面，再右键打开属性一次把只读勾上。
---

## 关闭自动更新
1.  进入 `C:\ProgramData\NVIDIA Corporation\Downloader`，找到 `gfeupdate.json`
2.  把内容改成
    ```json
    {"isMandatory":false,"num_of_attempts":0,"url":""}
    ```  
3.  保存，再参照“禁止程序写入GFE文件夹”一节中的内容，禁止程序写入这个文件。
4.  删除Downloader中的所有其他文件。
5.  回到Downloader文件夹，参照““禁止程序写入GFE文件夹”一节中的内容，禁止程序写入这个文件夹。~~其实做了这一步前一步可以不用做？双重保险还是做一下比较好~~
---

## 关闭计划任务
1.  Windows搜索“任务计划程序”
2.  任务计划程序库（本地）→任务计划程序
3.  找到以下四个任务：
    - NJwDriverlpdatecheckDaily 
    - NVIDIA GeForce Experience SelfUpdate_
    - NvNodeLauncher
    - NVProfileUpdaterDaily
    - NvProfileUpdaterOnLogon
4. 逐个右键，先点击“结束”，再点击“禁用。
---

## 结果
现在GeForce Experience将：
- 不会检查更新
- 不会自动下载更新
- 启动时不会先弹出新版本的安装程序
- 不会询问你是否要更新
- 任何外部程序尝试更新GFE都会失败（除非你再次进入GFE文件夹的“属性”页面并把权限恢复到“完全访问”）


# English
## Downloading Older Versions of GeForce Experience  
[Original Reddit Post](https://www.reddit.com/r/GeForceExperience/comments/1hrwdp0/any_way_to_download_the_old_geforce_experience_app/)  

**[Version 3.28.0.417](https://web.archive.org/web/*/https://us.download.nvidia.com/GFE/GFEClient/3.28.0.417/GeForce_Experience_v3.28.0.417.exe)**  
The latest and final GFE version before NVIDIA discontinued it in favor of the NVIDIA App.  

**[Version 3.27.0.120](https://web.archive.org/web/*/https://us.download.nvidia.com/GFE/GFEClient/3.27.0.120/GeForce_Experience_v3.27.0.120.exe)**  
The second-to-last version, reported to be more stable than the final release.  
~~May misidentify OBS as an unknown game (does not affect functionality)~~  

> **Important**: Do not sign in immediately after installation, as it will check for updates and prompt you to restart for installation.  
> 
## Block Write Access to GFE Folder  
1.  Right-click `C:\Program Files\NVIDIA Corporation\NVIDIA GeForce Experience`  
2.  Select **Properties** → **Security** → **Advanced** → **Change** (next to Owner) → **Advanced** → **Find Now**  
3.  Select your username from the search results and click **OK**.  
4.  Under **Advanced Security Settings**, click **Disable Inheritance** → Select **Remove all inherited permissions**.  
5.  Click **Add** → Add only yourself as the authorized user with the following permissions:  
    -   **Read & execute**  
    -   **List folder contents**  
    -   **Read**  
6.  Click **OK** to close all dialogs. Open Properties again and enable the **Read-only** attribute.  

---

## Disable Automatic Updates  
1.  Navigate to `C:\ProgramData\NVIDIA Corporation\Downloader` and open `gfeupdate.json`.  
2.  Replace its contents with:  
    ```json
    {"isMandatory":false,"num_of_attempts":0,"url":""}
    ```  
3.  Save the file, then apply the **Block Write Access** steps above to this file.  
4.  Delete all other files in "Downloader" folder
5.  Apply the **Block Write Access** steps to the entire `Downloader` folder.  
    ~~*(Step 3 can be skipped if completing Step 4, but dual protection is recommended.)*~~  

---

## Disable Scheduled Tasks  
1.  Search for **Task Scheduler** in Windows and open it.  
2.  Navigate to **Task Scheduler Library** → **Task Scheduler (Local)**  
3.  Locate these five tasks:  
    - `NJwDriverUpdatecheckDaily`  
    - `NVIDIA GeForce Experience SelfUpdate_`  
    - `NvNodeLauncher`  
    - `NVProfileUpdaterDaily`  
    - `NvProfileUpdaterOnLogon`  
4.  For each task:  
    - Right-click and select **End**  
    - Right-click again and select **Disable**  

---

## Result  
GeForce Experience will now:  
-   No longer check for updates  
-   Not automatically download updates  
-   Not launch the new version installer at startup  
-   Not prompt to update  
-   Block update attempts from external programs  
    *(Unless you restore "Full Control" permissions in the GFE folder Properties)* 
---
