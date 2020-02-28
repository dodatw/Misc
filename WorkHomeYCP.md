# Working From Home Document 

YouCam Perfect iOS

- http://pft-svn:8090/trac/androidbc/wiki/guide
- http://pft-svn:8090/trac/youperfect/wiki/install_macos_on_windows

- Antivirus
  - Windows
    ```
    ftp://ncov_pf:Perfectcorp@ftp.gocyberlink.com/IT/Antivirus/Windows/WIN64BIT/
    ```
  - Mac OS 10.14 or earlier
    - https://drive.google.com/file/d/1cgIhxK3fClYpZjefzz_c3qcnNdYtjoZ9/view?usp=sharing
  - Mac OS 10.15 and later
    - https://drive.google.com/file/d/1aawnNGQMjxn41mdItbaNuj5gVwTflise/view?usp=sharing 
    
- FTP
    ```
    ftp://ncov_cl:Cyberlink@ftp.gocyberlink.com/
    ftp://ncov_pf:Perfectcorp@ftp.gocyberlink.com/
    ```

- [U messenger](https://u.cyberlink.com/products/umessenger)

- VPN Windows:
  - Windows
    ```
    ftp://ncov_pf:Perfectcorp@ftp.gocyberlink.com/IT/VPN/Windows/PF%20Softether%20VPN%20Client%20install%20guide(Win).pdf
    ```
  - iOS: 
    ```
    ftp://ncov_pf:Perfectcorp@ftp.gocyberlink.com/IT/VPN/Mac%20OS%20X/How%20to%20configure%20VPN%20on%20Mac%20OS%20X%20(PF).pdf
    ```

## Table of Contents  

- [Overview](#overview)
- [Software and Git Repository](#software-and-git-repository)
- [Install VM on Windows](#install-vm-on-windows)
- [Install XCode and Git](#install-xcode-and-git)
- [Import Project](#import-project)



## Overview  

- This document tells you how to set up VMWare, MacOS, XCode step by step and how to import projects on iOS.
- If you can access VPN, you can download VM image from this path. This image already include VM and XCode. Jump to [Import Project](#import-project) directly.
    ```
    \\tommyc-dt3\ShareVM\Catalina_10_15_2_200GB_Dev
    ```
    > MacOS User: rdapp, password: 0000



## Software and Git Repository

- YouCam Perfect iOS
    ```
    ssh://git@git.pft.com/source/ycp-ios.git
    ```

- YouCam Perfect Android
    ```
    ssh://git@git.pft.com/source/ycp.git
    ```

## Install VM on Windows 

1. Install and unlock VMware Workstation
   - Enable Intel-vt.
   - Download and Install VMWare Pro or Player. [Offical Link](https://www.vmware.com/products/workstation-pro/workstation-pro-evaluation.html)
   - Official VMWare locked MacOS feature, Need unlock.
     - download [Unlocker](https://www.mediafire.com/file/ghjbz76885gx5d5/FMojave.rar/file) and unzip.
     - run "VMware Unlocker 3.0.1" → "win-install.cmd" by **Administrator**.
   - 如果遇到Intel-vt 關掉問題，可以[參考文件開啟](https://www.moonlol.com/vmware-workstation-install-mac-os-x-6151.html)
2. Install MacOS
   - 準備MacOS最新版本的VMDK(Virtual Machine Disk的簡稱). Download from [geekrar](https://www.geekrar.com/install-macos-mojave-on-vmware/)
   - Create a new VM and set disk to this VMDK.
   - Change Setting, "Virtual Machine Setting" → "USB controller" → "USB compatibility" to "USB 2.0". for connect iPhone.
   - Run VM and finish first time install flow.
   - Install WMware tools for screen resolution.

     - Click on vmware toolbar, "VM" → "Install VMware Tools.."
     - Click install vmware tools in MacOS.
     - Allow permission from security.
3. 螢幕的解析度如不正常運作
    - VMware 可能沒安裝成功. [傳送門](https://magiclen.org/macos-mojave-vmware/)
      - 如果VMware Tools有安裝並運作成功，在「關於設台 Mac」中應該要可以看到「顯示器 128MB」。注意「128MB」的部份，如果VMware Tools沒有運作成功，這個值會遠低於「128MB」哦！如果您有安裝VMware Tools卻還是無法成功運作的話，那就要再重新裝一次VMware Tools。
      - 會有這個問題是因為在第一次安裝VMware Tools的時候，安裝程式要安裝的功能被macOS擋下來了。所以必須要在跳出「已阻擋系統延伸功能」的訊息，並做了「允許」的動作後，再跑一次安裝程式，才能真正完成VMware Tools的安裝。
    - Autofit 沒打開 [傳送門](http://magicjackting.pixnet.net/blog/post/191234203-用-vmware-安裝及測試-mac-os-x)
      - 修改一下 VMware 的整體設定 (Edit → Preference… → Display):
        - 把 Autofit 的兩個選項都打勾 (Autofil window, Autofil guest)
        - 還有 Full srceen 的選項, 請點選第一個選項 Autofit guest



## Install XCode and Git
1. 請用公司的Email申請Apple ID. 並跟Ted報備, 設定後台.

2. Install "XCode" from App Store.
3. Install "Xcode command line tool" from Terminal
    ```
    xcode-select --install
    ```
4. Install "Homebrew" from Terminal
    ```
    /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    ```
5. Install "git" from Terminal
    ```
    brew install git
    ```
6. Install "git-lfs" from Terminal
    ```
    brew install git-lfs
    git lfs install
    ```



## Import Project

1. Launch XCode, import certificate from "xcode → preference"
   1. 帳號管理已經實名化, 請用公司Email加入.
   2. 加入後應該要看到Team: "PERFECT CORP.", 如果沒有請重開XCode, 再沒有請跟Ted確認後台已加帳號.
   3. Click "Download Manual Profiles".
   4. Click "Manage Certificates…", 要看到有內容才正確.
2. 如果手上的iOS devices沒註冊過，執行相關註冊流程 (找iOS team Jay)
3. Setup ssh on your Mac.
   
   - Keygen 一組ssh keypair，將你的public key上傳到phabricator
4. clone project from git
5. pull git lfs for large file.
    ```
    git lfs pull
    ```
6. happy build without errors!
   
   - System maybe ask keychain password, input "local password" and click "always allow".
